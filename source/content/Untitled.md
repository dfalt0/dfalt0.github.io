```
class Solution: 
	def twoSum(self, nums: List[int], target: int) -> List[int]: 
		pair_index = {}
		
		for i, num in enumerate(nums):
			if target - num in pair_index:
				return [i, pair_index[target - num]]
			pair_index[num] = i
```


```
class Solution:
	def twoSum(self, nums: List[int], target: int) -> List[int]:
		pair_index = {}

		for i, num in enumarate(num)
```