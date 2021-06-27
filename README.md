# Hello-Coding
- 알고리즘 기초 정리


## 목차
1. [빅오 표기법](#1-빅오-표기법--자료구조)
2. [이진 탐색](#2-이진-탐색)
3. [정렬](#3-정렬)
    - 선택 정렬
    - 퀵 정렬
4. [해시 테이블](#4-해시-테이블)
5. [DFS, BFS](#5-DFS-BFS)
6. [Dijkstra's Algorithm](#6-Dijkstra's-Algorithm)
7. [Greedy Algorithm](#7-Greedy-Algorithm)
8. [Dinamic Programming](#8-Dinamic-Programming)

## 1. 빅오 표기법 & 자료구조
- 알고리즘의 속도를 나타내는 방법
- 최악의 경우에 대해 표기. ex) 전화번호부에서 사람 단순 탐색. 처음부터 찾는 경우도 있지만, **O(n)으로 표기**
- 상수 값은 생략   O(an+b) -> O(n)

자료구조
- array(배열)
    - 값들이 연결되어 메모리에 저장되는 형태.
    - 배열 저장 위치에서 바로 이웃한 부분에 값이 채워져 있는 경우, 배열 전체가 연결되어 들어 갈 수 있는 새로운 공간을 찾아 이동
    - 장점: 빠른 조회 속도. 시간 복잡도 O(1)
    - 단점: 작업 시간이 느려짐. 만약 이러한 부분을 고려해서 배열에 미리 많은 공간을 할당하는 경우, 쓸데없는 메모리 낭비가 될 수 있음.

- Linked List(연결 리스트)
    - 각각의 값들이 다음 원소에 대한 주소값을 가지고 있음.
    - 장점: 새로운 값 추가시 작업 시간이 빠르며, 공간을 효율적으로 쓸 수 있음.
    - 단점: 느린 조회 속도. 차례대로 조회를 해야하기 때문에 시간 복잡도 O(n)

        ||배열|연결 리스트|
        |:---|:---|:---|
       |읽기|O(1)|O(n)|
       |삽입|O(n)|O(1)|

- Tree
    + 거꾸로 가는 간선이 없는 그래프
## 2. 이진 탐색
- 정렬 되어 있는 상태에 적용 해야 함
- 중간 값을 기준으로 크다/작다 판단
- 시간 복잡도 : O(log_2(n))

## 3. 정렬
- 선택 정렬
    - 단순히 일일히 비교 후 높은 값들은 차례로 찾아서 정렬하는 방법. 
    - 시간 복잡도 : O(n^2)
- 퀵 정렬
    - 분할 정복, 재귀 방법론 이용. ex)유클리드 호제법(https://s-night.tistory.com/91)
    - 분할 정복이란? 문제를 작게 쪼개어 답을 찾아나가는 bottom-up 방법론.
    - pivot(기준)값을 잡고 이 값보다 작은 것, 큰 것을 좌우로 위치 시킴
    - 좌, 우측 값들에서 다시 기준 값을 잡고 이전과 동일하게 작은, 큰 값들을 위치 시킴
    - -> 위 과정을 반복하면 선택 정렬보다 빠르게 정렬 가능
    - 시간 복잡도 : 평균 O(nlogn) / 최악의 상황 O(n^2)

## 4. 해시 테이블
- 해시 함수를 사용하여 값이 저장된 위치를 정확하게 알려줌
- ex) dictionary
- 해시 테이블을 캐시로 사용하여 성능 향상 가능.(서버 처리 작업 감소)
- 충돌 방지를 위해 linked list 사용하기도 함.
- 하지만, linked list를 너무 길어지면 속도가 느려짐. 따라서, 충돌이 많이 발생하지 않도록 좋은 해시 함수를 사용 해야 함
- 사용률이 커지면 리사이징해야됨 -> 시간 비용이 비쌈
- 시간 복잡도 : O(1). 탐색, 삽입, 삭제

## 5. DFS, BFS
- 그래프 탐색 : 하나의 정점으로부터 시작해 차례대로 모든 정점을 한 번씩 방문하는 것
    + 최단 거리 문제 해결 가능
    + 체커 게임에서 가장 적은 수로 승리할 수 있는 인공지능(BFS)
    + 문제 풀이 프로세스
        1. 문제를 그래프로 모형화 한다.
        2. 탐색 기법을 이용해서 문제를 푼다.
- DFS(Depth-First Search) : 깊이 우선 탐색
    + 방향 하나를 잡고 끝까지 탐색을 반복해나가는 방법
    + Stack 사용
- BFS(Breadth-First Search) : 너비 우선 탐색
    + 주변을 먼저 탐색해 나가는 방법
    + 시간 복잡도 : O(V+E) *vertex(정점), edge(간선)
    + Queue 사용

## 6. Dijkstra's Algorithm
- weighted graph에서 최단 경로를 구하는 알고리즘.
- DAG(Directed Acyclic Graph) 또는 cycle을 가진 경우 가중치가 양수일 때만 적용 가능
- 수행 과정
    + 출발점을 기준으로 정점까지의 가격을 계산(이웃하지 않은 정점의 경우 거리 inf로 지정)
    + 가장 가격이 싼 정점으로 이동 후 정점까지의 가격을 계산. 앞서 계산한 가격보다 싼 경우 새 값으로 업데이트.
    + 그래프 상의 모든 정점에 대해 위 과정을 반복
    + 최종 경로 계산

## 7. Greedy Algorithm
- 각 단계에서의 최적값을 찾아나가는 방법론.(전체로 보았을 땐, local minimum일 확률이 높음)
- 장점: **매우 빠르게** 근사 최적해를 찾을 수 있음.
- 경우의 수가 무수히 많은 집합 커버링문제, np-complete 문제 해결에 breakthrogh로서 사용됨

## 8. Dinamic Programming
