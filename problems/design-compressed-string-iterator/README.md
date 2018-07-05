# Leetcode: Design Compressed String Iterator     :BLOG:Medium:


---

Design Compressed String Iterator  

---

Similar Problems:  
-   [Basic Calculator](https://code.dennyzhang.com/basic-calculator)
-   [Review: Object-Oriented Design Problems](https://code.dennyzhang.com/review-oodesign)
-   Tag: [oodesign](https://code.dennyzhang.com/tag/oodesign)

---

Design and implement a data structure for a compressed string iterator. It should support the following operations: next and hasNext.  

The given compressed string will be in the form of each letter followed by a positive integer representing the number of this letter existing in the original uncompressed string.  

next() - if the original string still has uncompressed characters, return the next letter; Otherwise return a white space.  
hasNext() - Judge whether there is any letter needs to be uncompressed.  

Note:  
Please remember to RESET your class variables declared in StringIterator, as static/class variables are persisted across multiple test cases. Please see here for more details.  

Example:  

    StringIterator iterator = new StringIterator("L1e2t1C1o1d1e1");
    
    iterator.next(); // return 'L'
    iterator.next(); // return 'e'
    iterator.next(); // return 'e'
    iterator.next(); // return 't'
    iterator.next(); // return 'C'
    iterator.next(); // return 'o'
    iterator.next(); // return 'd'
    iterator.hasNext(); // return true
    iterator.next(); // return 'e'
    iterator.hasNext(); // return false
    iterator.next(); // return ' '

Github: [challenges-leetcode-interesting](https://github.com/DennyZhang/challenges-leetcode-interesting/tree/master/design-compressed-string-iterator)  

Credits To: [leetcode.com](https://leetcode.com/problems/design-compressed-string-iterator/description/)  

Leave me comments, if you have better ways to solve.  

---

    ## Blog link: https://code.dennyzhang.com/design-compressed-string-iterator
    ## Basic Ideas:
    ##
    ## Complexity:
    class StringIterator:
    
        def __init__(self, compressedString):
            """
            :type compressedString: str
            """
            self.string = compressedString
            self.index, self.count, self.ch = 0, 0, None
            self.length = len(self.string)
    
        def next(self):
            """
            :rtype: str
            """
            if self.hasNext() is False:
                return ' '
    
            if self.count != 0:
                self.count -= 1
            else:
                # fetch the next character
                self.ch = self.string[self.index]
                self.index += 1
                # find the count
                v = ''
                while self.index < self.length:
                    char = self.string[self.index]
                    if char.isdigit() is False: break
                    v = '%s%s' % (v, char)
                    self.index += 1
                self.count = int(v) - 1
            return self.ch
    
        def hasNext(self):
            """
            :rtype: bool
            """
            if self.index == self.length and self.count == 0:
                return False
            else:
                return True
    
    # Your StringIterator object will be instantiated and called as such:
    # obj = StringIterator(compressedString)
    # param_1 = obj.next()
    # param_2 = obj.hasNext()