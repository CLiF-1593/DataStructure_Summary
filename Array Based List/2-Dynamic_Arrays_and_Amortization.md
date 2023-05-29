# Array Based Sequence

- - -

### 3. Dynamic Arrays and Amortization

Low-Level Array : 크기가 정해져있음 (수정 불가능)   
왜냐하면 하나의 Array를 위하여 무작정 공간을 무한하게 할당해줄 수 없으며,   
뒤에 있는 메모리를 누군가 사용중일 수 있으므로 무작정 추가로 공간을 할당해줄 수도 없기 때문 

* **tuple** / str : immutable data -> 크기가 정해질 수 있음    
* **list** : mutable data -> 크기가 정해지지 않음   
  => 알고리즘 필요 (Dynamic Array)  

**Dynamic Array**
1. 사용중인 공간보다 **더 많은 공간을 할당** (필요할 때 사용중인 공간을 늘리기 편하도록)  
2. 예약된 공간이 모두 사용 -> **더 큰 공간을 새로 할당**, 기존 list 데이터를 새로 만든 list로 **복사**, 기존 리스트 삭제      
=> 용량이 계단식으로 증가   

<br>

#### 3.1. Implementing a Dynamic Array
list A가 다 찼을 때 
     
**Step 1** : 새로운 Array B 할당  
     
Array A  
|0x80|0x32|0xA4|0x6C|
|-|-|-|-|
     
Array B
|NULL|NULL|NULL|NULL|NULL|NULL|NULL|NULL|
|-|-|-|-|-|-|-|-|
     
     
**Step 2** : Array A의 reference 값 복사    
     
Array A  
|0x80|0x32|0xA4|0x6C|
|-|-|-|-|
     
Array B
|0x80|0x32|0xA4|0x6C|NULL|NULL|NULL|NULL|
|-|-|-|-|-|-|-|-|
    
    
**Step 3** : A = B  
     
Array A
|0x80|0x32|0xA4|0x6C|NULL|NULL|NULL|NULL|
|-|-|-|-|-|-|-|-|
     

**Step 4** : Insert Data
     
Array A
|0x80|0x32|0xA4|0x6C|0x52|NULL|NULL|NULL|
|-|-|-|-|-|-|-|-|
     
**추가 공간 크기** : 원래 공간 크기의 2배

*** 파이썬 코드는 교과서 196pg 참조 
     
<br>
     
#### 3.2 Amortized Analysis of Dynamic Arrays
**Amortized Analysis** :  
overflow가 일어나는 경우에만 크기를 2배로 늘림 
overflow가 일어나지 않는다면 모든 append 연산은 $O(1)$,  
한 번 늘리고 나서는 이전 list 크기만큼은 $O(1)$의 append 연산이 보장  

*** 증명 같지 않은 증명을 보고 싶으면 198pg 

**Geometric Increase in Capacity**  
* 공간이 부족할 때 n배씩 늘리는 전략  
* 크기를 늘리는 정도는 선택 가능    
(2 대신 4배로 늘린다면 메모리 낭비↑, 평균적인 소요시간↓)  
(2 대신 1.5배로 늘린다면 메모리 낭비↓, 평균적인 소요시간↑)  
* Amortized하게 분석하면 항상 $O(1)$  

**Arithmetic Progression**
* 공간이 부족할 때 c개씩 늘리는 전략
* 늘리는 정도 선택 가능 
* 시간복잡도를 분석해보면 $\Omega(n^2)$ 
  
$let \; m = \lfloor{\frac{n}{c}}\rfloor$  
$\sum_{i=1}^{m} ci=c\times \sum_{i=1}^{m} i = c \frac{m(m+1)}{2} \ge c\frac{\frac{n}{c}(\frac{n}{c} + 1)}{2} \ge \frac{n^2}{2c}$  

**Shrinking an Array**
사용 용량이 50% 이하일 때 절반을 줄여버리면 append 될 경우 다시 공간을 2배로 늘리는 작업을 하므로 매우 비효율적임 
따라서 **25% 이하로 떨어질 때 절반으로 줄이도록** 알고리즘을 설계 
그러면 항상 사용중인 공간과 전체 할당된 공간 사이의 관계가 약 2배 차이로 유지됨 
(최대 4배 이상 차이나지 않도록 하는 알고리즘) 
