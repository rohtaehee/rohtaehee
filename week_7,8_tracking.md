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


