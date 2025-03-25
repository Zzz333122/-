#include <bits/stdc++.h>
using namespace std;
const int N = 2e7 + 100;

int z[N]; // Z[i]表示s与其后缀s[i,n]的最长公共前缀LCP的长度
// LCP：最长公共前缀
string s, c;
int p[N]; // s与c的最长lCP

int main()
{
    cin >> c >> s;
    int n = s.size();
    int m = c.size();
    s = ' ' + s;
    c = ' ' + c;
    z[1] = n; // Z[1]=n
    int ans = (n + 1);
    for (int i = 2, l = 0, r = 0; i <= n; i++) // 求解Z-box //l,r用来维护区间 l,r满足s[l,r]=s[1,r-l+1]
    {
        if (i <= r)
            z[i] = min(z[i - l + 1], r - i + 1); // 如果i在盒子内 则有s[i,r]=s[i-l+1,r-l+1] ,但是不能超过盒子外，盒子外是未知的
        while (s[l + z[i]] == s[i + z[i]])
            z[i]++; // 超过盒子外就暴力枚举，看一下后面是否匹配，再盒子内一定不匹配了
        if (i + z[i] - 1 > r)
            l = i, r = i + z[i] + 1; // 维护有段带你最靠右的匹配段 并且要保证l<=i
        ans ^= (i * (z[i] + 1));
    }
    cout << ans << endl;
    ans = 0;
    // 看s和c的LCP
    for (int i = 1, l = 0, r = 0; i <= m; i++)//求与其他字符串的其实于上面同理 
    {
        if (i <= r)
            p[i] = min(z[i - l + 1], r - i + 1);
        while (l + p[i] <= n && i + p[i] <= m && s[l + p[i]] == c[i + p[i]])
            p[i]++;
        if (i + p[i] - 1 > r)
            l = i, r = i + p[i] + 1;
        ans ^= i * (p[i] + 1);
    }
    cout << ans;

    return 0;
}
