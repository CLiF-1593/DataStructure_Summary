# Sorting

- - -

### 3. Quick-Sort
#### 3.1. High-Level Description of Quick-Sort
분할 정복을 사용한 알고리즘 
단, 큰 작업을 수행하고 (대략적으로) 작은 작업 (세부 정렬)을 나중에 수행 

**Quick Sort Mechanism**
1. Divide : list 크기가 최소 2일 경우, 이 중 하나를 pivot으로 설정하고 pivot을 기준으로 좌측에 작은 값, 우측에 큰 값으로 분류   
2. Conquer : 좌측 값과 우측 값을 Quick Sort 
3. Combine : 정렬된 좌측값 + pivot + 정렬된 우측값으로 list 구성        

책에서는 추가 공간을 활용하여 Quick Sort를 수행함.  
근데 학교에서 배운 (일반적인 Quick Sort)는 그렇지 않음. 

#### 3.2 Left와 Right를 이용한 Quick Sort
1. 분할된 리스트의 가장 **왼쪽 값을 L**, 가장 **오른쪽 값을 R**로 지정 
2. Pivot을 기준으로 Pivot보다 **큰 값이 나올때 까지** (또는 범위를 넘어갈 때 까지) **L 오른쪽**으로 이동
3. Pivot보다 **작은 값이 나올때 까지** (또는 범위를 넘어갈 때 까지) **R 왼쪽**으로 이동   
4. L과 R을 **Swap**
5. L과 R이 **교차**된 경우 **Pivot과 더 가까이 위치한 포인터와 Pivot 교환**  
6. Pivot을 기준으로 쪼개진 왼쪽 영역과 오른쪽 영역을 Quick Sort -> **Recursion**  

#### 3.3. Running Time
반 씩 쪼개지므로 Quick-Sort Tree의 Height은 pivot에 의하여 적절히 쪼개질 경우 **$\log{n}$**  
각 단계에서 합치는 과정에서 총 **$n$** 번의 작업 필요   

**Time Complexity : $\Theta(n\log{n})$, $\Omega(n\log{n})$**  

만약 pivot이 극단적을 최솟값(혹은 이와 가까운) 또는 최댓값(혹은 이와 가까운)값으로 선택할 경우 Quick-Sort Tree의 Height은 **$n$** 에 근접 

**Time Complexity : $O(n^2)$**

**Space Complexity : $O(1)$**   

#### 3.4. Source Code
https://github.com/CLiF-1593/SortingVisualizer/blob/master/SortingAlgorithm/Quick_Sort.py

#### 3.5 Additional
1. **Randomized Quick Sort**
랜덤하게 Pivot을 선택   
(시퀸스의 패턴에 의존하지 않고 항상 50% 확률로 좋은 분할을 수행)    
(50%인 이유는 전체 데이터의 25%~75% 사이에 위치한 데이터를 선택하면 충분히 좋은 분할로 볼 수 있기 때문) 

2. **In-Place Quick Sort**
L과 R을 활용한 Quick Sort   
책에는 추가공간을 활용하여 Quick Sort 수행  

3. **Median of Three**
첫번째 값, 가운데 값, 마지막 값 중 중간값을 선택하여 pivot으로 설정하는 알고리즘    
잘못된 Pivot 설정으로 분할이 잘못되는 경우를 방지   

4. **Hybrid Approaches**
정렬할 데이터의 개수가 적은 경우 Quick Sort는 오히려 오버헤드 발생  
더 간단한 알고리즘으로 작은 데이터를 처리 (대부분 Insertion Sort)   
=> Intro Sort (std::sort in C++)    