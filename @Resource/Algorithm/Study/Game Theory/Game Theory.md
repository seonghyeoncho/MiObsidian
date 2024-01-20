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

grundy number => *해당 집합에 존재하지 않는 가장 작은 수*


## Minimax
- 나를 기준으로 보고 상대의 점수가 min이 되도록 선택하도록 한다.
- 두 경기자를 MAX MIN으로 부른다.
- 항상 MAX가 먼저 수를 둔다
- 순차적 게임
- zero-sum game
- MIN은 숫자가 작을 수록 이기고, MAX는 숫자가 클 수록 이길 확률이 높다

```cpp
using namespace std;

int c[1001] ={0};
int dp[1001][1001][2];

int reculsive_game(int start, int end, int turn) {
    int &ret = dp[start][end][turn];
    if(ret != -1) return ret;
    
    if(start >= end) {
        if(!turn) return ret = c[start];
        return ret = 0;
    }
    
    if(!turn) {
        return ret = max(reculsive_game(start + 1, end, 1) + c[start], reculsive_game(start, end-1, 1) + c[end]);
    } else {
        return ret = min(reculsive_game(start + 1, end, 0), reculsive_game(start, end-1, 0));
    }
    
}

int main() {
    ios::sync_with_stdio(0);
    cin.tie(0), cout.tie(0);
    
    int t;
    cin>>t;
    
    while(t--) {
        memset(dp, -1, sizeof(dp));
        
        int n;
        cin>>n;
        
        for(int i = 0; i< n; i++) {
            cin>> c[i];
        }
        
        cout<<reculsive_game(0, n-1, 0)<<"\n";
    }
    
    return 0;
}
```