2D 디지털 합성
===========
week 7
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

*1 point tracker*

pipeline: roto -blur - merge(mask) - tracker


