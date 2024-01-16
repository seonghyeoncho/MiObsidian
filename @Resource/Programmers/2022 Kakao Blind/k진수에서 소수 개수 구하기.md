- [[소수판별]]
- [[문자열 다루기]]
```cpp
#include <bits/stdc++.h>

using namespace std;

bool isPrime(long n) {
    if(n == 1) return false;
	for(int i = 2; i <= sqrt(n); i++)
		if(n%i == 0) return false;

	return true;
}
string toNdigit(int n, int k) {
    
    long result = 0;
    n*=k;
    for(long count = 1; n/=k; count*=10) result += (n%k)*count;

    return to_string(result);
}

int solution(int n, int k) {
    int answer = 0;
    
    string str = toNdigit(n, k);

    for(int i = 0; i < str.length(); i++) {
        string s;
        if(str[i] != '0') {
            for(; i < str.length() && str[i] != '0'; i++) {
                s+=str[i];
            }
            cout << s << '\n';
            if(isPrime(stol(s))) answer++;
        }
    }
    
    return answer;
}
```