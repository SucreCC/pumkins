---
title: CICD pipeline
sticky: true
date: 2024-6-29 10:16:00
layout: categories
categories:
- [Blog]
tags:
- Sucre
- CICD
- Java
---

Building a CI/CD pipeline using Jenkins and Grafana Loki help automate the build, test, deployment, and logging processes.


<!-- more -->

### Basic Environment Setup

#### 1. Install Jenkins
1. **Download and install Jenkins**:
   ```sh
   
   wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
   sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
   sudo apt update
   sudo apt install jenkins
   ```
2. **Start Jenkins and access it**: Visit `http://erver_ip:8080`
3. **Complete the initial setup and install recommended plugins**.

#### 2. Install Grafana and Loki
1. **Install Grafana**:
   ```sh
   
   sudo apt-get install -y software-properties-common
   sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
   sudo apt-get update
   sudo apt-get install grafana
   sudo systemctl start grafana-server
   sudo systemctl enable grafana-server
   ```

2. **Install Loki**:
   ```sh
   
   wget https://github.com/grafana/loki/releases/download/v2.2.1/loki-linux-amd64.zip
   unzip loki-linux-amd64.zip
   chmod +x loki-linux-amd64
   sudo mv loki-linux-amd64 /usr/local/bin/loki
   ```

3. **Install Promtail**:
   ```sh
   
   wget https://github.com/grafana/loki/releases/download/v2.2.1/promtail-linux-amd64.zip
   unzip promtail-linux-amd64.zip
   chmod +x promtail-linux-amd64
   sudo mv promtail-linux-amd64 /usr/local/bin/promtail
   ```

### 2. Configuring Loki and Promtail

#### 1. Configure Loki
**Create the Loki configuration file** `loki-config.yaml`:
```yaml

auth_enabled: false

server:
  http_listen_port: 3100

ingester:
  lifecycler:
    address: 127.0.0.1
    ring:
      kvstore:
        store: inmemory
      replication_factor: 1
    final_sleep: 0s
  chunk_idle_period: 5m
  chunk_retain_period: 30s
  max_transfer_retries: 0
schema_config:
  configs:
    - from: 2020-10-24
      store: boltdb
      object_store: filesystem
      schema: v11
      index:
        prefix: index_
        period: 168h
storage_config:
  boltdb:
    directory: /tmp/loki/index
  filesystem:
    directory: /tmp/loki/chunks
limits_config:
  enforce_metric_name: false
  reject_old_samples: true
  reject_old_samples_max_age: 168h
chunk_store_config:
  max_look_back_period: 0s
table_manager:
  retention_deletes_enabled: false
  retention_period: 0s
```

**Start Loki**:
```sh

loki -config.file=loki-config.yaml
```

#### Configure Promtail
**Create the Promtail configuration file** `promtail-config.yaml`:
```yaml

server:
  http_listen_port: 9080
  grpc_listen_port: 0

positions:
  filename: /tmp/positions.yaml

clients:
  - url: http://localhost:3100/loki/api/v1/push

scrape_configs:
  - job_name: system
    static_configs:
    - targets:
        - localhost
      labels:
        job: varlogs
        __path__: /var/log/*.log
```

**Start Promtail**:
```sh

promtail -config.file=promtail-config.yaml
```

### Jenkins Integration

#### 1. Install Necessary Plugins
- In the Jenkins dashboard, go to `Manage Jenkins` -> `Manage Plugins` -> `Available`, and install the following plugins:
    - `Git Plugin`
    - `Pipeline`
    - `Grafana Plugin`

#### 2. Create a Jenkins Pipeline

1. **Create a new Pipeline project**.
2. **Write the Pipeline Script (`Jenkinsfile`)**:

```groovy

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your-repo.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
            }
        }
    }

    post {
        always {
            script {
                def log = currentBuild.rawBuild.getLog(1000).join("\n")
                writeFile file: 'build.log', text: log
            }
            archiveArtifacts artifacts: 'build.log'
            grafanaSave logData: readFile('build.log'), dataSource: 'loki'
        }
    }
}
```

### Grafana Integration

#### 1. Configure Grafana
1. **Login to Grafana**: Default URL is `http://your_server_ip:3000`.
2. **Add Loki Data Source**:
    - Go to `Configuration` -> `Data Sources` -> `Add data source`, and select Loki.
    - Set the Loki URL to `http://localhost:3100`.

#### 2. Create a Dashboard
1. **Go to** `Create` -> `Dashboard` -> `Add new panel`.
2. **Configure the query to fetch logs from Loki**, for example:
   ```plaintext
   
   {job="jenkins"}
   ```
