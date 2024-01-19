게임 이론은 다음과 같은 상황에서 적용될 수 있다 .

- 2명에서 게임을 진행한다.
- 2명 모두 최선을 다해서 게임을 진행한다. 
- 2명 모두 서로의 정보에 대해서 잘 알고 있다. 

이런 경우 다음과 같은 논리가 통한다.

게임의 상태를 x라고 하면, 
현재 플레이어는 dp[x] = 0이면 이기고,
dp[x] = 1이면 진다.

즉, 현재 플레이어가 어떤 행동을 한 후의 게임의 상태가 y라고 하면, 
dp[y] = 0이면 지고, 
dp[y]=1이면 이긴다. 


 [[DP]]
```cpp
#include<bits/stdc++.h>

using namespace std;
int dp[1001] = {0};

int main() {
    ios::sync_with_stdio(0);
    cin.tie(0), cout.tie(0);
    
    int n;
    cin>>n;
    
    dp[1] = 0;
    dp[2] = 1;
    dp[3] = 0;
    dp[4] = 0;
    
    for(int i=5;i<=n;i++) {
        if(!dp[i-1] && !dp[i-3] && !dp[i-4]) dp[i] = 1;
            else dp[i] = 0;
    }
    
    cout<<(!dp[n]?"SK":"CY");
        
    return 0;
}

``` 
