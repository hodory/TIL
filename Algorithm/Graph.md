# 그래프

## BFS(Breadth First Search, 너비 우선 탐색)

- 가장 인접한 노드들을 먼저 방문, 먼 정점은 나중에(인접한 지점을 모두 방문 하였을 때) 방문.
- 맹목적 탐색법
- FIFO(First In First Out) 타입의 Queue로 구현할 수 있음

## DFS(Depth First Search, 깊이 우선 탐색)

- 한 방향으로 탐색하고, 막혔을 경우 루트 노드로 돌아가서 다음 방향을 지정하고 한방향으로 계속하여 탐색을 반복
- 맹목적 탐색법
- 재귀호출을 이용한 LIFO(Last In First Out) 타입의 Stack로 구현할 수 있음
  - Stack Overflow에 유의해야함.
