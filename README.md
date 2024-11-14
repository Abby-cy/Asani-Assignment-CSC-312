# Asani-Assignment-CSC-312
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None

class BinaryTree:
    def __init__(self):
        self.root = None

    def insert(self, data):
        if self.root is None:
            self.root = Node(data)
        else:
            self._insert(data, self.root)

    def _insert(self, data, current):
        if data < current.data:
            if current.left is None:
                current.left = Node(data)
            else:
                self._insert(data, current.left)
        else:
            if current.right is None:
                current.right = Node(data)
            else:
                self._insert(data, current.right)

    def search(self, data):
        return self._search(data, self.root)

    def _search(self, data, current):
        if current is None:
            return None
        elif current.data == data:
            return current
        elif data < current.data:
            return self._search(data, current.left)
        else:
            return self._search(data, current.right)

    def preorder_traversal(self, node):
        if node:
            print(node.data, end=' ')
            self.preorder_traversal(node.left)
            self.preorder_traversal(node.right)

    def inorder_traversal(self, node):
        if node:
            self.inorder_traversal(node.left)
            print(node.data, end=' ')
            self.inorder_traversal(node.right)

    def postorder_traversal(self, node):
        if node:
            self.postorder_traversal(node.left)
            self.postorder_traversal(node.right)
            print(node.data, end=' ')

# Example usage
bt = BinaryTree()
nodes = [27, 14, 35, 10, 19, 31, 42]
for node in nodes:
    bt.insert(node)

# Searching for a node
found_node = bt.search(31)
print(f"[{found_node.data}] Element found." if found_node else "[ x ] Element not found (31).")

# Traversals
print("\nPreorder traversal:", end=" ")
bt.preorder_traversal(bt.root)
print("\nInorder traversal:", end=" ")
bt.inorder_traversal(bt.root)
print("\nPostorder traversal:", end=" ")
bt.postorder_traversal(bt.root)
