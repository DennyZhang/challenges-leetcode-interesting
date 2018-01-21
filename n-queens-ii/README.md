# Leetcode: N-Queens II     :BLOG:Basic:


---

N-Queens II  

---

Follow up for N-Queens problem.  

Now, instead outputting board configurations, return the total number of distinct solutions.  

Github: [challenges-leetcode-interesting](https://github.com/DennyZhang/challenges-leetcode-interesting/tree/master/n-queens-ii)  

Credits To: [leetcode.com](https://leetcode.com/problems/n-queens-ii/description/)  

Leave me comments, if you know how to solve.  

    ## Blog link: http://brain.dennyzhang.com/n-queens-ii
    ## Basic Ideas: backtracking
    ##              Place queen row by row
    ##              For the position we have tried, examine conflict for rows and triangles
    ## Complexity: Time ? Space ?
    class Solution(object):
        def totalNQueens(self, n):
            """
            :type n: int
            :rtype: int
            """
            if n <= 0:
                return 0
            self.board = [] * n
            for i in xrange(n):
                self.board.append(['.']*n)
            self.res = 0
            self.myTotalNQueens(n, 0)
            return self.res
    
        def myTotalNQueens(self, n, row):
            """
            :type n: int
            :rtype: int
            """
            if row == n:
                self.res += 1
                return
    
            for col in xrange(n):
                self.board[row][col] = 'Q'
                if self.validQueeens(n, row, col):
                    self.myTotalNQueens(n, row+1)
                self.board[row][col] = '.'
    
        def validQueeens(self, n, row, col):
            # check column
            for index in xrange(n):
                if index == row: continue
                if self.board[index][col] == 'Q':
                    return False
    
            # Check triangle
            for i in xrange(n):
                for j in xrange(n):
                    if i == row and j == col: continue
                    if abs(i-row) == abs(j-col) and self.board[i][j] == 'Q':
                        return False
            return True
    
    s = Solution()
    print s.totalNQueens(1) # 1
    print s.totalNQueens(4) # 2