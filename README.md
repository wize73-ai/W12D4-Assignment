# W12D4-Assignment

solving the three binary tree traversal methods.

for this exercise I used a chatgpt copilot to create basic recursive boilerplate for the thee traversal methods
- Inorder
- Preorder
- Postorder

the boilerplate handling of the node discovery is identical in the three approaches in python.

the difference is in the order of writing the results

- Inorder:

            if node:
                _inorder_helper(node.left, result)  # Visit left subtree
                result.append(node.val)             # Visit node itself
                _inorder_helper(node.right, result) # Visit right subtree

- Preorder:

            if node:
                result.append(node.val)             # Visit node itself
                _preorder_helper(node.left, result) # Visit left subtree
                _preorder_helper(node.right, result)# Visit right subtree

- Postorder:

            if node:
                _postorder_helper(node.left, result)  # Visit left subtree
                _postorder_helper(node.right, result) # Visit right subtree
                result.append(node.val)               # Visit node itself


- Python Boilerplate

# Definition for a binary tree node.
class TreeNode(object):
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

class Solution(object):

    def preorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        def _preorder_helper(node, result):
            if node:
                result.append(node.val)             # Visit node itself
                _preorder_helper(node.left, result) # Visit left subtree
                _preorder_helper(node.right, result)# Visit right subtree

        result = []
        _preorder_helper(root, result)
        return result

# Example usage:
# Constructing the binary tree:
#       1
#      / \
#     2   3
#    / \
#   4   5

root = TreeNode(1)
root.left = TreeNode(2)
root.right = TreeNode(3)
root.left.left = TreeNode(4)
root.left.right = TreeNode(5)

# Create an instance of Solution and call preorderTraversal
solution = Solution()
# Preorder traversal: [1, 2, 4, 5, 3]
print(solution.preorderTraversal(root))





I will do the same in JavaScript

class TreeNode {
    constructor(val = 0, left = null, right = null) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}

class Solution {
    inorderTraversal(root) {
        const result = [];
        function _inorderHelper(node) {
            if (node) {
                _inorderHelper(node.left);   // Visit left subtree
                result.push(node.val);       // Visit node itself
                _inorderHelper(node.right);  // Visit right subtree
            }
        }
        _inorderHelper(root);
        return result;
    }
}

// Example usage:
const root = new TreeNode(1);
root.left = new TreeNode(2);
root.right = new TreeNode(3);
root.left.left = new TreeNode(4);
root.left.right = new TreeNode(5);

const solution = new Solution();
console.log(solution.inorderTraversal(root)); // [4, 2, 5, 1, 3]


class TreeNode {
    constructor(val = 0, left = null, right = null) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}

class Solution {
    preorderTraversal(root) {
        const result = [];
        function _preorderHelper(node) {
            if (node) {
                result.push(node.val);       // Visit node itself
                _preorderHelper(node.left);  // Visit left subtree
                _preorderHelper(node.right); // Visit right subtree
            }
        }
        _preorderHelper(root);
        return result;
    }
}

// Example usage:
const root = new TreeNode(1);
root.left = new TreeNode(2);
root.right = new TreeNode(3);
root.left.left = new TreeNode(4);
root.left.right = new TreeNode(5);

const solution = new Solution();
console.log(solution.preorderTraversal(root)); // [1, 2, 4, 5, 3]


class TreeNode {
    constructor(val = 0, left = null, right = null) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}

class Solution {
    postorderTraversal(root) {
        const result = [];
        function _postorderHelper(node) {
            if (node) {
                _postorderHelper(node.left);  // Visit left subtree
                _postorderHelper(node.right); // Visit right subtree
                result.push(node.val);        // Visit node itself
            }
        }
        _postorderHelper(root);
        return result;
    }
}

// Example usage:
const root = new TreeNode(1);
root.left = new TreeNode(2);
root.right = new TreeNode(3);
root.left.left = new TreeNode(4);
root.left.right = new TreeNode(5);

const solution = new Solution();
console.log(solution.postorderTraversal(root)); // [4, 5, 2, 3, 1]


Conclusion,

For this exercise I treated it as an opprtunity to learn the binary traversal methods rather than the memorization of the code. I used ChatGPT to create boilerplate to use and apply.

Leetcode challenge was to do it iteratively in stead of recursive.

follow up:


class TreeNode(object):
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

class Solution(object):

    def inorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        result, stack = [], []
        current = root

        while current or stack:
            while current:
                stack.append(current)
                current = current.left
            current = stack.pop()
            result.append(current.val)
            current = current.right
        
        return result

# Example usage:
root = TreeNode(1)
root.left = TreeNode(2)
root.right = TreeNode(3)
root.left.left = TreeNode(4)
root.left.right = TreeNode(5)

solution = Solution()
print(solution.inorderTraversal(root)) # [4, 2, 5, 1, 3]


class TreeNode(object):
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

class Solution(object):

    def preorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        if not root:
            return []

        result, stack = [], [root]

        while stack:
            current = stack.pop()
            result.append(current.val)
            if current.right:
                stack.append(current.right)
            if current.left:
                stack.append(current.left)

        return result

# Example usage:
root = TreeNode(1)
root.left = TreeNode(2)
root.right = TreeNode(3)
root.left.left = TreeNode(4)
root.left.right = TreeNode(5)

solution = Solution()
print(solution.preorderTraversal(root)) # [1, 2, 4, 5, 3]

class TreeNode(object):
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

class Solution(object):

    def postorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        if not root:
            return []

        result, stack = [], [root]
        visited = set()

        while stack:
            current = stack[-1]
            if (current.left and current.left not in visited) or (current.right and current.right not in visited):
                if current.right and current.right not in visited:
                    stack.append(current.right)
                if current.left and current.left not in visited:
                    stack.append(current.left)
            else:
                visited.add(current)
                result.append(current.val)
                stack.pop()
        
        return result

# Example usage:
root = TreeNode(1)
root.left = TreeNode(2)
root.right = TreeNode(3)
root.left.left = TreeNode(4)
root.left.right = TreeNode(5)

solution = Solution()
print(solution.postorderTraversal(root)) # [4, 5, 2, 3, 1]



For All Approaches:

the time complexity is O(n) and the space complexity varies from O(n) to O(log n) depending on the size and shape of the tree. If it is unbalanced and not deep it approaches linear space, and if there are many deep branches it will approach log n Space. Multiple deep branches create a much higher stack (h) than shallow branches hence the log n space.
