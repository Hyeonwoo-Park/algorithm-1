# BOJ 2003번 [수들의 합2](https://www.acmicpc.net/problem/2003)

## 🌈 풀이 후기
* 누적합으로 풀린 간단한 문제였습니다.
## 👩‍🏫 문제 풀이
* `accum` 배열에 누적합을 저장합니다.
* `find(int i)` 메서드에서 i번째 값이 M 이면 바로 `return true;` 합니다.
* 아니라면 `accum[i]- accum[j]` 값이 M이라면 `return true;` M 보다 작다면 바로 `return false;`를 합니다.
* 배열을 다 돌아도 M 값을 못찾았다면 `return false; `합니다.


</br></br>

### 투포인터
* 준영님 추천으로 투포인터로도 풀어봤습니다.
* 경계값과 변수값 생각하는 부분은 어려웠지만, 코드가 간결해져서 더 좋은 것 같습니다.

#### 변수
* int N, M -> N: 수의 개수, M: 수의 합
* int sum -> 구간합
* int left -> 다음에 뺄 값
* int right -> 다음에 더할 값
#### 풀이방법
* `sum < M && right< N` 일 때 sum 에 arr[right] 을 더합니다.
* `sum == M` 일 때 
    * 경우의수 1 증가해줍니다.
    * sum에서 arr[left] 을 뺍니다.
* `right == N` 일 때 while 문을 종료합니다.



