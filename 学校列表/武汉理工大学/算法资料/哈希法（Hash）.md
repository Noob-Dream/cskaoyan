# 哈希法（Hash）

##  两数之和

给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。

 

示例:

给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int n = nums.size();
        unordered_map<int,int> Hash;
        for(int i = 0;i < n;++i){
            Hash[nums[i]] = i;
        }// 构造一个哈希表：元素映射到相应的索引
        vector<int> ans;
        for(int i = 0;i < n;++i){
            int other = target - nums[i];
            // 如果 other 存在且不是 nums[i] 本身
            if( Hash.count(other) && Hash[other] != i ){
                ans.push_back(i);
                ans.push_back(Hash[other]);
                break;
            }
        }
        return ans;
    }
};
```

