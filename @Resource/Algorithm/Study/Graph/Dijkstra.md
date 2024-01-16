- 최단경로
- 매번 최단 경로의 정점을 선택 -> 그리디한 방법으로 최단이 아닐 수도 있음
- 

```cpp
//그래프
vector<pair<int, int>> g[];
//가중치 테이블
int d[];

//정점, 간선, 시작 정점 번호
int v, e, s;

void dijkstra()
{
	priority_queue< pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>> > pq;
	
	//가중치 , 시작 정범 번호
	pq.push({0, s}); 
	d[s] = 0;
	
	while(!pq.empty())
	{
		int current = pq.top().second;
        int dist = pq.top().first;
        
        pq.pop();
	    
	    //다음 방문할 노드의 가중치보다 현재 가중치가 작다면 갈 이유가 없음
        if(dist > d[current]) continue;
        
        for(int i = 0; i < g[current].size(); i++)
        {
            int n = g[current][i].first;
            int nDist = g[current][i].second;

			//
            if(nDist + dist < d[n])
            {
                d[n] = nDist + dist;
                pq.push({d[n], n});
            }
        }
		
	}

}

int main()
{
    ios::sync_with_stdio(false);
    cin.tie(NULL);
    cout.tie(NULL);
    
    cin >> v >> e >> s;

    for(int i = 0; i < e; i++)
    {
        int x, y, w;
        
        cin >> x >> y >> w;
        //방향이 존재함
        g[x].push_back({y, w});
    }
    
    for(int i = 1; i < v + 1; i++) d[i] = INF;
    
    dijkstra();
    
    for(int i = 1; i < v + 1; i++) 
    {
        if(d[i] == INF) cout << "INF";
        else cout << d[i];
        
        cout << '\n';
    }
    
    return 0;
}
```

