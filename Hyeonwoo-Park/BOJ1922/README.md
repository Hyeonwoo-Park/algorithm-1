# BOJ 1922번 [네트워크 연결](http://noj.am/1922)

## 🌈 풀이 후기
- 원래 MST 몰라서 이런 문제도 어려웠는데, 수월하게 풀어서 뿌듯하네요.
- 매번 프림 쓰는 편인데, 이번엔 크루스칼로 한번 해봤습니다.
## 👩‍🏫 문제 풀이
- 모든 컴퓨터가 최소 비용으로 연결 된 경우(= MST)
- PriorityQueue에 각 간선의 비용을 기준으로 계속 입력.
- 앞에서부터 하나씩 꺼내면서, 루트 노드가 같지 않은 두 노드라면 연결.
- 누적된 합을 출력.
