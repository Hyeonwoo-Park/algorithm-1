# BOJ 12847번 [꿀 아르바이트](http://noj.am/12847)

## 🌈 풀이 후기
- 간단한 누적합 문제.
- 풀어본적 없는 것 같아서 한번 내봤습니다 :)
## 👩‍🏫 문제 풀이
- 매 Ti 입력시 마다
    - `sum[i]`에 `sum[i - 1]` 값에 Ti를 더한값을 입력합니다.
- 이후 M에서 N까지
    - `sum[i] - sum[i - M]`을 구해 최대값과 비교합니다.
