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

## nim game
- 여러 더미 중 하나의 더미를  선택한다.
- 선택한 더미에서 한 대 이상의 구슬을 가져온다.

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

## grundy number
- 현재 상태의 grundy number가 0이면 다음 상태에는 0이 존재하지 않는다
- 현재 상태의 grundy number가 0이 아이면 다음 상태에는 0이 존재한다.

- 현재 상태의 grundy number가 0이면 후공을 통해 상대가 0을 깨트리도록 만든다
- 현재 상태의 grundy number가 0이 아니면 선공을 통해 0으로 만든다.