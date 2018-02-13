# Leetcode: Verify Preorder Sequence in Binary Search Tree     :BLOG:Medium:


---

Verify Preorder Sequence in Binary Search Tree  

---

Similar Problems:  
-   Tag: [#binarytree](https://brain.dennyzhang.com/tag/binarytree)

---

Given an array of numbers, verify whether it is the correct preorder traversal sequence of a binary search tree.  

You may assume each number in the sequence is unique.  

Follow up:  
Could you do it using only constant space complexity?  

Github: [challenges-leetcode-interesting](https://github.com/DennyZhang/challenges-leetcode-interesting/tree/master/verify-preorder-sequence-in-binary-search-tree)  

Credits To: [leetcode.com](https://leetcode.com/problems/verify-preorder-sequence-in-binary-search-tree/description/)  

Leave me comments, if you have better ways to solve.  

    ## Blog link: https://brain.dennyzhang.com/verify-preorder-sequence-in-binary-search-tree
    
    class Solution(object):
        def verifyPreorder(self, preorder):
            """
            :type preorder: List[int]
            :rtype: bool
            """
            import sys
            return self.myVerifyPreorder(preorder, -sys.maxsize-1)
    
        def myVerifyPreorder(self, preorder, min_val):
            length = len(preorder)
            if length == 0: return True
    
            index = sys.maxsize
            for i in range(length):
                if preorder[i] < min_val: return False
                if i != 0 and preorder[i] > preorder[0]:
                    index = i
                    break
    
            # left sub-tree
            if self.myVerifyPreorder(preorder[1:index-1], min_val) is False:
                return False
    
            # if index == sys.maxsize, right sub-tree is empty
            # right sub-tree
            if self.myVerifyPreorder(preorder[index:], preorder[0]) is False:
                return False
    
            return True