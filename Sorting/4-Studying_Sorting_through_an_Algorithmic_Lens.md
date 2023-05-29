# Sorting

- - -

### 4. Studying Sorting through an Algorithmic Lens
#### 4.1. Lower Bound for Sorting
비교 기반 정렬의 시간 복잡도 하한 : $O(n\log{n})$

> a < b 의 결과는 오직 True/False 둘 중 하나이다.   
> a < b 결과를 바탕으로 c라는 추가적인 데이터를 비교하여 a,b,c의 배치 상태를 특정할 수 있는데,    
> 이런식으로 둘 씩 비교하는 과정을 Tree로 나타내면 어떤 Height(h)을 가지는 Tree의 Leaves는 총 $2^h$ 개가 된다.    
> n개의 데이터를 배치하는 경우의 수는 $n!$개이므로  
> **$2^h \ge n!$** 을 만족해야한다.
> 식을 정리하면
> $h \ge \log{n!} > \log{(n/e)^n} > O(n\log{n})$
> **따라서 어떤 정렬된 시퀸스를 얻기 위해서는 최소 $O(n\log{n})$만큼 비교를 수행해야한다.**

#### 4.2. Linear-Time Sorting Algorithm
**Bucket Sort**
데이터가 [0, N-1] 사이의 정수 범위에 있는 경우  
N개의 Array를 제작한 이후,  
데이터를 인덱스로 하여 N개짜리 Array에 그 데이터의 개수를 표기하고,
나중에 N개의 Array를 0부터 순서대로 읽으며 그 개수만큼 결과 Array에 데이터를 삽입하여 정렬  

Time Complexity : $O(n + N)$  
Space Complexity : $O(N)$   

$N \le O(n)\;or\;O(n\log{n})$ 일 때 효율적

https://github.com/CLiF-1593/SortingVisualizer/blob/master/SortingAlgorithm/Counting_Sort.py 

https://github.com/CLiF-1593/SortingVisualizer/blob/master/SortingAlgorithm/Counting_Sort.py

**Radix Sort**
사전순으로 정렬할 수 있는 데이터인 경우     
각 자릿값을 인덱스로 취할 수 있는 Array를 제작한 이후,  
각 자릿값을 인덱스로 하여 만든 Array에 그 데이터의 값을 순서대로 표기하고,  
나중에 만든 Array를 처음부터 끝까지 순서대로 읽으며,    
각 인덱스에 저장된 값들을 순서대로 Sorted Array에 삽입  
그 이후 다음 자릿수를 똑같은 방식으로 정렬 수행 
단, Radix Sort는 가장 낮은 자릿수부터 시작해야함. (LSD) 

Time Complexity : $O(nk)$  
Space Complexity : $O(k)$   

여기서 k는 각 자릿값을 인덱스로 취할 때 Array의 크기    

https://github.com/CLiF-1593/SortingVisualizer/blob/master/SortingAlgorithm/Counting_Sort.py

**Stable Sorting**
데이터 a와 b의 값이 서로 같을 때, a가 b보다 먼저 위치해있다면, 정렬 후에도 a는 반드시 b보다 앞에 위치해야함.    

* Stable Sort : Bubble, Insertion, Merge, Radix, Bucket
* Not Stable : Quick, Selection, Heap