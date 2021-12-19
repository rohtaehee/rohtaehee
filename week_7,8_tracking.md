2D 디지털 합성
===========
week 7,8
-----------

### TRACKING ###

**TRACKER**

트레킹 엥커를 기준으로 큰 네모(search box)안의 범위에서 작은 네모(pattern box)안의 패턴을 찾는 것.
search box가 더 큰 이유는 카메라가 움직일때 pattern box가 흔들리기 때문.

>출처 :https://learn.foundry.com/nuke/content/reference_guide/transform_nodes/tracker.html?Highlight=tracker

작동원리 : 화면에서 한 픽셀의 위치를 (x.y)라고 가정하면 트레커를 (x.y)에 붙이는 것.
          이후 점들을 찾아서 프레임 바이 프레임으로 계속 따라가는 것.
          
     1point : 위치 정보
     2point : + 회전 정보
     3point : + 각도 (3d 데이터없이 면적을 활용해 퍼스펙티브가 어떻게 변하고 있는지 알 수 있음.)
     4point 등은 2d tracker.

camera tracker : 2d 배경에 가상의 카메라를 만들어내어 공간을 3d로 만드는 것. 

-----------------

*framehold node* : 레퍼런스 프레임으로 이용할 때 사용


**1 point tracker BG replacement**

pipeline: roto -blur - merge(mask) - tracker 

좌우로 움직임이 크다면 패턴박스를 좌우로 넓게 , 위아래로 움직임이 크다면 위아래로 넓게

트래커가 여러개일 경우, 데이터를 연결하기 어려워진다. -> 이럴 경우 트래커 탭에 있는 여러가지 기능들 이용. (stabilizer , match move, conerping 2d)

----------------

**2 point track**

로테이션 값 체크해야 회전이 계산됨

카메라에 회전이 있을 때 사용.

ex. 간판교체 등

----------------


**3 point track**

트랜스폼, 로테이션, 스케일 값 체크 

각도까지 필요할때.

ex. 거미줄 추가

----------------------

**4 point track**

3point에 트래킹 하나 추가한 것 이지만

4point는 코너핀 기능 사용 할 수 있음

conerpin 2d: 4개의 꼭지점을 계산하여 합성시킬 물체를 데이터에 맞춰 변형.

간판교체 혹은 모니터 화면을 교테할때 등등을 사용할 수 있음.

모니터 화면(안쪽이 비춰야하는 곳)의 경우에는 merge(screen) 이용.

over로 올릴 시 안쪽의 데이터가 사라짐.

--------------

**planar tracker**

로토 쉐입을 이용하여 트레킹 영역을 추적하는 트레커. - > roto 노드에 같이 있다.

평면의 영역 검출하는 원리.

pipeline: 플레이트 - 디노이즈 - 로토(합성할 부분 형태 따기) - 베지어커브 선택 - 플레나트랙 - 쉐입 색상 보라색으로 바뀜 - 그리드 선택 - 바로 옆 correct plane 선택 - 그리드 퍼스펙티브 맞추기 - 합성할 이미지에 셔플(알파 0 만들기) - 이후 코너핀 2d (일반 트레커와 동일) - blur, edgeblur 노드 이용하여 자연스럽게 - grain 노드로 노이즈를 넣어 원본플레이트와 자연스럽게 함.

주의사항 : 아무프레임이 아니라 최대한 데이터가 좋은 레퍼런스 프레임 사용할 것.

----------------------

**3d - cameratracker**

실제로 촬영하지 않고도 극적인 카메라 연출을 매트페인팅을 통해 할 수 있다는 장점.

tab : 3d viewport

scene node : 마야에서 씬 불러오는 것과 같음. (씬1 , 씬2 ...)

camera node : 3d 공간에서 시뮬레이션된 카메라 (실제로 피사체와 카메라의 거리가 시뮬레이션됨)

scanlinerender node : 3d를 2d로 보게 만드는 누크 자체 렌더러.

*cameratracker*

<img width="450" alt="스크린샷 2021-12-20 오전 5 24 57" src="https://user-images.githubusercontent.com/90230587/146689702-22c70ab8-62e1-4a4b-b698-daf3fc218f22.png">

analasys - track , solve 

feature 계산하여 3d 공간 계산.

cameramotion : 카메라 움직임

lens distortion: 렌즈 왜곡. 모르면 unknown.

focal length : 렌즈 화각. 모르면 unknown.

--------------

**2d mattepaint**

포토샵에서 매트페인팅한 이후 PSD파일로 저장, 누크 read 노드 사용.  psd option - breakout layers 하면 자동으로 레이어를 분리해서 read함
이때 자동으로 붙게되는 shuffle 노드는 구버전이기 때문에 shuffle 새로 달아도됨. input 값에서 해당레이어의 이름 선택후 사용

breakout layers로 생긴 노드에 premult - card 노드 붙임
scene 노드에 연결
card 노드에서 제일 멀리 있는 배경레이어부터 z depth 조절.
이후 camera 노드를 만져 공간감 형성.



