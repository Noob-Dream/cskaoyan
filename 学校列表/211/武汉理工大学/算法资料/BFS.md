# BFS

## Catch That Cow

Description

Farmer John has been informed of the location of a fugitive cow and wants to catch her immediately. He starts at a point N (0 ≤ N ≤ 100,000) on a number line and the cow is at a point K (0 ≤ K ≤ 100,000) on the same number line. Farmer John has two modes of transportation: walking and teleporting.

* Walking: FJ can move from any point X to the points X - 1 or X + 1 in a single minute
* Teleporting: FJ can move from any point X to the point 2 × X in a single minute.

If the cow, unaware of its pursuit, does not move at all, how long does it take for Farmer John to retrieve it?

Input
Line 1: Two space-separated integers: N and K

Output
Line 1: The least amount of time, in minutes, it takes for Farmer John to catch the fugitive cow.

Sample Input

5 17

Sample Output

4

```
5 17
```

Sample Output

```
4
```

```CPP
#include <iostream>
#include <queue>
#include <cstring>
using namespace std;
const int MAXN = 100005;
struct Status{
    int x;//x为当前位置
    int t;//t为已经消耗的时间
    Status(int x,int t):x(x),t(t){};
};
bool visit[MAXN];
int BFS(int n,int k){
    queue<Status> Sq;//新建一个队列用来存储所有可能经过的位置
    Sq.push(Status(n,0));//压入初始状态
    visit[n] = true;//当前位置n已经被访问过了
    while (!Sq.empty()) {//队列中还有元素的时候不断弹出
        Status cur = Sq.front();//cur为队头元素
        Sq.pop();
        if (cur.x == k ) {//如果队头元素恰好走到路径就返回
            return cur.t;
        }
        for (int i = 0; i <= 2; ++i) {//分别对三种可能的走法进行分析，如果没走到终点就都进入队列
            Status next(cur.x,cur.t + 1);//next为下一点的位置以及时间
            if (i == 0) {
                next.x++;//加1
            }
            if (i == 1) {
                next.x--;//减1
            }
            if (i == 2) {
                next.x*=2;//乘2
            }
            if (next.x > MAXN || next.x < 0 || visit[next.x]) {
                continue;//位置超出范围（过小，过大，访问过）
            }
            Sq.push(next);//新位置进入队列
            visit[next.x] = true;//标记访问过位置next
        }
    }
    return 0;
}
int main(){
    int n,k;//n是起点，k是终点
    cin >> n >> k;
    memset(visit, false, sizeof(visit));
    cout << BFS(n, k);
    return 0;
}

```

## Find The Multiple

Description

Given a  positive integer n, write a program to find out a nonzero multiple m of n whose decimal representation contains only the digits 0 and 1. You may  assume that n is not greater than 200 and there is a corresponding m  containing no more than 100 decimal digits.

Input

The input file may contain multiple test cases. Each line contains a value  of n (1 <= n <= 200). A line containing a zero terminates the  input.

Output

For  each value of n in the input print a line containing the corresponding  value of m. The decimal representation of m must not contain more than  100 digits. If there are multiple solutions for a given value of n, any  one of them is acceptable.

Sample Input

```
2
6
19
0
```

Sample Output

```
10
100100100100100100
111111111111111111
```



```cpp
#include <iostream>
#include <queue>
#include <cstdio>
using namespace std;
void BFS(int n){
    queue<long long> Q;
    Q.push(1);//放入初始值1
    while (!Q.empty()) {//队列不为空的时候就弹出
        long long cur = Q.front();//弹出队头元素
        Q.pop();
        if (cur % n == 0) {//队头元素满足条件
            printf("%lld\n",cur);//输出
            return;
        }
        Q.push(cur * 10);//不满足条件时，原来数字添0后入队
        Q.push(cur * 10 + 1);//原来数字添1后入队
    }
}
int main(){
    int n;
    while (scanf("%d",&n)!=EOF) {
        if (n == 0) {
            break;
        }
        BFS(n);
    }
    return 0;
}
```

## 二叉树层次遍历



从上到下打印出二叉树的每个节点，同一层的节点按照从左到右的顺序打印。

 

例如:
给定二叉树: [3,9,20,null,null,15,7],
```cpp
    3
   / \
  9  20
    /  \
   15   7
```

返回：

>   [3,9,20,15,7]

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<int> levelOrder(TreeNode* root) {
        vector<int> result;
        if(root == nullptr) return result;   //判断根节点是否为空
        queue<TreeNode*> Sq;
        Sq.push(root);
        while(!Sq.empty()){
            TreeNode* cur = Sq.front();
            Sq.pop();
            result.push_back(cur->val);
            if(cur->left){
                Sq.push(cur->left);
            }
            if(cur->right){
                Sq.push(cur->right);
            }
        }
        return result;
    }
};
```

## 二叉树之字形遍历(使用栈)

请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。

 

例如:
给定二叉树: [3,9,20,null,null,15,7],
```
    3
   / \
  9  20
    /  \
   15   7
