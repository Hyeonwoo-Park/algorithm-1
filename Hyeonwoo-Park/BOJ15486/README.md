# BOJ 15486번 [퇴사 2](http://noj.am/15486)

## 🌈 풀이 후기
- 단순 dp였습니다.
## 👩‍🏫 문제 풀이
- 마지막 날짜부터 거꾸로 돌면서
    - 만약, 걸리는 기간이 남은 날짜보다 크다면
        - `dp[i + 1]` (어차피 해당 일정은 못고르기 때문에)
    - 그렇지 않다면
        - `max (money + dp[i + time], dp[i])`
- 코드를 간결하게 작성하기 위해, dp[n + 1]을 0으로 사용하였습니다.