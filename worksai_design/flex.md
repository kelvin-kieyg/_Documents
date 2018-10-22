flex

cf> flex & grid
flex : 레이아웃을 다룰 때 한번에 하나의 차원(행이나 열)만을 다루는 1차원 레이아웃
grid : 행과 열을 함께 조절하는 2차원 모델


주축 / 교차축

주축 = row
row-reverse
> 인라인 방향으로 행을 따른다

column
column-reverse
>상단에서 하단으로 블록방향을 따른다.


교차축 

cross Axis-flex-direction :row
>
교차축은 주축에 수직.
flex-direction(주축)이 row(or row-reverse)라면 교차축은 열 방향을 따른다.

주축이 column(or column-reverse)라면 교차축은 행 방향
cross Axis-flex-direction : column


flex요소를 정렬하고 끝을 justify(맞추려면) 어느 축이 어느 방향인지 이해하는 것이 중요.
flex는 주축, 교차축을 따라 항목을 정렬하고 끝을 마추는 각종 속성을 적용.


시작선 끝 선으로 생각하는 것이 자연스럽다. (교차축의 시작선 끝선)

-----


flex container
> 문서의 영역중 flexbox가 놓여 있는 영역을 flex container.
flex container를 생성하려면 display:flex or inline-flex라고 설정.
이 값이 지정된 일차 자식(direct children) 요소가 flex 항목이 된다. 

default 값.
 - 항목은 행으로 나열(flex-direction 속성의 기본값은 row_
 - 항목은 주축의 시작 선에서 시작
 - 항목은 주 차원 위에서 늘어나지는 않지만 줄어들 수 있다
 - 항목은 교차축의 크기를 채우기 위해 늘어난다.
 - flex-basis 속성은 auto
 - flex-wrap 속성은 nowrap으로 지정


--------

flex-wrap을 이용한 복수 행 flex container 지정

flexbox는 1차원 모델, but
flex 항목이 여러 행에 나열되도록 할 수 있다. 그 경위 각 행이 새로운 flex-container라고 생각.
공간 배분은 해당 행에서만 이루어지며 다른 행은 영향을 받지 않는다. 

항목이 여러 행에 나열되려면 flex-wrap속성의 값을 wrap으로 지정.
> 그러면 항목이 하나의 행에 들어가지 않을 정도로 클 경우 다른 행에 배치.
> nowrap을 지정하고 flex항목에 대한 확대/축소 방식을 별도로 지정하지 않으면 flex 항목들은 컨테이너의 폭에 맞게 줄어든다. 
>nowrap을 지정하면 항목이 전혀 줄어들 수 없거나 충분히 줄어들 수 없을 때 흘러넘치게 된다.



-----


# 축약형 속성 flex-flow

flex-direction & flex-wrap 속성을 flex-flow라는 축약 속성으로 합칠 수 있다. 첫 번째 값은 flex-direction이고 두 번째 값은 flex-wrap이다.




-----


# flex 항목에 지정 가능한 속성들


 - flex-grow
 - flex-shrink
 - flex-basis

## flex-basis
> 항목의 크기를 결정. 기본값은 auto. flex 항목에 크기가 지정되어 있지 않으면 flex 항목의 내용물 크기가 flex-basis 값으로 사용된다. 따라서 flex container에 display:flex 속성만을 지정하면 flex항목들이 각 내용물 크기만큼 공간을 차지하게 된다.


## flex-grow
>flex-grow 값을 양수로 지정하면 flex항목별로 주축 방향의 크기가 flex-baiss 값 이상으로 늘어날 수 있게 된다. 
ex) flex-grow 값을 1로 지정하면 사용가능한 공간은 각 항목들에게 동일하게 분배되며, 각 항목은 주축을 따라 분배받은 값만큼 사이즈를 늘려 공간을 차지한다.

첫 항목의 flex-grow 값을 2로 지정하고 나머지 두 개의 항목을 1로 지정하면 각 항목에 지정된 flex-grow 값의 비율에 따라 남은 공간이 분배된다. 
ex) flex-grow 비율이 2:1:1 이므로 첫 항목에게 100px, 두번째와 세 번째 항목에게 50px씩 분배된다. 


## flex-shrink
>flex-grow 속성이 주축에서 남는 공간을 항목들에게 분배하는 방법을 결정한다면, flex-shrink 속성은 주축의 공간이 부족할 때 각 항목의 사이즈를 줄이는 방법을 정의한다. 
flex container 가 flex항목을 모두 포함할 만큼 넉넉한 공간을 갖고 있지 않고 flex-shrink 값이 양수이면 flex 항목은 flex-basis에 지정된 크기보다 작아진다. 
flex-grow 속성과 마찬가지로 더 큰 flex-shrink 값을 갖는 항목의 사이즈가 더 빨리 줄어든다. 

* flex-grow, flex-shrink값이 비율임을 유의! 


------

# 축약형 속성 flex

보통은 flex-grow, flex-shrink, flex-basis 값을 각각 사용하지 않고 이 세 속성을 한번에 지정하는 flex축약형을 많이 사용.
flex-grow, flex-shrink, flex-basis 순서로 지정.

첫 값이 양수를 지정하면 flex 항목이 넓어질 수 있다. 두 번째 값은 flex-shrink를 지정하며, 양수를 지정하면 flex항목이 좁아질 수 있다. flex-basis를 지정하며, flex 항목이 넓어지거나 좁아질 때 고려하는 기준 값.


-----------


flex : initial 로 지정하면 
> flex : 0 1 auto와 동일하게 동작.
flex-basis보다 커지지 않고, flex-shrink가 1이므로 flex container 공간이 모자라면 크기가 줄어든다.  flex-basis가 auto이므로 flex항목은 주축 방향으로 지정된 크기 또는 자기 내부 요소 크기 만큼 공간을 차지한다. 

flex : auto로 지정하면
>flex : 1 1 auto와 동일.
initial과 다른 점은 주축 방향 여유 공간이 있을 때 flex항목이 늘어나서 주축 방향과 여유 공간을 채우는 점만 다르다. 

flex : none으로 지정하면
>flex : 0 0 auto와 동일.
flex container 크기 변화에도 flex 항목 크기는 변하지 않고, flex-basis를 auto로 지정했을 때 정해지는 크기로 결정.

flex : 1 or flex : 2 처럼 쓸 수도 있는데 이는 flex-grow 만 지정하고 나머지는 1 0 으로 사용한다는 뜻이다. 따라서 flex : 2 는 flex : 2 1 0과 동일하게 처리된다. 













