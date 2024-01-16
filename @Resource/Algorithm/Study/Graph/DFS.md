Deep First Search


```cpp
bool visit[] = { false };
vector<int> graph[];

void dfs(int x)
{
	visit[x] = true;
	for(int i = 0; i < graph[x].size(); i++)
	{
		int y = graph[x][i];
		if(!visit[y]) dfs(y);
	}
}

```