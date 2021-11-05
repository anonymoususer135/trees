# trees

**Binary Search trees** are only guaranteed if the tree is balanced (near log_2N height)

## AVL Trees

This is a binary search tree which rebalances itself when heights of two subtrees of any node differ by at most 1.

-It operate in O(log_2(N) time in the average and worst case of lookup, insertion, node removal.

-**Balance factor** is associated with tree node which is difference in height between its two subtrees.

-After the usual insertion/removal is performed, it's followed with tree rotations to regain balance. And then it's no longer AVL tree.

-**Tree Rotations** are switching the positions of a child node and its parent
  -Direction to rotate depends on structure of the tree and location of inserted or deleted node
  -Every imbalance can be solved with only one or two rotations

### Four rotation cases

-The rotation cases are based on the location of the inserted or deleted node
-Rotations are only used if the tree becomes unbalanced

1. If node insert into let subtree of node T's left child, right rotation is applied
2. If it's inserted into right subtree's right child, left rotation
3. Insert into left subtree of T right child, right-left rotation.
4. Insert into right subtree of T left child, left-right rotation.

**Balanced node** has balance factor at most 1. **Unbalanced ones** have balanced factor greater than 1

Example:

**Right Rotation**
1. A node named 6 is created. Right now it is balanced.
2. A left child named 4 is created for 6. It is still balanced.
3. Another left child named 2 is created for 4, and it loses balance.
4. The 6 node is rotated to the right, making a right child for 4.
5. It is balanced. 4 has a left child called 2 and a right child called 6.

**Left Rotation**
1. A node named 2 is created. It's balanced.
2. A right child named 4 is created. Still balanced.
3. A right child for 4 named 6 is created. It's now unbalanced.
4. The 2 is rotated to the left.
5. It's balanced again. 4 has a left child named 2 and a right child named 6.

**Single Rotations**
-Single left or right rotation reduces the height of the tree by 1
-Right rotation is used if the height of the left subtree is greater than right one
-Left rotation is used if the height of the right subtree is greater than left one

**Double Rotation**
-Used when a single rotation isn't enough.
-First rotation in the double sets up the tree for second rotation

**AVL Tree Logical Level**
-AVL tree and binary search tree share same operations
-They add additional conditions to PutItem and DeleteItem. The tree will be balanced before and after these operations are performed

**AVL Tree Application Level**
-Binary Search tree are great for random, unchanging data. The tree can be balanced once and left alone
-AVL trees are better when insertion and deletion operations perform over the lifetie of the tree

**AVL Implementation Level**
-AVL tree implementation has a few more helper functions.
  -Four rotation unctions
  -Difference, for finding difference in height between two subtrees
  -Balance, for deciding which rotation is needed
-PutItem and DeleteItem call Balance after performing insertion/deletion

**Rotation functions**
-Rotatons are straightforward
-Each one takes unbalanced node as parameter and returns updated root node
-Compare code to rotations diagrams

## Code for rotating right

```cpp
TreeNode* RotateRight(TreeNode* T) {
  TreeNode* S = T->left;
  TreeNode* B = S->right;
  S->right = T;
  T->left = B;
  return S;
}
```

I'm not done...
