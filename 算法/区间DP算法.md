# DP区间算法
DP区间算法，即动态规划区间算法，是一种高效的算法设计策略，主要用于解决具有重叠子问题和最优子结构性质的问题。其核心思想是将原问题分解为若干个子问题，并保存子问题的解，以避免重复计算。在区间型问题中，DP区间算法尤为有效，它通过定义状态、状态转移方程和边界条件，逐步求解子区间，并最终得到整个区间的解。

DP区间算法的基本步骤包括：

1.状态定义：根据问题的特点，定义状态以表示子问题的解。在区间问题中，状态通常与区间的起始和结束位置相关。
2.状态转移方程：建立状态转移方程，描述子问题之间的关系。通过已知子问题的解，推导出更大子问题的解。
3.初始化边界条件：为最小的子问题设定初始解，通常是问题的基本情况或边界情况。
4.填表或迭代求解：根据状态转移方程和边界条件，逐步求解所有子问题的解，直至得到整个问题的解。
# 多多的回文修建
多多有一个长度为 n 的字符串，这个字符串由 26 个小写字母组成。多多可以对这个字符串进行多次操作，每次操作可以把该字符串中一段连续的回文子串删除（单个字符也属于回文串），删除后剩下的串会拼在一起。请问最少需要多少次操作可以将这个字符串删光。

## 输入描述

第一行，包含一个正整数 T (1 ≤ T ≤ 20) 代表测试数据的组数。

对于每组测试数据，仅有一行，代表这个字符串。

(1 ≤ n ≤ 500)

保证 ∑n 不超过 3000

## 输出描述

对于每组数据输出一行整数，代表多多在进行最少多少次操作后，可以将这个字符串删光。

## 补充说明

示例 1

输入:
```
3
mwapd
tvuvv
yxxmi
```
输出:
```
5
3
4
```
说明: 对于字符串 “tvuvv”， 第一步: 删除 “u”，此时剩下 “tvvv”， 第二步: 删除 “vvv”，此时剩下 “t”。

## 解法
```
#include <iostream>
#include <vector>
#include <string>
#include <climits>

using namespace std;

class Solution {
public:
    void solve() {
        int T;
        cin >> T;

        for (int t = 0; t < T; t++) {
            string s;
            cin >> s;

            if (s.empty()) {
                cout << 0 << endl;
                continue;
            }

            int n = s.length();

            if (n == 1) {
                cout << 1 << endl;
                continue;
            }

            vector<vector<int> > dp(n, vector<int>(n, 1000));

            for (int i = 0; i < n; i++) {
                dp[i][i] = 1;
            }

            for (int j = 1; j < n; j++) {
                for (int i = j - 1; i >= 0; i--) {
                    if (i == j - 1) {
                        dp[i][j] = (s[i] == s[j]) ? 1 : 2;
                        continue;
                    }

                    if (s[i] == s[j]) {
                        dp[i][j] = min(dp[i][j], dp[i + 1][j - 1]);
                    }

                    for (int k = i; k < j; k++) {
                        dp[i][j] = min(dp[i][j], dp[i][k] + dp[k + 1][j]);
                    }
                }
                
                for (int i = 0; i < n; i++)
                {
                	for (int k = 0; k < n; k++)
                	{
                		cout << dp[i][k] << " ";
					}
					cout << endl;
				}
            }

            cout << dp[0][n - 1] << endl;
        }
    }
};

int main() {
    Solution solution;
    solution.solve();

    return 0;
}
```