```
返回其层次遍历结果：
```
[
  [3],
  [20,9],
  [15,7]
]
```
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> result;
        if(root == nullptr) return result;   //判断根节点是否为空
        stack<TreeNode*> St1;//用栈存储
        St1.push(root);
        stack<TreeNode*> St2;
        while(!St1.empty() || !St2.empty()){
            if(!St1.empty()){
                result.push_back(vector<int>());
                while(!St1.empty()){
                    TreeNode* cur = St1.top();
                    St1.pop();
                    result.back().push_back(cur->val);
                    if(cur->left != nullptr){
                        St2.push(cur->left);
                    }
                    if(cur->right != nullptr){
                        St2.push(cur->right);
                    }
                }
            }
            if(!St2.empty()){
                result.push_back(vector<int>());
                while(!St2.empty()){
                    TreeNode* cur = St2.top();
                    St2.pop();
                    result.back().push_back(cur->val);
                    if(cur->right != nullptr){
                        St1.push(cur->right);
                    }
                    if(cur->left != nullptr){
                        St1.push(cur->left);
                    }
                }
            }
        }
        return result;
    }
};
```

## 单词接龙II

给定两个单词（beginWord 和 endWord）和一个字典 wordList，找出所有从 beginWord 到 endWord 的最短转换序列。转换需遵循如下规则：

    每次转换只能改变一个字母。
    转换过程中的中间单词必须是字典中的单词。

说明:

    如果不存在这样的转换序列，返回一个空列表。
    所有单词具有相同的长度。
    所有单词只由小写字母组成。
    字典中不存在重复的单词。
    你可以假设 beginWord 和 endWord 是非空的，且二者不相同。

示例 1:

输入:
beginWord = "hit",
endWord = "cog",
wordList = ["hot","dot","dog","lot","log","cog"]

输出:
[
  ["hit","hot","dot","dog","cog"],
  ["hit","hot","lot","log","cog"]
]

示例 2:

输入:
beginWord = "hit"
endWord = "cog"
wordList = ["hot","dot","dog","lot","log"]

输出: []

解释: endWord "cog" 不在字典中，所以不存在符合要求的转换序列。

```c++
const int INF = 1 << 20;

class Solution {
private:
    unordered_map<string, int> wordId;
    vector<string> idWord;
    vector<vector<int>> edges;
public:
    vector<vector<string>> findLadders(string beginWord, 
                                       string endWord, vector<string>& wordList) {
        int id = 0;
        for (const string& word : wordList) {
            if (!wordId.count(word)) {
                wordId[word] = id++;
                idWord.push_back(word);
            }
        }//创建WORD-ID(unordered_map)映射以及ID-WORD映射(vector<string>)
        if (!wordId.count(endWord)) {
            return {};
        }//不存在目标单词，返回空
        if (!wordId.count(beginWord)) {
            wordId[beginWord] = id++;
            idWord.push_back(beginWord);
        }//添加起始单词
        edges.resize(idWord.size());//edges[i][j]表示ID为i与j的单词之间有边(只差一个字母))
        for (int i = 0; i < idWord.size(); i++) {
            for (int j = i + 1; j < idWord.size(); j++) {
                if (transformCheck(idWord[i], idWord[j])) {
                    edges[i].push_back(j);
                    edges[j].push_back(i);
                }
            }
        }//创建edges二维矩阵
        const int dest = wordId[endWord];//dest为目标单词的ID
        vector<vector<string>> res;//变化的单词路径
        queue<vector<int>> q;//BFS的队列
        vector<int> cost(id, INF);
        //cost[i] 表示 beginWord 对应的点到第 i 个点的代价（即转换次数）。
        //初始情况下其所有元素初始化为无穷大。
        //所有的单词耗费初始化为无限远
        q.push(vector<int>{wordId[beginWord]});//队列放入起始单词
        cost[wordId[beginWord]] = 0;
        while (!q.empty()) {
            //将起点加入队列开始广度优先搜索，队列的每一个节点中保存从起点开始的所有路径。
            vector<int> now = q.front();
            //取出与队列首单词相连的单词ID数组(相差一个字母的单词数组)为now
            q.pop();//弹出首单词ID
            int last = now.back();//last为now的最后一个ID，即相邻的最后一个单词
            /*
             对于每次取出的节点 now，每个节点都是一个数组，数组中的最后一个元素为当前路径的最后节点 last:
    		若该节点为终点，则将其路径转换为对应的单词存入答案;
    		若该节点不为终点，则遍历和它连通的节点（假设为 to ）中
    		满足 cost[to]>=cost[now]+1的加入队列，
    		并更新 cost[to]=cost[now]+1。
    		如果 cost[to]<cost[now]+1，
    		说明这个节点已经被访问过，不需要再考虑。
            */
            if (last == dest) {//若到达终点单词,将其路径转换为对应的单词存入答案;
                vector<string> tmp;
                for (int index : now) {//对now数组中的每个单词ID进行遍历
                    tmp.push_back(idWord[index]);
                }
                res.push_back(tmp);
            } else {//不为终点，则遍历和它连通的节点（假设为 to ）
                for (int i = 0; i < edges[last].size(); i++) {//对ID为last邻接的单词进行扫描
                    int to = edges[last][i];//to为邻接的单词ID
                    if (cost[last] + 1 <= cost[to]) {
                        cost[to] = cost[last] + 1;
                        vector<int> tmp(now);
                        tmp.push_back(to);
                        q.push(tmp);
                    }
                }
            }
        }
        return res;
    }

    bool transformCheck(const string& str1, const string& str2) {
        //检查它们是否可以通过改变一个字母进行互相转换。如果可以，则在这两个点之间建一条双向边。
        int differences = 0;//不同字母的个数
        for (int i = 0; i < str1.size() && differences < 2; i++) {
            if (str1[i] != str2[i]) {//对两个单词的字母一一对比，有不同的dif自增，大于1则跳出
                ++differences;
            }
        }
        return differences == 1;
    }
};

```
