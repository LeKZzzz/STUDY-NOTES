# LeetCode

----

# 线性表

---



## Q1	两数之和	-E

循环，O(mn)

```c++
class Solution {
public:
    vector<int> twoSum(vector<int> &nums, int target) {
        vector<int> result, larger, lower, equal;
        for (int i = 0; i < nums.size(); ++i) {
            if (nums[i] < target / 2) lower.push_back(i);
            else if (nums[i] == target / 2) equal.push_back(i);
            else larger.push_back(i);
        }
        if (equal.size() >= 2) {
            result.push_back(equal[0]);
            result.push_back(equal[1]);
            return result;
        } else if (equal.size() == 1) {
            if (target > 0)
                lower.push_back(equal[0]);
            else
                larger.push_back(equal[0]);
        }
        for (int i = 0; i < larger.size(); ++i) {
            for (int j = 0; j < lower.size(); ++j) {
                if (nums[larger[i]] + nums[lower[j]] == target) {
                    result.push_back(larger[i]);
                    result.push_back(lower[j]);
                }
            }
        }
        return result;
    }
};
```

哈希表，O(n)

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> hashtable;
        for (int i = 0; i < nums.size(); ++i) {
            auto it = hashtable.find(target - nums[i]);
            if (it != hashtable.end()) {
                return {it->second, i};
            }
            hashtable[nums[i]] = i;
        }
        return {};
    }
};
```



## Q27	移除元素	-E

双指针，*O*(*n*)

```c
int removeElement(int *nums, int numsSize, int val) {
    int p = 0, q = 1;
    if (numsSize == 1) {
        if (nums[0] != val) {
            return 1;
        } else {
            return 0;
        }
    }else if (numsSize == 0){
        return 0;
    }
    for (; q < numsSize; q++) {
        if (nums[p] != val)
            p++;
        nums[p] = nums[q];
    }
    if (nums[p] == val && q == numsSize) p--;
    return p + 1;
}
```



双指针优化，O(n)

```c++
class Solution {
public:
    int removeElement(vector<int> &nums, int val) {
        if (nums.size() == 0) return 0;
        int p = 0, q = nums.size() - 1;
        while (p < q) {
            while (nums[p] != val && p < q) p++;
            while (nums[q] == val && p < q) q--;
            if (p < q) {
                nums[p] = nums[q];
                p++;
                q--;
            }
        }
        if (p == q)
            if (nums[p] == val)
                p--;
        if (p > q)
            p--;
        return p + 1;
    }
};

