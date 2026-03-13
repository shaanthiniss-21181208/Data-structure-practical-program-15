from collections import deque

class Solution:
    
    def maxOfSubarrays(self, arr, k):
        
        dq = deque()   # stores indices
        result = []

        for i in range(len(arr)):
            
            # Remove indices out of window
            if dq and dq[0] == i - k:
                dq.popleft()

            # Remove smaller elements
            while dq and arr[dq[-1]] < arr[i]:
                dq.pop()

            dq.append(i)

            # Window ready
            if i >= k - 1:
                result.append(arr[dq[0]])

        return result# Data-structure-practical-program-15
