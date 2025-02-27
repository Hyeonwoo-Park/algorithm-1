# BOJ 2504번 [괄호의 값](https://www.acmicpc.net/problem/2504)

## 🌈 풀이 후기
- 길이가 30 이하이므로 Scanner를 사용 하였습니다.
- 모든 경우를 깔끔하게 처리하고 싶었는데, 최상단 [], ()를 깔끔하게 처리하지 못했습니다.
## 👩‍🏫 문제 풀이
### 사용한 변수
1. `bracketStack` : 괄호를 저장할 스택
2. `sumStack`     : 각 층별 합을 저장할 스택

### 풀이 방법
1. 입력을 처음부터 끝까지 확인.
2. 여는 괄호일 경우 `braketStack`에 괄호 삽입, `sumStack`에 0 삽입.
3. 닫는 괄호인 경우,
    3-1. `braketStack`의 top과 맞는 괄호이면(올바른 괄호이면), `sumStack`의 top에 괄호의 값만큼 곱하여 sumStack의 다음 top에 더함. 
    3-2. 다른 괄호이면, 0을 출력하고 실행을 종료.
4. 입력의 길이만큼 모두 돌았는데도 `braketStack`이 비워져있지 않은 경우(올바르지 않은 경우) 0을 출력.
5. 그렇지 않다면 `sumStack`에 누적된 값을 출력.
