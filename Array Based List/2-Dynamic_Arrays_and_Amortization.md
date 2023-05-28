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

*** 파이썬 코드는 교과서 pg 196 참조 
     
<br>
     
#### 3.2 Amortized Analysis of Dynamic Arrays