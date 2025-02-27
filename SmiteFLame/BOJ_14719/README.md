# BOJ 14719번 빗물

## 🌈 풀이 후기
왼쪽에서 오른쪽, 오른쪽에서 왼쪽으로 가는 두 번 검사하는 방법으로 사용했습니다. <br>
좌우를 검사해서 바로 넣으려다가 좌우 최대 높이가 같은 경우는 더해지지 않은 경우가 있었습니다. <br>
그 부분을 예외처리하기 보다 새로운 배열을 만들어서 물이 차오르는 높이를 따로 구했습니다.


## 👩‍🏫 문제 풀이
<br>

### 변수
- H, W(int): 세로 길이와 가로 길이
- data(int[]): 블록의 크기
- flood(int[]): 쌓이는 물의 양

### 원리
1. 왼쪽으로 오른쪽으로 가면 최대값을 최산화 하면서 쌓이는 물의 양을 먼저 검사합니다
2. 오른족에서 왼쪽으로 가면서 똑같이 검사합니다.
3. 둘 중에서 작은 값이 차오르는 범위가 된다.
작은 값이 들이가는 이유
- 좌 우 중에서 낮은 블록을 기준으로 물이 쌓이게 된다.

```
EX) 3 1 2 3 4 1 1 2

        |
|     | |
|   | | |     |
| | | | | | | |

1. left -> right를 할때
max 변화    3 3 3 3 4 4 4 4
flood       0 2 1 0 0 3 3 2

2. left <- right를 할때
max 변화    4 4 4 4 4 2 2 2
flood       1 3 2 1 0 1 1 0

3. flood의 최소값
flood       0 2 1 0 0 1 1 0

```