# 494. 目标和

## 题目

[来源](https://leetcode-cn.com/problems/target-sum/)

给你一个整数数组 `nums` 和一个整数 `target` 。

向数组中的每个整数前添加 `'+'` 或 `'-'` ，然后串联起所有整数，可以构造一个 **表达式** ：

- 例如，`nums = [2, 1]` ，可以在 `2` 之前添加 `'+'` ，在 `1` 之前添加 `'-'` ，然后串联起来得到表达式 `"+2-1"` 。

返回可以通过上述方法构造的、运算结果等于 target 的不同 **表达式** 的数目。

**示例 1：**

```
输入：nums = [1,1,1,1,1], target = 3
输出：5
解释：一共有 5 种方法让最终目标和为 3 。
-1 + 1 + 1 + 1 + 1 = 3
+1 - 1 + 1 + 1 + 1 = 3
+1 + 1 - 1 + 1 + 1 = 3
+1 + 1 + 1 - 1 + 1 = 3
+1 + 1 + 1 + 1 - 1 = 3
```

**示例 2：**

```
输入：nums = [1], target = 1
输出：1
```

**提示：**

- `1 <= nums.length <= 20`
- `0 <= nums[i] <= 1000`
- `0 <= sum(nums[i]) <= 1000`
- `-1000 <= target <= 100`

## 解题

#### Python

1. 用递归的方式，因为每个数只有两种操作方式，加或者减，所以如果要得到目标值，需要前几个数先得到目标值加上最后一个数或减去最后一个数得到的目标值，举例：

   ```
   输入：nums = [1,1,1,1,1], target = 3
   输出：5
   解释：
   f(5, target=3) = (f(4, target=2) + 1) 或 (f(4, target=4) - 1)
   f(4, target=2) = (f(3, target=1) + 1) 或 (f(3, target=3) - 1)
   f(4, target=4) = (f(3, target=3) + 1) 或 (f(3, target=5) - 1)
   ...
   f(3, target=1) = (f(2, target=0) + 1) 或 (f(3, target=2) - 1)
   ...
   f(2, target=2) = (f(1, target=1) + 1) 或 (f(1, target=3) - 1)
   ...
   f(1, target=1) = (f(0, target=0) + 1) 或 (f(0, target=2) - 1)
   f(0) = 0 # 因为只剩一个数也有两种操作
   ```

   根据思路写出代码：

   ```python
   class Solution:
       def findTargetSumWays(self, nums: List[int], target: int) -> int:
           if len(nums) == 0:
               return 0
   
           if len(nums) == 1 and nums[0] == 0 and target == 0:
               return 2
   
           if len(nums) == 1:
               return 1 if nums[0] == target or - nums[0] == target else 0
   
           return self.findTargetSumWays(nums[:-1], target - nums[-1]) + \
                  self.findTargetSumWays(nums[:-1], target + nums[-1])
   ```

   代码没有问题，leetcode在线运行，本地跑都没有出错，但提交后显示超时，所以需要优化一下。

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [超出时间限制](https://leetcode-cn.com/submissions/detail/184619155/) | N/A      | N/A      | Python3 | 2021/06/07 09:22 | 添加备注 |

2. 我们大胆猜测，同样的数组和target应该重复算了多次，所以我们可以将运算结果记录下来，减少重复计算。

   ```python
   class Solution:
       def findTargetSumWays(self, nums: List[int], target: int) -> int:
           num_target_ways_map = {}
   
           def find_ways(nums, target, ntwm):
               if len(nums) == 0:
                   return 0
   
               if len(nums) == 1 and nums[0] == 0 and target == 0:
                   return 2
   
               if len(nums) == 1:
                   return 1 if nums[0] == target or - nums[0] == target else 0
   
               def get_ways_from_map(nums, key, target, ntwm):
                   if key in ntwm and target in ntwm[key]:
                       return ntwm[key][target]
                   else:
                       ways = find_ways(nums, target, ntwm)
                       if key not in ntwm:
                           ntwm[key] = {}
                       ntwm[key][target] = ways
                       return ways
   
               return get_ways_from_map(nums[:-1], len(nums) - 1, target - nums[-1], ntwm) + \
                      get_ways_from_map(nums[:-1], len(nums) - 1, target + nums[-1], ntwm)
   
           return find_ways(nums, target, num_target_ways_map)
   ```

   这次通过了，没有超时。

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [通过](https://leetcode-cn.com/submissions/detail/184629050/) | 460 ms   | 15.4 MB  | Python3 | 2021/06/07 09:54 | 添加备注 |

   我们可以看到，代码执行仍然耗时很久，那还有没有优化的空间了呢？

3. 有的。通过对Python的了解，我们可以知道，Python数组切片耗费时间复杂度为 `O(k)` , $k$ 为切片的长度，我们应该将每一个长度的数组都保存下来，减少多余切片。

   ```python
   class Solution:
       def findTargetSumWays(self, nums: List[int], target: int) -> int:
           if len(nums) == 0:
               return 0
   
           num_target_ways_map = {}
           num_slice_map = {}
   
           def find_ways(nums, target, ntwm):
               if len(nums) == 1 and nums[0] == 0 and target == 0:
                   return 2
   
               if len(nums) == 1:
                   return 1 if nums[0] == target or - nums[0] == target else 0
   
               def get_ways_from_map(nums, key, target, ntwm):
                   if key in ntwm and target in ntwm[key]:
                       return ntwm[key][target]
                   else:
                       ways = find_ways(nums, target, ntwm)
                       if key not in ntwm:
                           ntwm[key] = {}
                       ntwm[key][target] = ways
                       return ways
   
               length, last_value = len(nums) - 1, nums[-1]
               nonlocal num_slice_map
               if length not in num_slice_map:
                   nums = nums[:-1]
                   num_slice_map[length] = nums
               else:
                   nums = num_slice_map[length]
   
               return get_ways_from_map(nums, length, target - last_value, ntwm) + \
                      get_ways_from_map(nums, length, target + last_value, ntwm)
   
           return find_ways(nums, target, num_target_ways_map)
   ```

   一顿操作猛如虎，回头一看。。。以后再优化。

   | 提交结果                                                     | 执行用时 | 内存消耗 | 语言    | 提交时间         | 备注     |
   | :----------------------------------------------------------- | :------- | :------- | :------ | :--------------- | :------- |
   | [通过](https://leetcode-cn.com/submissions/detail/184639656/) | 452 ms   | 15.2 MB  | Python3 | 2021/06/07 10:23 | 添加备注 |

