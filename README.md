# python
Python is an easy to learn, powerful programming language. It has efficient high-level data structures and a simple but effective approach to object-oriented programming. Python’s elegant syntax and dynamic typing, together with its interpreted nature, make it an ideal language for scripting and rapid application development in many areas on most platforms.

The Python interpreter and the extensive standard library are freely available in source or binary form for all major platforms from the Python Web site, https://www.python.org/, and may be freely distributed. The same site also contains distributions of and pointers to many free third party Python modules, programs and tools, and additional documentation.

The Python interpreter is easily extended with new functions and data types implemented in C or C++ (or other languages callable from C). Python is also suitable as an extension language for customizable applications.

This tutorial introduces the reader informally to the basic concepts and features of the Python language and system. It helps to have a Python interpreter handy for hands-on experience, but all examples are self-contained, so the tutorial can be read off-line as well.

For a description of standard objects and modules, see The Python Standard Library. The Python Language Reference gives a more formal definition of the language. To write extensions in C or C++, read Extending and Embedding the Python Interpreter and Python/C API Reference Manual. There are also several books covering Python in depth.

This tutorial does not attempt to be comprehensive and cover every single feature, or even every commonly used feature. Instead, it introduces many of Python’s most noteworthy features, and will give you a good idea of the language’s flavor and style. After reading it, you will be able to read and write Python modules and programs, and you will be ready to learn more about the various Python library modules described in The Python Standard Library.
# Python program to check binary tree is a subtree of 
# another tree 

# A binary tree node 
class Node: 

	# Constructor to create a new node 
	def __init__(self, data): 
		self.data = data 
		self.left = None
		self.right = None

# A utility function to check whether trees with roots 
# as root 1 and root2 are indetical or not 
def areIdentical(root1, root2): 
	
	# Base Case 
	if root1 is None and root2 is None: 
		return True
	if root1 is None or root2 is None: 
		return False

	# Check fi the data of both roots is same and data of 
	# left and right subtrees are also same 
	return (root1.data == root2.data and
			areIdentical(root1.left , root2.left)and
			areIdentical(root1.right, root2.right) 
			) 

# This function returns True if S is a subtree of T, 
# otherwise False 
def isSubtree(T, S): 
	
	# Base Case 
	if S is None: 
		return True

	if T is None: 
		return False

	# Check the tree with root as current node 
	if (areIdentical(T, S)): 
		return True

	# IF the tree with root as current node doesn't match 
	# then try left and right subtreee one by one 
	return isSubtree(T.left, S) or isSubtree(T.right, S) 


# Driver program to test above function 

""" TREE 1 
	Construct the following tree 
			26 
			/ \ 
		10	 3 
		/ \	 \ 
	4	 6	 3 
	\ 
		30 
	"""

T = Node(26) 
T.right = Node(3) 
T.right.right = Node(3) 
T.left = Node(10) 
T.left.left = Node(4) 
T.left.left.right = Node(30) 
T.left.right = Node(6) 

""" TREE 2 
	Construct the following tree 
		10 
		/ \ 
	4	 6 
	\ 
		30 
	"""
S = Node(10) 
S.right = Node(6) 
S.left = Node(4) 
S.left.right = Node(30) 

if isSubtree(T, S): 
	print "Tree 2 is subtree of Tree 1"
else : 
	print "Tree 2 is not a subtree of Tree 1"

# This code is contributed by Nikhil Kumar Singh(nickzuck_007) 
