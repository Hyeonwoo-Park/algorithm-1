# BOJ 2003번 [수들의 합 2](https://www.acmicpc.net/problem/2003)

## 🌈 풀이 후기
- 문제를 처음 봤을 때는, 단순 2중 포문으로 풀면 시간초과가 날 것 같다고 생각 했습니다.
    - 지난주에 너무 크게 데여서, 아직까지 시간초과가 무섭습니다 ㅠ
- 의미상 cnt++와 break를 분리하고 싶어,
    - sum == M, sum >= M 조건을 사용했습니다.
## 👩‍🏫 문제 풀이
- nums 배열에 입력을 받은 뒤,
- i를 0 ~ N 까지
    - j를 i ~ N 까지 반복하며
    - sum에 nums[j] 값을 누적하며,
        - sum이 M과 같으면 cnt++
        - sum이 M이상이면 break;