//官方：
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int left = 0, right = nums.size();
        while (left < right) {
            if (nums[left] == val) {
                nums[left] = nums[right - 1];
                right--;
            } else {
                left++;
            }
        }
        return left;
    }
};
```



## Q26	删除有序数组中的重复项	-E

```c
int removeDuplicates(int* nums, int numsSize){
    int p=0,q=1,tmp;
    for(;q<numsSize;q++){
        if(nums[p]!=nums[q])    p++;
        tmp=nums[p];
        nums[p]=nums[q];
        nums[q]=tmp;
    }
    return p+1;
}
```

```c++
class Solution {
public:
    int removeDuplicates(vector<int> &nums) {
        int p = 0;
        for (int i = 0; i < nums.size(); ++i) {
            if (nums[p] != nums[i]) p++;
            if (i - p >= 1)
                nums[p] = nums[i];
        }
        return p + 1;
    }
};
```



## Q1828	统计一个圆中点的数目	-M

```c++
class Solution {
public:
    vector<int> countPoints(vector<vector<int>> &points, vector<vector<int>> &queries) {
        vector<int> ans;
        float distance;
        for (int i = 0; i < queries.size(); ++i) {
            ans.push_back(0);
            for (int j = 0; j < points.size(); ++j) {
//                if (points[j][0]>queries[i][0]+queries[i][2]||points[j][0]<queries[i][0]-queries[i][2]) continue;
//                if (points[j][1]>queries[i][1]+queries[i][2]||points[j][1]<queries[i][1]-queries[i][2]) continue;

                distance = ::sqrt(::pow(points[j][0] - queries[i][0], 2) + ::pow(points[j][1] - queries[i][1], 2));
                if (distance <= queries[i][2])
                    ans[i]++;
            }
        }
        return ans;
    }
};
```



## Q1920	基于排列构建数组	-E

```c++
class Solution {
public:
    vector<int> buildArray(vector<int>& nums) {
        vector<int> result;
        for (int i = 0; i < nums.size(); ++i) {
            result.push_back(nums[nums[i]]);
        }
        return result;
    }
};
```



## Q2011	执行操作后的变量值	-E

```c++
class Solution {
public:
    int finalValueAfterOperations(vector<string>& operations) {
        int result=0;
        for (int i = 0; i < operations.size(); ++i) {
            if(operations[i][0]=='+'||operations[i][2]=='+')    result++;
            if(operations[i][0]=='-'||operations[i][2]=='-')    result--;
        }
        return result;
    }
};
```



## Q807	保持城市天际线	-M

```c++
class Solution {
public:
    int maxIncreaseKeepingSkyline(vector<vector<int>>& grid) {
        int result=0,rmax,cmax,n=grid[0].size();
        vector<int>row;
        vector<int>column;

        for (int i = 0; i < n; ++i) {
            rmax=grid[i][0];
            cmax=grid[0][i];
            for (int j = 0; j < n; ++j) {
                rmax=rmax<grid[i][j]?grid[i][j]:rmax;
                cmax=cmax<grid[j][i]?grid[j][i]:cmax;
            }
            row.push_back(rmax);
            column.push_back(cmax);
        }
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                result+=(row[i]<=column[j]?row[i]-grid[i][j]:column[j]-grid[i][j]);
            }
        }
        return result;
    }
};
```



## Q1255	得分最高的单词集合	-H

回溯法

```c++
class Solution {
public:
    vector<string> m_words;
    vector<char> m_letters;
    vector<int> m_score;
    int count[26], tmp[26];
    int best = 0, curbest = 0;
    bool flag[26];
//    int x[5];

    int maxScoreWords(vector<string> &words, vector<char> &letters, vector<int> &score) {
        m_words = words;
        m_letters = letters;
        m_score = score;

        for (int i = 0; i < 25; ++i) {
            count[i] = 0;
        }
        for (int i = 0; i < letters.size(); ++i) {
            count[letters[i] - 97]++;
        }

        backtrack(0, words.size());
        return best;
    }

    void backtrack(int i, int n) {
        if (i == n) best = curbest >= best ? curbest : best;
        else {
            if (check(i)) {
//                x[i] = 1;
                cost(i);
                backtrack(i + 1, n);
                reset(i);
            }
//            x[i] = 0;
            backtrack(i + 1, n);
        }
    }

    bool check(int n) {
        for (int i = 0; i < 26; ++i) {
            flag[i] = false;
        }
        for (int i = 0; i < m_words[n].size(); ++i) {
            if (!flag[m_words[n][i] - 97]) {
                flag[m_words[n][i] - 97] = true;
                tmp[m_words[n][i] - 97] = 1;
            } else {
                tmp[m_words[n][i] - 97]++;
            }
            if (count[m_words[n][i] - 97] < tmp[m_words[n][i] - 97])
                return false;
        }
        return true;
    }

    void cost(int n) {
        for (int i = 0; i < m_words[n].size(); ++i) {
            count[m_words[n][i] - 97]--;
            curbest += m_score[m_words[n][i] - 97];
        }
    }

