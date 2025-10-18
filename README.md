# Maximum-Number-of-Distinct-Elements-After-Operations

You are given an integer array nums and an integer k.
You are allowed to perform the following operation on each element of the array at most once:
Add an integer in the range [-k, k] to the element.
Return the maximum possible number of distinct elements in nums after performing the operations.


from typing import List

class Solution:
    def maxDistinctElements(self, nums: List[int], k: int) -> int:
        nums.sort()
        last_picked = -10**18
        distinct_count = 0

        for num in nums:
            lower_bound = num - k
            upper_bound = num + k
            if last_picked < lower_bound:
                last_picked = lower_bound
            else:
                last_picked += 1
            if last_picked <= upper_bound:
                distinct_count += 1
            else:
                last_picked -= 1

        return distinct_count
 
