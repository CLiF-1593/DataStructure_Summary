# Sorting

- - -

### 1. Why Study Sorting Algorithms?
**Sorting** : 데이터를 규칙에 따라 나열하는 것  
<,> Operator 이용   
\+ Irreflexive property : !<, !>    
\+ Transitive property : k1 < k2 and k2 < k3 => k1 < k3 

정렬이 중요한 이유  
**Binary Search (+ 다른 Advanced Algorithm)를 할 수 있음**  

Python : arr.sort(), arr = sorted(arr)

**책에 등장하는 정렬 알고리즘**
1. Bubble Sort
2. Insertion Sort
3. Selection Sort
4. Quick Sort
5. Merge Sort
6. Bucket Sort (Counting Sort)
7. Radix Sort
8. Heap Sort
    
#### 1.1. Bubble Sort
양 옆 데이터를 비교하여 a[i] > a[i+1]일 경우 swap   
n개의 데이터를 검사하면 가장 큰 값이 마지막에 위치  
이러한 과정을 최대 n번 수행 
이름이 버블인 이유는 시각화 결과가 버블이 올라가는 것 처럼 보여서 그럼    

Time Complexity : $O(n^2)$  
Space Complexity : $O(1)$   

https://github.com/CLiF-1593/SortingVisualizer/blob/master/SortingAlgorithm/Bogo_Sort.py

#### 1.2. Insertion Sort
어떤 데이터 앞의 모든 데이터는 정렬되어있다고 가정  
어떤 데이터와 그 앞의 데이터를 비교하여 적절한 위치에 삽입  
데이터를 삽입하므로 삽입 정렬    

Time Complexity : $O(n^2)$  
Space Complexity : $O(1)$   

https://github.com/CLiF-1593/SortingVisualizer/blob/master/SortingAlgorithm/Insertion_Sort.py

#### 1.3. Selection Sort
어떤 데이터 기준 그 뒤에있는 데이터 중 최소값을 골라서  
어떤 데이터와 swap  
최종적으로 작은 값부터 순차적으로 쌓임  
최소값을 선택하므로 선택 정렬   

Time Complexity : $O(n^2)$  
Space Complexity : $O(1)$   

https://github.com/CLiF-1593/SortingVisualizer/blob/master/SortingAlgorithm/Selection_Sort.py

#### 1.4. Heap Sort
Heap 자료 구조를 활용한 정렬    
Heap의 root는 어떤 데이터의 최댓값 혹은 최솟값  
root에서 데이터를 빼서 차례대로 채워넣으면서 정렬   

Time Complexity : $O(n\log{n})$ 
ㄴ Heapify : $O(\log{n})$   
Space Complexity : $O(1)$   

https://github.com/CLiF-1593/SortingVisualizer/blob/master/SortingAlgorithm/Heap_Sort.py