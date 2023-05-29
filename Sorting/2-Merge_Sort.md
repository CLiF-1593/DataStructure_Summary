# Sorting

- - -

### 2. Merge-Sort
#### 2.1. Divide-and-Conquer
분할 정복   
어떤 문제를 해결하기 위해 문제를 작게 쪼개어 해결하는 것    
1. Divide : 문제 쪼개기 
2. Conquer : 조그마한 문제 해결하기 (쉬움)  
3. Combine : 두 개의 문제 해결 결과를 합치기    

**Merge Sort Mechanism**
1. Divide : 데이터를 반 씩 쪼갬 (1개가 될 때 까지)  
2. Conquer : 데이터가 1개씩 쪼개진 상태에서는 모든 데이터가 정렬된 것과 마찬가지임. 
3. Combine : 정렬된 두 리스트를 병합 (정3 내용 참고)    

#### 2.2. Running Time
반 씩 쪼개지므로 Merge-Sort Tree의 Height은 **$\log{n}$**  
각 단계에서 합치는 과정에서 총 **$n$** 번의 작업 필요   

**Time Complexity : $O(n\log{n})$, $\Theta(n\log{n})$, $\Omega(n\log{n})$**  

두 list를 합치는 과정에서 두 list의 크기의 합과 같은 길이의 list가 필요함.  
추가 공간을 쓰지 않으려면 데이터를 inserting 해야하므로 시간복잡도 증가 

**Space Complexity : $O(n)$**   

#### 2.3 Source Code
https://github.com/CLiF-1593/SortingVisualizer/blob/master/SortingAlgorithm/Merge_Sort.py