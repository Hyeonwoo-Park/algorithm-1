# BOJ 14719번 [빗물](https://www.acmicpc.net/problem/14719)

## 🌈 풀이 후기
map 배열을 int로 생성했다가 boolean으로 변경했습니다. 메모리와 의미상 boolean이 더 어울리는 것 같습니다.   
int: 4바이트 , boolean: 1바이트

</br></br>

## 👩‍🏫 문제 풀이
* boolean [][] map 배열에 벽인 부분을 true로 만들었습니다.

* 0행부터 H 행까지 Wx열을 돌면서 3가지의 경우로 나눴습니다.
    1. map 이 벽이고 wallStart == false일때  -> 벽이 시작함을 체크합니다.
    2. map 이 빈공간이고 wallStart == true일때 -> 물을 채울 수 있으므로 빈공간의 개수를 셉니다.
    3. map이 벽이고 wallStart == true 일 때 -> 벽이 끝났으므로 빈공간의 개수를 water 변수에 더합니다.


### 예시

|map[y][x] |true|false|false|true|false|  
|----|----|-----|----|----|----|
|wallStart|true|true|true|true|true|
|tempWater|0|1|2|0|1|
|water|0|0|0|2|2|2|