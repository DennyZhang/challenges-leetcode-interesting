# Leetcode: Valid Square     :BLOG:Amusing:


---

Given the coordinates of four points in 2D space, return whether the four points could construct a square.  

---

Given the coordinates of four points in 2D space, return whether the four points could construct a square.  

The coordinate (x,y) of a point is represented by an integer array with two integers.  

    Example:
    Input: p1 = [0,0], p2 = [1,1], p3 = [1,0], p4 = [0,1]
    Output: True

Note:  

1.  All the input integers are in the range [-10000, 10000].
2.  A valid square has four equal sides with positive length and four equal angles (90-degree angles).
3.  Input points have no order.

Github: [challenges-leetcode-interesting](https://github.com/DennyZhang/challenges-leetcode-interesting/tree/master/valid-square)  

Credits To: [Leetcode.com](https://leetcode.com/problems/valid-square/description/)  

Leave me comments, if you know how to solve.  

    ## Basic Ideas:
    ##              p2(0,1)               p4(1,1)
    ##
    ##
    ##              p1(0,0)               p3(1,0)
    ##
    ## Complexity: Time O(1), Space O(1)
    class Solution(object):
        def validSquare(self, p1, p2, p3, p4):
            """
            :type p1: List[int]
            :type p2: List[int]
            :type p3: List[int]
            :type p4: List[int]
            :rtype: bool
            """
            l = sorted([p1, p2, p3, p4])
            print l
            if l[0][0] >= l[3][0] or l[0][1] >= l[3][1]:
                return False
            return l[1] == [l[0][0], l[3][1]] and l[2] == [l[3][0], l[0][1]]
    
    s = Solution()
    print s.validSquare([1,0], [-1,0], [0,1], [0,-1]) # true