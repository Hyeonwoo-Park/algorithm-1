# BOJ 16918번 [봄버맨](https://www.acmicpc.net/problem/16918)

## 🌈 풀이 후기
* 초를 계산할 때 헷갈렸습니다.

## 👩‍🏫 문제 풀이
* map에 문자와 폭탄이 터지거나 폭탄을 터트린 초를 Node 클래스로 저장했습니다.

### 주요 코드 
``` java
 //지금 터트필 폭탄보다 나중에 설치된 폭탄 제거
 if (map[yy][xx].ch == 'O' && map[yy][xx].bombTime > time) {
    map[yy][xx] = new Node('.', time); // 현재 시간으로 변경
 }
 ```
 * A폭탄을 제거할 때, 4방향을 순회하면서 같은 시간에 설치된 B,C,D 폭탄을 모두 제거하면, 다음 차례인 B 폭탄을 제거했을 때 터져야할 4방향은 접근할 수 없습니다.
 * 그래서 현재 시간보다 나중에 설치된 폭탄을 제거했습니다.
 <br><br>


 ```java
 //변경된 시간이 현재 시간보다 더 작을 경우에 폭탄 설치
 else if (map[y][x].ch == '.' && map[y][x].bombTime < time) {

 //폭탄이 터질 시간 (time+3) 으로 저장
    map[y][x] = new Node('O', time + 3);
 }
 ```
 * 모든 시간에 폭탄을 설치하면, 같은 시간대에 터진 폭탄 자리에 새로 폭탄을 설치할 수 있습니다.
 * 그래서 현재시간보다 더 작은 bombTime 일 때 폭탄을 설치했습니다.