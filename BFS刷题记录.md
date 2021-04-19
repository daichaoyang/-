**二叉树的层级遍历**
题解：
建立一个二叉树高的二位数组，递归遍历的时候根据遍历的层级在相应的二位数组内加上二叉树元素即可
~~~
class Solution(object):
    #递归遍历二叉树
    def travel_node(self, root, list_node, level):
        if root != None:
            list_node[level].append(root.val)
            self.travel_node(root.left, list_node, level + 1)
            self.travel_node(root.right, list_node, level + 1)

    def levelOrder(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """

        #获取二叉树的高度
        def get_treenode_high(root, high): 
            if root == None:
                return high
            left_high = get_treenode_high(root.left, high + 1)
            right_high = get_treenode_high(root.right, high + 1)
            return max(left_high, right_high)
        if root == None:
            return []
        high = get_treenode_high(root, 0)
        list_node = []
        for i in range(0, high):
            tmp = []
            list_node.append(tmp)
        self.travel_node(root, list_node, 0)
        return list_node
~~~

