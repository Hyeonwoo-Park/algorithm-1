# BOJ 18222번 [투에-모스 문자열](https://www.acmicpc.net/problem/18222)

## 🌈 풀이 후기
* 풀이방법이 떠오르지 않아 어려웠습니다.
* 블로그에서 재귀를 활용하면 된다는 아이디어를 보고 풀었습니다.

## 👩‍🏫 문제 풀이
* `long[] arr` 에 각 단계별 문자열 길이를 저장합니다.
* x보다 작으면서 가장 큰 값을 가지는 단계의 길이(before)를 구합니다.
* 구하려는 값은 (1 - 이전 단계의 자리값) 이므로 이전 단계의 자리값을 재귀를 돌면서 얻어옵니다.
