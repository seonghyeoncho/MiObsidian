- [[백트레킹]]
```cpp
using namespace std;

int n, m;

int arr[9];
bool visited[9] = { false };

void dfs(int c) {
    
    if(c == m)
    {
        for(int i = 0; i < m; i++)
            cout << arr[i] << ' ';
        cout << '\n';
        
        return;
    }
    
    for(int i = 1; i < n + 1; i++)
    {
        if(!visited[i])
        {
            visited[i] = true;
            arr[c] = i;
            dfs(c + 1);
            visited[i] = false;
        }
    }
}

int main()
{
    cin >> n >> m;
    dfs(0);

    return 0;
}
```


dfs를 응용하는 것 은 동일. 하지만 백트레킹에서 중요한 부분은  재귀문을 탈출하는 방법과 방문을 핸들링한느 것