---
tags:
  - classnotes
  - dsa
Chapter: 4
Course: Data Structures and Algorithms 2
---


# AVL Trees
- AVL Trees are a special case of the [[Binary Search Tree]]
- **self balancing** BST
- Time complexity: 
	- Balanced BST (AVL): O(log(n))
	- Unbalanced BST: O(n)
	- For search, insert, and delete operations
- designed to maintain a balance between the left and right subtrees, ensuring that the tree remains approximately balanced even after insertions or deletions of nodes
- binary tree with balance condition
	- to ensure the depth is O(log(n))
		- search complexity bound to O(log(n))
- Balance condition
	- for **every node** in tree, height of left and right subtree can **differ by at most 1**
	- both left and right subtrees are themselves AVL trees
- How to maintain the balance?
	- Rotate nodes if condition violated when inserting nodes
	- Assume lazy deletion
		- just put a tag stating that it has been deleted
- Widely used in the following applications for searching ,inserting and deleting
	- Dictionary table or symbol table
	- Database indexing
	- compiler implementations
	- text editors
	- Network Routing
	- Priority Queues
	- File Systems
AKA height-balanced tree
- Balance factor = (height(rightSubtree) - height(leftSubtree))
## Specification
```c++
class AVLTree {
	public:
		void find(x);
		void makeEmpty();
		void insert(x);
		void remove(x);
		Node* findMin();
		void removeMin(Node* t);
	private:
		Node* root;
}
```

### Insertion tree
- Attach a new node as a leaf as if it is a BST
- only nodes that are on the path from insertion to root can have imbalances
- The deepest node in the tree with a balance factor greater than +/- 1 will be the pivot
### Imbalance conditions
The imbalance could have occurred as a result of:
1. An insertion in the left subtree of the left child of the pivot node (outside insertion/right rotation)
2. An insertion in the right subtree of the left child of the pivot node (inside insertion)
3. An insertion in the left subtree of the right child of the pivot node (inside insertion)
4. An insertion in the right subtree of the right child of the pivot node (outside insertion/left rotation)
### **Single rotation** 
- needed for *outside insertions*, cases 1 and 4

![[rotation.excalidraw]]
```c++
void rotateWithLeftChild(AvlNode* &k2) {
	AvlNode *k1 = k2->left;
	k2->left = k1->left;
	k1->right = k2;
	k2->height = max(height(k2->left), height(k2->right)) + 1;
	k1->height = max(height(k1->left), height(k1->right)) + 1;
	k2 = k1;
}
```

### Double Rotation
![[Double Rotation.excalidraw]]
```c++
void doubleRotateWithLeftChild(AvlNode* & k3) {
	rotateWithRightChild(k3->left);
	rotateWithLefChild(k3);
}
```
## Implementation
```c++
struct AvlNode {
	Comparable element;
	AvlNode *left;
	AvlNode *right;
	int height;
	AvlNode (const Comparable & ele, AvlNode* lt, AvlNode& rt, int h - 0) : element{ele}, left{lt}, right{rt}, height{h}{}
	
	AvlNode (Comparable & ele, AvlNode* lt, AvlNode& rt, int h - 0) : element{ele}, left{lt}, right{rt}, height{h}{}
};

int height(AvlNode *t) const {
	return t == nullptr ? t-> height;
}

void insert(const Comparable& x, AvlNode*& t)
	if (t == nullptr) {
		t = new AvlNode{x, nullptr, nullptr};
	else if (x < t->element)
		insert(x, t->left)
	else if (x > t->element)
		insert(x, t->right);
	balance(t);
} 
```
## Summary
### Binary Trees
- may have a path length of O(n)
- fairly likely to have a path length of O(log<sub>2</sub>(n))
### AVL trees
- insertion and deletion fro binary trees is such that the height is guaranteed to be O(log<sub>2</sub>(n))
- guarantees that the tree is close to full
- changes are limited to the simple path from root to leaf node O(logn)
### Cost
- more complex insertion/deletion implementation
- must store the balance factor for each node

## Problems with Big 0 Notation
- assumes all operations take equal time
- suppose all data does not fit in memory
- some part of data may be stored on hard disk
- CPU speed in millions of instructions per second
- Typical disk speeds about 7,200 RPM
- so accessing disk in incredibly expensive
- So we may be willing to do more computation to organize our data better and make fewer disk accesses
	- how can we achieve this?
	- Multi-level index
## Problems with binary trees
- There is no guarantee that binary trees will be balanced
	- there are potentially O(n) disk operations
## M-ary trees
- allows up to M children for each node
- A complete M-ary tree of N nodes has a depth of log<sub>M</sub>N
### M-ary Search tree
- Each node has (M-1) keys to decide which of the M branches to follow.
- Larger M -> smaller tree depth
# B-Trees
- an M-ary search tree with he following balance restrictions
1. Every node has at most *m* children.  
	1. *m* is the order
2. Every internal node has at least ⌈m/2⌉ children.  
3. The root is either a leaf, or has at least 2 children.  
4. All leaves appear on the same level.  
5. A non-leaf node with k children contains k−1 keys.

## Insertion
### Search for the correct position  
- Start at the root node.  
- Find the leaf node where the key should be inserted.  
### Insertion in a leaf node  
- Insert the key into the leaf node while maintaining the sorted order within the node  
### Check for overflow  
- If the leaf node is not full, insert the key into the node.
- If the leaf node is full, split the node into two nodes. 
### Splitting nodes:  
- Promote the median key from the overfull node to the parent node.  
- Adjust the parent node to include the new child pointers and keys.  
### Recursion:  
- If the parent node is full, split the parent node until the root node is reached
### Root node split:
- If the root node splits, create a new root node with the two children resulting from the split and promote the median key to the new root

# B+ trees
b tree with links between leaf nodes
the leaves are the nodes with the pointer to the data on disk