    void reset(int n) {
        for (int i = 0; i < m_words[n].size(); ++i) {
            count[m_words[n][i] - 97]++;
            curbest -= m_score[m_words[n][i] - 97];
        }
    }
};
```



## Q1769	移动所有球到每个盒子所需的最小操作数	-M

双循环，O(n^2^)

```c++
class Solution {
public:
    vector<int> minOperations(string boxes) {
        vector<int> box;
        vector<int> result;
        int sum;
        for (int i = 0; i < boxes.size(); ++i) {
            if(boxes[i] != '0')
            box.push_back(i);
        }

        for (int i = 0; i < boxes.size(); ++i) {
            sum = 0;
            for (int j = 0; j < box.size(); ++j) {
                sum += box[j] > i ? (box[j] - i) : (i - box[j]);
            }
            result.push_back(sum);
        }
        return result;
    }
};
```

两次遍历

```c++
class Solution {
public:
    vector<int> minOperations(string boxes) {
        vector<int> box;
        vector<int> result_l(boxes.size(), 0);
        vector<int> result_r(boxes.size(), 0);
        vector<int> count_l(boxes.size(), 0);
        vector<int> count_r(boxes.size(), 0);
        vector<int> result;
        for (int i = 0; i < boxes.size(); ++i)
            box.push_back(boxes[i] - '0');


        for (int i = 1; i < boxes.size(); ++i) {
            if (box[i - 1] == 1)
                count_l[i] = count_l[i - 1] + 1;
            else
                count_l[i] = count_l[i - 1];
            result_l[i] = result_l[i - 1] + count_l[i];
        }

        for (int i = boxes.size() - 2; i >= 0; --i) {
            if (box[i + 1] == 1)
                count_r[i] = count_r[i + 1] + 1;
            else
                count_r[i] = count_r[i + 1];
            result_r[i] = result_r[i + 1] + count_r[i];
        }

        for (int i = 0; i < boxes.size(); ++i)
            result.push_back(result_l[i] + result_r[i]);


        return result;
    }
};
```



## Q2208	将数组和减半的最少操作次数	-M

> 贪心+优先队列

```c++
class Solution {
public:
    int halveArray(vector<int> &nums) {
        double result = 0, tmp;
        int ans = 0;
        double sum = accumulate(nums.begin(), nums.end(), 0.0);
        priority_queue<double> q(nums.begin(), nums.end());
        while (result < sum / 2) {
            tmp = q.top();
            result += tmp / 2;
            q.pop();
            q.push(tmp / 2);
            ans++;
        }
        return ans;
    }

};
```



## Q2500	删除每行中的最大值	-E

排序

```c++
class Solution {
public:
    int deleteGreatestValue(vector<vector<int>> &grid) {
        int result = 0, max;
        int m = grid.size(), n = grid[0].size();
        for (int i = 0; i < m; ++i)
            sort(grid[i].begin(), grid[i].end());
        for (int i = 0; i < n; ++i) {
            max = 0;
            for (int j = 0; j < m; ++j) {
                max = max >= grid[j][i] ? max : grid[j][i];
            }
            result += max;
        }
        return result;
    }
};
```



## Q453 最小操作次数使数组元素相等 -M

> n-1个数同时+1，相当于每次有1个数自身-1，因为只能做减法，所以数组最后的数只能是最小值，这样的话每个元素减去最小值求其和就是答案。

```c++
class Solution {
public:

    int min;
    int minIndex;
    int n;

    int minMoves(vector<int> &nums) {
        int result = 0;
        n = nums.size();
        min = nums[0];
        minIndex = 0;
        for (int i = 1; i < n; ++i) {
            if (nums[i] < min) {
                min = nums[i];
                minIndex = i;
            }
        }
        for (int i = 0; i < n; ++i) {
            if (i != minIndex && nums[i] != min)
                result += (nums[i] - min);
        }
        return result;
    }
};
```



## Q665 非递减数列 -M

> 要满足题意，我们能够在数组中找到这两个数`[x, y]`，其中`y < x`。很明显`[..., x]`和`[y, ...]`满足非递减条件，如果不满足则说明修改次数必然超过1次。接下来我们再考虑边界问题：
>
> - 如果数组内元素数量n<=2，必然能够通过修改1次元素使数列满足非递减
> - 如果x是最左侧元素，则通过修改x使其小于y就能使数列满足非递减
> - 如果x是最右侧元素，则通过修改y使其大于x就能使数列满足非递减
> - 设x的上一个数为k，y的下一个数为t
>     - `k <= y`通过修改x可满足
>     - `t >= x`通过修改y可满足

```C++
class Solution {
public:

