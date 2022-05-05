# LeetCode刷题tips

sort()必须时静态成员函数

```cpp
static bool cmp(vector<int>a,vector<int>b){
        return a[1]<b[1];
}

sort (...,...,cmp);
```



