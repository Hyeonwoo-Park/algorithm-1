# BOJ 0000번 [문제이름]()

## 🌈 풀이 후기
* 배열을 복사할 때는 __Arrays.copyOf()__ 를 사용해야 한다는 것을 다시 상기했습니다.
* 입력에 주어진 배열의 크기보다 y를 1 더 큰 배열로 생각해야 한다는 점이 새로웠습니다.  4방이나 8방 탐색이 아니라 왼쪽부터 오른쪽으로 탐색했는데 이 점도 새로웠습니다.
* 풀이를 쓰다 보니 메서드를 더 작게 쪼개면 좋을 것 같다고 느꼈습니다.

## 👩‍🏫 문제 풀이
### 변수 
    static int N,M,D;   -> map의 세로줄, 가로줄, 궁수의 공격거리 제한
    static int[][]map; -> 초기 배열의 값을 저장하는 배열
    static int[][]copy; -> 게임하면서 map의 상태를 변경할 때 사용하는 copy배열
    static int archer=3; -> 궁수 수
    static int max; -> 제거할 수 있는 적의 최대 수



### 메서드

* 조합의 방법으로 map의 N번째 줄에 궁수를 배치합니다.
* ex) N이 5라고 가정했을 때, 11100, 11010, 11001, 10110 ... 순으로 저장됩니다.
* 궁수는 3명이므로 재귀의 깊이 now== archer(3) 이 됐을 때 게임을 시작합니다.
* 게임 후 kill 변수에 죽인 적의 수를 저장합니다.
* 그 후 max 값을 구해서 리턴합니다.  -> 재귀를 반복합니다.

```java
static void defense(int now, int index){
        if(now==archer){
            int kill=game();

            max=Math.max(max,kill);
            return;
        }

        for(int i=index; i<M;i++){
            map[N][i]=1;
            defense(now+1,i+1);
            map[N][i]=0;
        }
    }

```
 1. 게임하면서 배열의 값을 변경하므로 copy배열에 map배열의 값을 복사합니다.
 2. 적이 N 번 앞으로 전진할 수 있으므로 for문도 N번 반복합니다.
3. 궁수별로 죽일 수 있는 적을 저장할 배열을 초기화합니다. -> -1 로 초기화해서 적이 있는 요소와 없는 요소를 구분합니다.
4. copy배열의 N번째 행을 순회하면서 copy[N][j]==1 인 부분에 궁수가 있으므로 변수들을 초기화합니다.
    * minDistance: 궁수와 적의 최소거리 -> D 거리까지 도달할 수 있으므로 D+1값으로 초기화
    * enomyY, enomyX : 적의 좌표 -> -1 인 경우 적이 없는 것으로 간주
5. 배열을 순회하면서 유효거리에 적이 있으면 minDistance값을 갱신합니다.
6. 적의 좌표가 0 이상일 때만 배열에 저장합니다.
7. 적에 해당하는 좌표를 0으로 만듭니다.
8. 궁수 3명이 적을 1턴씩 죽일때마다 적이 밑으로 전진해야 하므로 moveEnomy() 메서드를 호출합니다.

```java

static int game(){
        int kill=0;
        int [][]enomy=new int[M][2];
        for(int i=0;i<N+1;i++){ //1
            copy[i]=Arrays.copyOf(map[i], M);
        }
        for(int cnt=0;cnt<N;cnt++){//2

            for(int k=0;k<M;k++){ //3
                Arrays.fill(enomy[k], -1);
            }

            for(int j=0;j<M;j++){

                if(copy[N][j]==0) continue;
                //4. 궁수가 있으면
                int minDistance=D+1;
                int enomyY=-1;
                int enomyX=-1;
                for(int x=0;x<M;x++){ //5
                    for(int y=N-1;y>=N-D;y--){
                        if(y<0)continue;
                        if(copy[y][x]==0) continue;
                        //적이 있으면
                        int distance=Math.abs(y-N)+Math.abs(x-j);
                        if(distance<=D && distance<minDistance){
                            enomyY=y;
                            enomyX=x;
                            minDistance=distance;
                          
                        }
                    }
                }

                if(enomyY>=0 && enomyX>=0){ //6
                    enomy[j][0]=enomyY;
                    enomy[j][1]=enomyX;

                }
            }

            for(int i=0;i<M;i++){ //7
                int y=enomy[i][0];
                int x=enomy[i][1];
                if(y>=0 && x>=0 && copy[y][x]==1){
                    kill++;
                    copy[y][x]=0;
                }
            }

            moveEnomy(); //8
        }


        return kill;
    }

```

* 게임을 1턴 했으면 적을 밑으로 1칸 전진해야하므로  copy[y] 줄에 copy[y-1] 줄을 복사합니다.  여기서 Arrays.copyOf 가 아닌 copy[y]= copy[y-1] 를 사용했더니 주소가 복사돼서 힘들었습니다. 😂

```java
 static void moveEnomy(){
        for(int y=N-1;y>0;y--){
            copy[y]=Arrays.copyOf(copy[y-1], M);
        }
        Arrays.fill(copy[0],0);
    }

```