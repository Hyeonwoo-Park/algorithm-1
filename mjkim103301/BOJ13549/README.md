# BOJ 13549번 [숨바꼭질3](https://www.acmicpc.net/problem/13549)

## 🌈 풀이 후기

## 👩‍🏫 문제 풀이

- 우선순위큐를 사용해서 num\*2, num+1, num-1 를 큐에 넣습니다.
- 큐에서 값을 꺼낼 때마다 M과 같은지 확인하고 visit check를 해줍니다.
- 큐에서 꺼낸 값이 M과 같으면 `answer = now.time; ` 후 반환합니다.
