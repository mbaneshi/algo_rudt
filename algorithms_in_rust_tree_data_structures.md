### Timestamp: 2024-10-28 14:25:00 UTC

### Summary: This section explores tree data structures, focusing on binary trees, binary search trees, tree traversal methods, heaps, and priority queues, along with their implementations in Rust.

---

### 8. Tree Data Structures

#### Binary Trees
1. **Properties of Binary Trees**:
   - A binary tree is a tree data structure in which each node has at most two children, referred to as the left child and the right child.
   - The maximum number of nodes at level \(l\) is \(2^l\), and the maximum number of nodes in a binary tree of height \(h\) is \(2^{h+1} - 1\).

2. **Applications**:
   - Used in various applications like expression parsing, binary heaps, and decision trees.

#### Binary Search Trees (BST)
1. **Definition**:
   - A binary search tree is a binary tree with the property that for each node, all elements in the left subtree are less than the node, and all elements in the right subtree are greater.

2. **Operations**:
   - **Insertion**:
   ```rust
   struct TreeNode {
       value: i32,
       left: Option<Box<TreeNode>>,
       right: Option<Box<TreeNode>>,
   }

   impl TreeNode {
       fn new(value: i32) -> Self {
           TreeNode {
               value,
               left: None,
               right: None,
           }
       }

       fn insert(&mut self, value: i32) {
           if value < self.value {
               if let Some(left) = &mut self.left {
                   left.insert(value);
               } else {
                   self.left = Some(Box::new(TreeNode::new(value)));
               }
           } else {
               if let Some(right) = &mut self.right {
                   right.insert(value);
               } else {
                   self.right = Some(Box::new(TreeNode::new(value)));
               }
           }
       }
   }
   ```

   - **Searching**:
   ```rust
   fn search(node: &Option<Box<TreeNode>>, target: i32) -> bool {
       if let Some(n) = node {
           if target == n.value {
               return true;
           } else if target < n.value {
               return search(&n.left, target);
           } else {
               return search(&n.right, target);
           }
       }
       false
   }
   ```

   - **Deletion**:
   ```rust
   fn delete(node: Option<Box<TreeNode>>, target: i32) -> Option<Box<TreeNode>> {
       if let Some(mut n) = node {
           if target < n.value {
               n.left = delete(n.left, target);
           } else if target > n.value {
               n.right = delete(n.right, target);
           } else {
               // Node to delete found
               if n.left.is_none() {
                   return n.right;
               } else if n.right.is_none() {
                   return n.left;
               }

               // Node with two children
               let min_larger_node = find_min(n.right.as_ref().unwrap());
               n.value = min_larger_node.value;
               n.right = delete(n.right, min_larger_node.value);
           }
           Some(n)
       } else {
           None
       }
   }

   fn find_min(node: &Box<TreeNode>) -> &TreeNode {
       if let Some(left) = &node.left {
           find_min(left)
       } else {
           node
       }
   }
   ```

#### Tree Traversals
1. **In-Order Traversal**:
   - Visits nodes in the order: left child, current node, right child.
   ```rust
   fn in_order(node: &Option<Box<TreeNode>>) {
       if let Some(n) = node {
           in_order(&n.left);
           println!("{}", n.value);
           in_order(&n.right);
       }
   }
   ```

2. **Pre-Order Traversal**:
   - Visits nodes in the order: current node, left child, right child.
   ```rust
   fn pre_order(node: &Option<Box<TreeNode>>) {
       if let Some(n) = node {
           println!("{}", n.value);
           pre_order(&n.left);
           pre_order(&n.right);
       }
   }
   ```

3. **Post-Order Traversal**:
   - Visits nodes in the order: left child, right child, current node.
   ```rust
   fn post_order(node: &Option<Box<TreeNode>>) {
       if let Some(n) = node {
           post_order(&n.left);
           post_order(&n.right);
           println!("{}", n.value);
       }
   }
   ```

#### Heaps and Priority Queues
1. **Heap Properties**:
   - A heap is a special tree-based data structure that satisfies the heap property: for a max heap, each parent node is greater than or equal to its children, and for a min heap, each parent node is less than or equal to its children.

2. **Applications**:
   - Used in implementing priority queues, scheduling algorithms, and heapsort.

3. **Implementing a Min Heap**:
   ```rust
   struct MinHeap {
       elements: Vec<i32>,
   }

   impl MinHeap {
       fn new() -> Self {
           MinHeap { elements: vec![] }
       }

       fn insert(&mut self, value: i32) {
           self.elements.push(value);
           self.bubble_up();
       }

       fn bubble_up(&mut self) {
           let mut index = self.elements.len() - 1;
           while index > 0 {
               let parent_index = (index - 1) / 2;
               if self.elements[index] < self.elements[parent_index] {
                   self.elements.swap(index, parent_index);
                   index = parent_index;
               } else {
                   break;
               }
           }
       }

       fn extract_min(&mut self) -> Option<i32> {
           if self.elements.is_empty() {
               return None;
           }
           let min = self.elements[0];
           let last = self.elements.pop().unwrap();
           if !self.elements.is_empty() {
               self.elements[0] = last;
               self.bubble_down();
           }
           Some(min)
       }

       fn bubble_down(&mut self) {
           let mut index = 0;
           let length = self.elements.len();
           loop {
               let left_child = 2 * index + 1;
               let right_child = 2 * index + 2;
               let mut smallest = index;

               if left_child < length && self.elements[left_child] < self.elements[smallest] {
                   smallest = left_child;
               }
               if right_child < length && self.elements[right_child] < self.elements[smallest] {
                   smallest = right_child;
               }

               if smallest == index {
                   break;
               }

               self.elements.swap(index, smallest);
               index = smallest;
           }
       }
   }
   ```

---

### Closing Thoughts
This section covers essential tree data structures and their operations, emphasizing their significance in algorithm design. Understanding trees, including binary search trees and heaps, is vital for effective data organization and retrieval in complex applications.

---

### Lines and Characters
- **Lines**: 83
- **Characters**: 6,390

### Filename for Archiving
```bash
nvim algorithms_in_rust_tree_data_structures.md
```
