# BOJ 2504번 [괄호의 값](https://www.acmicpc.net/problem/2504)

## 🌈 풀이 후기

이전 코딩테스트에서 괄호의 스택을 가지고 푸는 문제가 나왔어서 고생했던 경험이 있습니다. 끝나고 이 문제를 한번 풀어봤었는데 오랜만에 보니 여전히 스택 문제는 어려운거 같습니다..

이전에 풀었을 때는 규칙을 따라가면서 길고 복잡하게 풀어봤어서 이번에는 괄호를 가지고 규칙을 찾아보려고 열심히 그려봤습니다. 

 괄호의 중첩에 따라서 현재 value를 잘 업데이트 하여 활용하면 깔끔하게 풀 수 있는 문제였습니다.  

## 👩‍🏫 문제 풀이

**핵심 원리**

 0. 초기값으로 curValue(현재 값)를 1로, answer는 0으로 설정합니다. 

1. '(' 혹은 '[' 가 오면 stack을 두개로 나눠서 소괄호는 stackS에 대괄호는 stackB에 저장하고 curValue를 각각 *2, *3을 해줍니다.
2. ')' 나 ']' 이 오면 각 괄호에 맞춰서 비어있는지 확인합니다.
3. 스택이 비어있다면 불가능한 경우이기에 반복문을 탈출합니다.

3-2. 스택이 비어있지 않다면 현재 검사하는 위치의 바로 전이 무엇인지 확인합니다.

4. 만약 바로 닫혀있다면 ) 의 경우 () , ] 의 경우 [ ] 의 경우라면 curValue를 answer에 더해줍니다. 

5. 그리고 각 괄호의 stack에서 pop을 해준뒤 괄호에 맞게 curValue에 맞게 /2 , /3을 해줍니다. 

**예시**

ex) (()[[]])

```java
(  // answer => 0 ,curValue *2 =>  2
(( // answer => 0 ,curValue *2 => 4
(() // answer => 4 ,curValue => 2
(()[ // answer =>4 ,curValue => 6
(()[[ // answer =>4 ,curValue => 18
(()[[] // answer =>22 , curValue => 6
(()[[]] // answer => 22,curValue =>2
(()[[]]) // answer =>22 ,curValue=>1
```

()안에 있다면 *2 , []안에 있다면 *3을 이용했고 올바른 괄호열이 붙어있다면 더해주는 규칙을 이용했습니다. 

(()[[]]) 이란 결국 2*2 + 2*3*3 

**핵심 코드**

```java
for(int i=0;i<str.length();i++) {
			char c=str.charAt(i);
			if(c=='(' || c=='[') {
				if(c=='(') {
					stackS.push(c);
					curValue *=2;
				} else { // c=='[' 
					stackB.push(c);
					curValue *=3;
				}
			}else { // ch => ) || ]
				if(c==')') {
					if(stackS.isEmpty()) {
						isValid=false;
						break;
					}
					if(str.charAt(i-1) == '(')
						answer+=curValue;
					stackS.pop();
					curValue/=2;
				} else { // ]
					if(stackB.isEmpty()) {
						isValid=false;
						break;
					}
					if(str.charAt(i-1)=='[')
						answer+=curValue;
					stackB.pop();
					curValue/=3;
				}
			}
			
		}
```
