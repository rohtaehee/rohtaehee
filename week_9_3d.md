2D 디지털 합성
===========
week 9
-----------

### 3D ###

포토샵에서 매트페인팅한 psd 파일 read - breakout layers 기능으로 불러오기.

전체가 아니라 몇개의 레이어만 필요한 경우에는 통째로 psd 불러오고 shuffle - input layer에서 필요한 레이어 사용.

레이어 라벨링을 할땐 <value in1> 입력하면 자동으로 레벨링.

Edit Geo 이용하면 카드에 볼륨감을 만들어 씬에 입체감을 만들 수 있음. (ex. 구불구불한 산맥)

card 노드 - rows/columns 

edit geo -  tab(3d전환) -  node seclection 선택

vertex selection , face selection 등으로 바꾸면 움직일 수 있게 됨.

곡선을 선택하면 soft selection - 범위

color correct 노드로 멀리 있는 레이어를 흐리게 표현.

그러나 레이어가 많아지면 복잡해짐. 

이를 해결하기위해 레퍼런스가 될 레이어를 고르고 copy.

copy link 후 파라미터에 paste relative.

edit expression 1 이하의 값 입력. 레퍼런스 레이어의 값에 비례해 수치를 조절 가능.
