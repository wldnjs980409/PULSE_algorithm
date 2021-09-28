## 이분 탐색 (Binary Search)
### BOJ 2110번   <https://www.acmicpc.net/problem/2110>
<hr/>   

이런 문제를 처음 접해보고, 문제 이해가 잘 되지 않아서
다른 사람들 소스코드 많이 보면서 최대한 이해하려고 노력했습니다. 특히 나동빈님 코드를 많이 참고했습니다.


1. 문제   

> 최대한 많은 곳에서 와이파이를 사용하려고 하기 때문에, 한 집에는 공유기를 하나만 설치할 수 있고, 가장 인접한 두 공유기 사이의 거리를 가능한 크게 하여 설치하려고 한다.
> C개의 공유기를 N개의 집에 적당히 설치해서, 가장 인접한 두 공유기 사이의 거리를 최대로 하는 프로그램을 작성하시오.

> 입력
첫째 줄에 집의 개수 N (2 ≤ N ≤ 200,000)과 공유기의 개수 C (2 ≤ C ≤ N)이 하나 이상의 빈 칸을 사이에 두고 주어진다. 둘째 줄부터 N개의 줄에는 집의 좌표를 나타내는 xi (0 ≤ xi ≤ 1,000,000,000)가 한 줄에 하나씩 주어진다.

>출력
첫째 줄에 가장 인접한 두 공유기 사이의 최대 거리를 출력한다.
   


2. 문제를 틀린 이유   
   1.문제를 제대로 이해하지 못함   
   2. 이진 탐색 대상을 제대로 설정하지 못함  
    집(N)의 개수는 최대 200,000개라서 괜찮지만, 집의 좌표는 최대 1,000,000,000(10<sup>9</sup>)이라서 모든 경우를 다 탐색할 경우 시간 초과가 발생한다.   
    따라서 이진 탐색(O(log<sub>2</sub>n)을 사용해 탐색할 데이터 수를 줄이고, 최악의 경우에도 30번의 탐색만 하면 된다는 것까지는 이해했다.   
    하지만 '어떤 것, 어떤 값'을 이진 탐색의 대상으로 정해야 하는지 어려웠고 다양하게 시도해봤다.
  
   
   
3. 오답 해결 방법   
   1. 처음에는 당연히 집의 좌표 (X<sub>i</sub>)를 탐색 대상으로 생각했지만, 이 문제는 '공유기가 설치된 두 집의 거리 차'의 최솟값과 최댓값을 
   각각 이분탐색의 left, right값으로 정해야 하고, 이 둘의 평균을 mid 값으로 해야 한다.   
   ~~또한 mid 값을 활용해 어떤 조건을 만족하면 mid이하 또는 mid 이상의 것은 고려하지 않는다는 것을 
   생각해야 한다.~~   
   2. 또 처음에는 공유기 개수(C)에 딱 맞게 구해야 된다고 생각했는데 (공유기 개수 C개를 설치하면 탐색을 종료한다고 생각했음)   
      다른 문제의 풀이들을 보니 이 문제는 공유기 개수 C에 딱 맞게 구하는 게 초점이 아니라, "가장 인접한 두 공유기 사이의 최대 거리"를 구하는 것이므로   
      그냥 공유기 위치를 C개 이상을 찾았으면 그냥 "최대 거리"를 구하는데 초첨을 맞추면 된다.   
      


// vector로 하면 sort할 때 편리한데, 그러면 이분탐색할 때 처음과 끝 인덱스를
// 어떻게 넘겨줘야 할지 곤란하다고 판단해서 그냥 배열 사용
// 그리고 data가 200,000이라서 배열 사용해도 시간초과 없음...(?ㅎㅎ)