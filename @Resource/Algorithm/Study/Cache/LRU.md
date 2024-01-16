Least Recently Used

가장 오랫동안 참조되지 않은 페이지를 교체

프로세스가 주기억장치에 접근할 때마다 참조된 페이지에 대한 시간을 기록해야함. 큰 오버헤드가 발생


```cpp
class LRU
{
	list<int> LRUList;
	unordered_map<int, list<int>::iterator> LRUMap;
	int LRUMaxSize;
public:
	LRU(int);
	void refer(int);
	void display();
}

LRU::LRU(int n)
{
	LRUMaxSize = n;
}

void LRU::refer(int x)
{
	if(LRUMap.find(x) == LRUMap.end())
	{
		if(LRUList.size() == LRUMaxSize())
		{
			int last = LRUList.back();
			LRUList.pop_back();
			LRUMap.erase(last);
		}
	} else LRUList.erase(LRUMap[x]);

	LRUList.push_front(x);
	LRUMap[x] = LRUList.begin();
}

```