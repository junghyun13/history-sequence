# history-sequence
# The first line gives the number of events, n, and the number of known events, k, in the first line. The next k lines are given the numbers of the two events of known context. This means that the event in the preceding number occurred before the event in the number after it. Of course, there is no case where the context of the event is contradictory. Next, we are given the number s of pairs of events for which we want to know the context of an event. The next s line is given the number of two different events, respectively. The number of events is a natural number greater than or equal to 1 and less than or equal to n. Answer the questions across s lines. On each line, print -1 if the preceding numbered event occurred first, 1 if the second numbered event occurred first, or 0 if you do not know what! 첫째 줄에 첫 줄에 사건의 개수 n과 알고 있는 사건의 전후 관계의 개수 k가 주어진다. 다음 k줄에는 전후 관계를 알고 있는 두 사건의 번호가 주어진다. 이는 앞에 있는 번호의 사건이 뒤에 있는 번호의 사건보다 먼저 일어났음을 의미한다. 물론 사건의 전후 관계가 모순인 경우는 없다. 다음에는 사건의 전후 관계를 알고 싶은 사건 쌍의 수 s가 주어진다. 다음 s줄에는 각각 서로 다른 두 사건의 번호가 주어진다. 사건의 번호는 1보다 크거나 같고, n보다 작거나 같은 자연수이다. s줄에 걸쳐 물음에 답한다. 각 줄에 만일 앞에 있는 번호의 사건이 먼저 일어났으면 -1, 뒤에 있는 번호의 사건이 먼저 일어났으면 1, 어떤지 모르면 0을 출력해라!
# 플로이드 워셜 알고리즘
플로이드 워셜 최단경로 알고리즘은 그래프에서 여러 노드가 있을 때, 모든 노드(All Source)에서 출발하여 다른 모든 노드(All Destination)로의 최단 경로를 구하는 알고리즘이다.
플로이드 알고리즘은 음수 사이클을 포함하면 사용할 수 없다는 특징을 갖는다. 다만 음수 사이클이 발생되지 않는한, 음수 간선은 포함할 수 있다.
음수 사이클이란 해당 경로를 무한 반복하면 음수 방향으로 계속 거리가 작아져서 수렴하지 않고 발산하는 경우를 말한다.
플로이드는 간단히 설명하면 I 로 부터 J 까지의 거리를 구하는데 K 라는 지점을 거쳐서 지나갈 때 최단경로가 나오는지 아닌지를 판별하며 Edge Relaxation을 통해 최단 거리를 업데이트 하는 알고리즘이다. Optimal substructure가 이곳에도 적용되는데, 최단 경로는 여러 개의 최단 경로로 이루어져 있다는 원리에 의해 음수 사이클이 발생할 수 없다는 전제가 설정된다. 이런 원리들에 의해 플로이드 알고리짐은 다이나믹 프로그래밍의 일종으로 분류한다.
구현해보면? --> # 점화식에 따라 플로이드 워셜 알고리즘을 수행
for k in range(1, v + 1):
    for i in range(1, v + 1):
        for j in range(1, v + 1):
            # k를 지나치는 경로와, k를 지나치지 않는 경로중 더 짧은 경로로 업데이트
            graph[i][j] = min(graph[i][j], graph[i][k] + graph[k][j])
# python
n,k=map(int,input().split())
arr=[[0]*(n+1) for _ in range(n+1)]
for _ in range(k):
    a,b=map(int,input().split())
    arr[a][b]=1
for k in range(1,n+1): # 플로이드 워셜 알고리즘 이용 
    for i in range(1,n+1):
        for j in range(1,n+1):
            if arr[i][k]+arr[k][j]==2:
                arr[i][j]=1
s=int(input())
for _ in range(s):
    x,y=map(int,input().split())
    if arr[x][y]==1: #앞의 번호의 사건이 먼저 일어남
        print(-1)
    elif arr[y][x]==1: #뒤에 있는 번호의 사건이 먼저 일어남
        print(1)
    else: #어떤지 모름
        print(0)
#input--> 5 5  1 2  1 3  2 3  3 4  2 4  3  1 5 #result--> 0  2 4 #result--> -1  3 1 #result--> 1
