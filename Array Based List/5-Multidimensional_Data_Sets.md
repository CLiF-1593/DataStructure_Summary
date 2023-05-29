# Array Based Sequence

- - -

### 6. Multidimensional Data Sets
Matrix 제작법을 설명하고 있음   

여기서는 그냥   
`list/tuple = [[0] * 10] * 10`으로 소환하면 안된다는 걸 알려주고 있음   
(왜냐하면 list/tuple은 reference를 저장하기 때문 -> 하나가 바뀌면 모든 행에서 데이터가 바뀜) 

`list/tuple = [[0] * 10 for i in range(10)]`가 바람직함 