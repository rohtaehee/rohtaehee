2D 디지털 합성
===========
week 11
-----------

### EXR ###

exr 파일 포맷이란 HDR 이미지. 

채널당 16비트 이상 32비트까지 가능함.

 
사실 float 하나가 32비트인데 TGA 이미지는 겨우 8비트밖에 되지 않음

즉 처리할 수 있는 용량대비 너무 적은 이미지를 사용하고 있었던 것. 

때문에 마치 카메라의 RAW 파일처럼 깊이값이 깊은 이미지를 생성해 낼 필요가 생기는데, 이것이 exr 파일 포맷. 

>출처 : http://egloos.zum.com/chulin28ho/v/5452964


https://www.openexr.com/

### DEEP COMPOSITING ###

ZDepth: 카메라에서부터 해당 픽셀까지 거리를 계산.

물체가 반투명 혹은 투명하거나 뒤에 물체가 또 있는 경우는 데이터 계산 x.

그러나 , deep 으로 렌더링 한 이미지는 해당 픽셀과 픽셀들의 샘플링 데이터가 전부 있기 때문에 뎁스 계산 가능.

deepread / deepmerge 등 depp 전용 노드 사용.


3d 오브젝트 뿐만 아니라 볼륨 레이어에도 사용 가능. (ex. 연기)

하지만 용량이 매우 크기 때문에 필요한 경우에만 사용할 것.

--------

**deep research**

Skill Up With Nuke | An Introduction To Deep Compositing In 11.2

> 출처 : https://www.youtube.com/watch?v=OFu93YJIIx8


피운드리사에서 제공하는 누크 기초.

> 출처 :https://learn.foundry.com/nuke/content/comp_environment/deep/deep_compositing.html