    bool checkIncremental(vector<int> nums, int beginIndex, int endIndex) {
        int begin = beginIndex < 0 ? 0 : beginIndex;
        int end = endIndex >= nums.size() ? nums.size() : endIndex;
        for (int i = begin + 1; i < end; ++i) {
            if (nums[i] < nums[i - 1])
                return false;
        }
        return true;
    }

    bool checkPossibility(vector<int> &nums) {
        if (nums.size() <= 2)
            return true;
        for (int i = 1; i < nums.size(); ++i) {
            if (nums[i] >= nums[i - 1])
                continue;

            if (!checkIncremental(nums, i,nums.size()))
                return false;
            if ((i + 1) < nums.size()) {
                if (nums[i + 1] > nums[i - 1])
                    return true;
                if ((i - 2) < 0)
                    return true;
                else if (nums[i] >= nums[i - 2])
                    return true;
                else
                    return false;
            } else
                return true;
        }
        return true;
    }
};
```



## Q283 移动零 -E

> 遍历数组，查找所有非零的元素并将其放置到数组前，使用双指针即可，左指针指向下一个待放置的位置，右指针寻找非0的元素

```cpp
class Solution {
public:
    int count = 0;
    int left = 0, right;

    void moveZeroes(vector<int> &nums) {
        for (right = 0; right < nums.size(); right++) {
            if (nums[right] != 0) {
                nums[left] = nums[right];
                left++;
            } else
                count++;
        }
        for (int i = nums.size() - count; i < nums.size(); ++i)
            nums[i] = 0;
    }
};
```



## Q189 旋转数组 -M

> **关键点：元素旋转后的位置 = (index+k)%n**
>
> - 方法一：使用额外的数组
>
> - 方法二：数组翻转
>
>     > ```
>     > nums = "----->-->"; k =3
>     > result = "-->----->";
>     > 
>     > reverse "----->-->" we can get "<--<-----"
>     > reverse "<--" we can get "--><-----"
>     > reverse "<-----" we can get "-->----->"
>     > this visualization help me figure it out :)
>     > ```
>     >
>     > https://leetcode.com/problems/rotate-array/solutions/54250/Easy-to-read-Java-solution/
>
> - 方法三：环状替换，只使用一个中间变量而不需要开辟新的数组

```cpp
class Solution {
public:
//    vector<int> tmp;
//    int n;

    void rotate(vector<int> &nums, int k) {
// 方法一
/*        n = nums.size();
        tmp.resize(n);
        for (int i = 0; i < nums.size(); ++i)
            tmp[(i + k) % n] = nums[i];
        nums.assign(tmp.begin(), tmp.end());*/
// 方法二
      k %= nums.size();
        reverse(nums.begin(), nums.end());
        reverse(nums.begin(), nums.begin() + k);
        reverse(nums.begin() + k, nums.end());
//方法三
/*        int n = nums.size();
        k = k % n;
        int count = gcd(k, n);
        for (int start = 0; start < count; ++start) {
            int current = start;
            int prev = nums[start];
            do {
                int next = (current + k) % n;
                swap(nums[next], prev);
                current = next;
            } while (start != current);
        }*/
    }
};
```



## Q396 旋转函数 -M

> ![image-20240313122340381](LeetCode/image-20240313122340381.png)

```cpp
class Solution {
public:

    int maxRotateFunction(vector<int> &nums) {
        int n = nums.size();
        int sum = 0, res, tmp = 0;
        for (int i = 0; i < n; ++i)
            sum += nums[i];
        for (int i = 0; i < n; ++i) {
            tmp += i * nums[i];
            res = tmp;
        }
        for (int i = 1; i < n; ++i) {
            tmp = tmp + sum - n * nums[n - i];
            res = max(res, tmp);
        }
        return res;
    }
};
```



# 树

---

## Q2569	更新数组后处理求和查询	-H

线段树

```c++
```

