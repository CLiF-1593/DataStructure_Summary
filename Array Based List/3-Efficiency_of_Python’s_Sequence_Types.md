# Array Based Sequence

- - -

### 4. Efficiency of Python’s Sequence Types

#### 4.1. Python’s List and Tuple Classes
tuple은 immutable한 자료형  
따라서 list처럼 추가적인 공간 할당이 필요 없음  
따라서 Amortization이 필요 없음 

**Nonmutating Behaviors**
|Operation|Running Time|
|--------:|:-----------|
|len(data)|$O(1)$|
|data[j]|$O(1)$|
|data.count(value)|$O(n)$|
|data.index(value)|$O(k + 1)$|
|value in data|$O(k + 1)$|
|data1 == data2<br>(Comparing)|$O(k + 1)$|
|data[j:k]|$O(k - j)$|
|data1 + data2|$O(n_1 + n_2)$|
|c * data|$O(cn)$|  
<br>    

1. **Constant Time Operations**
len(data), data[index]  
<br>

2. **Searching for Occurrences of a Value**    
각 원소들을 모두 확인해야하므로 기본적으로 $O(n)$   
단, 모든 원소를 확인할 필요가 없다면 중간에 중단 가능   
<br>

3. **Lexicographic Comparisons**   
사전식으로 검사 (앞쪽 index에서 대소관계가 결정되면 뒤에는 확인할 필요가 없음)  
<br>

4. **Creating New Instances**
새로 생성하야하는 크기에 비례하게 시간이 소요됨 
<br>

**Mutating Behaviors**
|Operation|Running Time|
|--------:|:-----------|
|data[j] = val|$O(1)$|
|data.append(val)|$O(1)$*|
|data.insert(k, val)|$O(n - k + 1)$*|
|data.pop()|$O(1)$*|
|data.pop(k)<br>del data[k]|$O(n - k)$*|
|data.remove(val)|$O(n)$*|
|data1.extend(data2)|$O(n_2)$|
|data.reverse()|$O(n)$|
|data.sort()|$O(nlogn)$|

\* : amortized
<br>

1. **Adding Elements to a List**
append : 최악의 경우 $\Omega(n)$이 걸리지만, 평균적으로 $O(1)$의 시간복잡도를 달성함 
insert : amortization 되어 있을 때 (추가 공간을 새로 할당할 필요가 없을 때)  
k부터 n-1까지 n-k개의 데이터를 1칸씩 뒤로 shifting, k 위치에 val 삽입 
따라서 $O(n-k+1)$   
<br>

2. **Removing Elements from a List**
pop() : 최악의 경우 $\Omega(n)$이 걸리지만 (크기 감소 과정), 평균적으로 $O(1)$의 시간복잡도를 달성함    
pop(k) : k+1부터 n-1까지 n-k-1개의 데이터를 1칸씩 앞으로 shifting (shifting 과정에서 k번째 데이터는 자동 소멸), n-1번째 데이터를 None으로 설정  
따라서 $O(n - k)$   
remove : val이 나올때까지 반복, val이 나오면 삭제하고 뒤에 데이터 shifting (따라서 항상 $O(n)$) 
<br>

3. **Extending a List**
추가되는 양을 수용할 수 있도록 공간을 새로 할당하고, 데이터를 하나씩 추가   
append보다는 extend가 효율적임 (공간을 중간 중간 새로 확장하는 경우 X, 그 외 여러 쓸데없는 작업이 제거됨 (오버헤드 제거) + extend는 파이썬으로 돌아가지 않고 C로 돌아감)   

4. **Constructing New Lists**   
new_list = [(notation with k) for k in range(n)]    

<br>

#### 4.2. Python’s String Class
list/tuple과 대응하는 연산들은 위의 결과와 동일 
1. **Parttern Matching**
contains , find, index, count, replace, split   
간단한 알고리즘 : $O(mn)$ (m은 확인할 문자열 길이)     
$O(n)$ 알고리즘 존재    
<br>    

2. **Composing Strings**
효율적으로 str을 제작하는 방법  
하나하나 push (str += character) -> 굉장히 비효율적 
왜냐하면 str은 immutable 하므로 계속 새로운 공간을 할당 
결국 시간복잡도는 $\Omega(n^2)$ 
따라서 list 이용    
list에 append ($O(1)$)  
string = "".join(list)  