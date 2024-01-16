Breath First Search
인접한 노드부터 탐색

queue 사용 

```cpp
bool visit[] = { false };
vector<int> graph[];

void bfs(int start) {
	queue<int> q;
	
	q.push(start);
	visit[start];
	
	while(!q.empty())
	{
		int x = q.front();
		q.pop();

		for(int i = 0; i< graph[x].size(); i++)
		{
			int y = graph[x][i];
			if(!visit[y])
			{
				q.push(y);
				visit[y] = true;
			}
		}
		
	}
}

int main()
{

	graph[a].push_back(b);
	graph[b].push_back(a);

}
```