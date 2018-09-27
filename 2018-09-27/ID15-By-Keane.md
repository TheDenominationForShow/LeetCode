>create by jzf@2018/09/27 北河大傻逼
## 15. 三数之和@2018/09/27
```c++
static auto X = [] {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return nullptr;
}();

class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> v;
        if (nums.size() < 3) {
            return v;
        }
        sort(nums.begin(), nums.end());
        if (nums[0] > 0 || nums[nums.size() - 1] < 0) {
            return v;
        }
        int idx = -1;
        for (int i = 0; i < nums.size(); ++i) {
            if (nums[i] >= 0) {
                idx = i;
                break;
            }
        }
        if (idx == -1) {
            return v;
        }
        if (nums.size() > idx + 2 && nums[idx] == 0 && nums[idx + 1] == 0 && nums[idx + 2] == 0) {
            v.push_back(vector<int>{0, 0, 0});
        }
        set<int> s1;
        for (int i = 0; i < idx; ++i) {
            s1.insert(nums[i]);
        }
        for (auto x : s1) {
            int j = nums.size() - 1;
            for (int i = idx; i < j;) {
                if (nums[i] + nums[j] + x == 0) {
                    v.push_back(vector<int>{x, nums[i], nums[j]});
                    int m = nums[i++];
                    int n = nums[j--];
                    bool cont = true;
                    while (cont) {
                        cont = false;
                        if (m == nums[i]) {
                            ++i;
                            cont = true;
                        }
                        if (n == nums[j]) {
                            --j;
                             cont = true;
                        }
                    }
                } else if (nums[i] + nums[j] + x > 0) {
                    --j;
                } else {
                    ++i;
                }
            }
        }
        set<int> s2;
        for (int i = idx; i < nums.size(); ++i) {
            s2.insert(nums[i]);
        }
        for (auto x : s2) {
            int j = idx - 1;
            for (int i = 0; i < j; ) {
                if (nums[i] + nums[j] + x == 0) {
                    v.push_back(vector<int>{x, nums[i], nums[j]});
                    int m = nums[i++];
                    int n = nums[j--];
                    bool cont = true;
                   while (cont) {
                        cont = false;
                        if (m == nums[i]) {
                            ++i;
                            cont = true;
                        }
                        if (n == nums[j]) {
                            --j;
                             cont = true;
                        }
                    }
                } else if (nums[i] + nums[j] + x > 0) {
                    --j;
                } else {
                    ++i;
                }
            }
        }
        return v;
    }
};
```