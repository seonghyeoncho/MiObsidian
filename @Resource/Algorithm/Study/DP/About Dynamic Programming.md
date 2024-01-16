특정 범위의 값을 구하기 위해서 그것과 다른 범위까지의 값을 이용하여 효율적으로 값을 구하는 알고리즘

DP는 분할 정복과 비슷한 계산방식을 가진다.

점화식이 존재한다면 DP를 의심하자.

![external/s21.pos...](https://i.namu.wiki/i/fHsvaExGaqhsW5vNUY6Knp5VVllho2vIrYZQJgHmQBtss_F8DNYoxIqrJGFhrNF29LKkdgQQOzBdhLAk_MMJJSEDZE4SuJaAwfrruDHx2L7EHD067hzgyHlmcRdr_MHsN3J4cZup56HNl5SHFIo2Iw.png)

- f(a,b) = f(a-1,b) + f(a,b-1) (a,b >= 1 )