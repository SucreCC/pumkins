---
title: Tree
sticky: false
date: 2024-1-15 07:54:00
layout: categories
categories:
- [Interview]
tags:
- Sucre
- Algorithms and Data Structure
---


<!-- more -->

A note for tree.


# Some concepts about tree

## Inorder Traversal, Preorder Traversal and Postorder Traversal
To know which is inorder travers, Preorder Traversal and Postorder Traversal, we need find out the search order of the current root node.

![img.png](/assets/blog/img3.png)

1. Inorder Traversal
> The order of search root node is in middle, in printInorder method. 

```` Java

// Java program for different tree traversals

// Class containing left and right child of current
// node and key value
class Node {
	int key;
	Node left, right;

	public Node(int item)
	{
		key = item;
		left = right = null;
	}
}

class BinaryTree {

	// Root of Binary Tree
	Node root;

	BinaryTree() { root = null; }

	// Given a binary tree, print its nodes in inorder
	void printInorder(Node node)
	{
		if (node == null)
			return;

		// First recur on left child
		printInorder(node.left);

		// Then print the data of node
		System.out.print(node.key + " ");

		// Now recur on right child
		printInorder(node.right);
	}

	// Driver code
	public static void main(String[] args)
	{
		BinaryTree tree = new BinaryTree();
		tree.root = new Node(1);
		tree.root.left = new Node(2);
		tree.root.right = new Node(3);
		tree.root.left.left = new Node(4);
		tree.root.left.right = new Node(5);

		// Function call
		System.out.println(
			"Inorder traversal of binary tree is ");
		tree.printInorder(tree.root);
	}
}

````


2. Preorder Traversal
> The order of search root node is in first, in printPreorder method. 
```Java
// Java program for different tree traversals

// Class containing left and right child of current
// node and key value
class Node {
	int key;
	Node left, right;

	public Node(int item)
	{
		key = item;
		left = right = null;
	}
}

class BinaryTree {

	// Root of Binary Tree
	Node root;

	BinaryTree() { root = null; }

	// Given a binary tree, print its nodes in preorder
	void printPreorder(Node node)
	{
		if (node == null)
			return;

		// First print data of node
		System.out.print(node.key + " ");

		// Then recur on left subtree
		printPreorder(node.left);

		// Now recur on right subtree
		printPreorder(node.right);
	}

	// Driver code
	public static void main(String[] args)
	{
		BinaryTree tree = new BinaryTree();
		tree.root = new Node(1);
		tree.root.left = new Node(2);
		tree.root.right = new Node(3);
		tree.root.left.left = new Node(4);
		tree.root.left.right = new Node(5);

		// Function call
		System.out.println(
			"Preorder traversal of binary tree is ");
		tree.printPreorder(tree.root);
	}
}

```



3. Postorder Traversal
> The order of search root node is in last, in printPostorder method.
```Java

// Java program for different tree traversals

// Class containing left and right child of current
// node and key value
class Node {
	int key;
	Node left, right;

	public Node(int item)
	{
		key = item;
		left = right = null;
	}
}

class BinaryTree {

	// Root of Binary Tree
	Node root;

	BinaryTree() { root = null; }

	// Given a binary tree, print its nodes according to the
	// "bottom-up" postorder traversal.
	void printPostorder(Node node)
	{
		if (node == null)
			return;

		// First recur on left subtree
		printPostorder(node.left);

		// Then recur on right subtree
		printPostorder(node.right);

		// Now deal with the node
		System.out.print(node.key + " ");
	}

	// Driver code
	public static void main(String[] args)
	{
		BinaryTree tree = new BinaryTree();
		tree.root = new Node(1);
		tree.root.left = new Node(2);
		tree.root.right = new Node(3);
		tree.root.left.left = new Node(4);
		tree.root.left.right = new Node(5);

		// Function call
		System.out.println(
			"Postorder traversal of binary tree is ");
		tree.printPostorder(tree.root);
	}
}

```
