***03/17/2019***

Red-Black Tree is a self-balancing Binary Search Tree (BST) where every node follows following rules.

  1. Every node has a color either red or black.
  2. Root of tree is always black.
  3. There are no two adjacent red nodes (A red node cannot have a red parent or red child).
  4. Every path from a node (including root) to any of its descendant NULL node has the same number of black nodes.
  
<div>
  <p style = "align : center"><img src="https://www.geeksforgeeks.org/wp-content/uploads/RedBlackTree.png></p>
</div>
  
Most of the BST operations (e.g., search, max, min, insert, delete.. etc) take O(h) time where h is the height of the BST. The cost of these operations may become O(n) for a skewed Binary tree. If we make sure that height of the tree remains O(Logn) after every insertion and deletion, then we can guarantee an upper bound of O(Logn) for all these operations. The height of a Red-Black tree is always O(Logn) where n is the number of nodes in the tree.
