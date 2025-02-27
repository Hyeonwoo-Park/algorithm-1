# BOJ 2302번 극장좌석

## 🌈 풀이 후기
각각의 벽을 만들고 피보나치 수열을 활용하는 문제였습니다. <br>

## 👩‍🏫 문제 풀이
<br>

### 변수
- N, M(int): 좌석의 수 고정된 좌석의 수
- fixed(int[]): 고정된 좌석의 위치
- fibo(int[]): 피보나치 수열

### 원리
1. 고정된 좌석의 위치와 처음, 마지막 위치를 데이터를 추가합니다.
2. 고정된 좌석들의 차이값들 이용하여 데이터를 구합니다. <br>
2-1. 차이값 중에서 가장 큰 값을 골라서 피보나치 수열의 최대값을 구합니다.
3. 차이값들에 해당되는 피보나치 값들을 곱하여 데이터를 구합니다.

### 테스트 케이스
9 <br>
2 <br>
4 <br>
7 <br>
 <br>
fixed[] -> 0, 4, 7, 10 <br>
 <br>
차이값 -> 4, 3, 3 <br>
 <br>
fibo <- 0, 1, 2, 3 //(여기 까지 구함) 5, 8.. <br>
 <br>
3 * 2 * 2 = 12 값 출력 <br>