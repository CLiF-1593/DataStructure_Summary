# Array Based Sequence

- - -

### 1. Python's Sequence Types
1. **list** 
2. **tuple**
3. **str**

> 모두 array를 기반으로 한 자료구조이다.    
> Encapsulation 되어있는 구조이다.  
> => 내부 구조를 자세히 알 필요가 없음  
> => Public한 기능들의 작동 방식만 대충 알면 됨 

<br>

### 2. Low-Level Arrays
**Array** : 연속된 메모리 공간
> 컴퓨터의 메모리는 주소값 (Memory Address)으로 저장되는데 Array는 이러한 공간들이 일렬로 이어진 구조임.    
> RAM (Random Access Memory)를 사용하기에 주소값을 활용하여 O(1)의 시간복잡도로 메모리에 접근 가능한 구조임.  

**Array를 사용하는 이유** : 각 데이터를 따로 보관하는 것이 아니라, 연관된 데이터들을 연속된 데이터로 그룹화하여 보관하여 인덱스를 활용해 데이터에 쉽게 접근하고, 관리할 수 있음.

**Terms**
1. **Cell** : 데이터의 각 위치
2. **Index** : 데이터를 정수형으로 표현한 것

Array의 모든 Cell의 크기는 같아야함.    
(왜냐하면 위치를 O(1)로 찾기 위해서 (address = start + cellsize * index))  

<br>

#### 2.1. Referential Arrays
Python에서는 다양한 타입의 데이터를 Sequence Data Type에 넣을 수 있음.  
하지만 Array의 모든 원소들의 크기는 같아야함.   
**=> 따라서 참조 객체를 활용 (Reference Objects)**

> **참조 객체**
> 어떤 데이터의 위치를 포인팅하는 객체  
> 다른 말로 화살표 ([참조] -> [데이터])
> 참조 객체의 크기는 항상 일정 (64bits) -> Array에 저장할 수 있음
> 
> (C/C++의 포인터(*) 혹은 C++의 참조(&)와 같은 역할)    

* **None Object** : 파이썬의 비어있는 객체    
(C의 NULL, C++ : nullptr과 유사 (아마도...?))   

참조 객체를 사용한다.  
=> 어떤 같은 객체를 두 개 list, tuple 혹은 그 외 다른 참조형 객체가 같은 객체를 가르키고 있을 수 있다.  
**=> 참조된 데이터가 변경된다면 그 변경 사항이 모든 참조 변수에서 적용되어 나타남.**    
(단 Mutable일 때만 변경 가능, Immutable한 자료는 새로운 객체 생성)  


ex) List Slicing : 새로 만들어진 list 객체는 새로운 참조 객체만 생성하고, 원래 리스트가 참조하고 있던 객체를 그대로 참조.

**Shallow Copy & Deep Copy (얕은 복사 & 깊은 복사)**    
* Shallow Copy : 새로운 객체를 제작, 그 객체의 내부 데이터를 그대로 복사 => 참조 객체도 그대로 복사되므로, 참조하고 있는 객체의 종류는 서로 같음  
* Deep Copy : 새로운 객체를 제작, 그 객체의 내부 데이터 중 참조 객체가 있으면, 참조하는 객체를 새로 제작하여 참조 (copy 모듈의 deepcopy 함수 이용)    
* Examples
  - Python list의 `*`연산자 : 새로운 객체를 n개 제작하는 것이 아니라, 객체의 **참조 객체**를 n개 제작   
  - Python list의 extend 함수 : 각 원소에 해당하는 객체를 복사하는 것이 아닌, 원소의 **참조 객체를 복사**하여 원본 리스트에 추가

<br>

#### 2.2 Compact Arrays in Python
**Compact Array** : Reference가 아닌 값을 직접 저장하는 Array => 특정 데이터만 저장 가능 (ex. str : character를 저장한 array)  

> **장점**    
> 1. 메모리 사용량이 적음 (Referece 객체가 추가적으로 필요하지 않음) 
> 2. 연속된 데이터이므로 cache되기에 유리함 (Referece가 가르키는 실제 데이터의 위치는 일정하지 않음 (랜덤하다고 말할 수는 없을듯?))   

> **array 객체**    
> Python의 Compact Array를 제작할 수 있도록 해줌.   
> type code가 필요함. (arr = array('i', [0, 1, 2, 3]))  
> |Code|C Data Type (byte)|
> |:--:|:---------:|
> |b|signed char (1)|
> |B|unsigned char (1)|
> |u|unicode char (wchar) (2 or 4)|
> |h|signed short int (2)|
> |H|unsigned short int (2)|
> |i|signed int (2 or 4)|
> |I|unsigned int (2 or 4)|
> |l|signed long int (4)|
> |L|unsigned long int (4)|
> |f|float (4)|
> |d|double (8)|    
> 
> ctype만 가능 (class는 불가능)
> 이런건 시험에 안 나올 확률이 굉장히 높음  