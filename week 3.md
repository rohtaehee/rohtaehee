2D 디지털 합성
===========
week 2
-----------
### Gamma / Linear workflow

1. **Gamma**

사람의 눈은 베버의 법칙으로 인해 ***어두운색***에 더욱 민감.  

(*베버의 법칙이란?* 자극을 받고 있는 감각기에서 자극의 크기가 변화된 것을 느끼려면 처음에 약한 자극을 주면 자극의 변화가 적어도 그 변화를 쉽게 감지할 수 있으나 처음에 강한 자극을 주면 자극의 변화를 감지하는 능력이 약해져서 작은 자극에는 느낄 수 없으며 더 큰 자극에서만 변화를 느낄 수 있다는 법칙이다.)

> 출처 : [네이버 지식백과] 베버의 법칙 [Weber's law] (두산백과)

![118788622-ecc46600-b8ce-11eb-843c-c985eb6be98e](https://user-images.githubusercontent.com/90230587/135759993-81488e05-95a0-4524-aef3-0b4057f11957.png)

우리는 위쪽이 그림이 더 자연스러운 그라데이션이라고 생각. 하지만 수학적으론 밑쪽의 그림이 사실은 더 자연스러운 그라데이션임.

그렇기 때문에 선형 색 공간의 그라데이션을 ***사람의 눈***에 더욱 자연스럽게 만드려면, ***감마*** 값을 조정 해야함.

![gdwUz4F](https://user-images.githubusercontent.com/90230587/135760256-c0d5980b-a468-440a-8151-3ab3acd41e5f.png)

***

2. **Linear workflow**

선형 워크플로우란 모든 그래픽 작업이 선형 색 공간(Linear Color Space)에서 이루어지는 방식.
 
>출처 https://kyoungwhankim.github.io/ko/blog/color_linearworkflow/

![3how-linear1](https://user-images.githubusercontent.com/90230587/135761935-f0e296b3-0d26-4263-8e80-47946d4193f0.jpeg)

> 출처 : https://www.eizoglobal.com/library/management/3dcg/

***export할때 옳바른 색 공간을 지정해야 옳바른 이미지를 얻을 수 있음.***

***

### ACES

1. **Academy Color Encoding System**

아카데미에서 제시하는 업계 표준의 컬러 매니지먼트 시스템.

![img](https://user-images.githubusercontent.com/90230587/135762249-42d0a3e2-873b-42fc-89b9-27bbcaf47eba.png)

위 CIE 도표는 인간이 볼 수 있는 모든 색 영역을 나타내고 보라색으로 표시된 ACEScg의 색 영역은 디지털로 구현된 대부분의 색 공간을 커버함. 쉽게 말해 ACES 색상 표준에 넣으기만 하면, 모든 사람이
같은 색 환경에서 작업을 할 수 있게 됨.

![다운로드](https://user-images.githubusercontent.com/90230587/135762279-8f27898f-1876-4fd2-9e82-087c0dbe1389.png)

(좌) 일반적인 '선형' 워크플로우 / (우) 동일한 씬을 ACEScg로 변환 후 ACES sRGB LUT로 나타낸 것

> ACES의 색 공간을 ACEScg라고 합니다. 이 색 공간은 인간의 가시영역을 나타내는 CIE XYZ 1931, 디지털 시네마 환경에서 사용되는 DCI-P3, HDTV Rec.709 및 UHDTV Rec.202 색공간을 포함합니다.
>  > 출처 : https://artnfear.com/entry/ACES-%EC%8B%9C%EC%8A%A4%ED%85%9C%EC%9D%B4%EB%9E%80

***

### premultiplication

![1](https://user-images.githubusercontent.com/90230587/135762630-0a625769-449b-44db-82be-0dca71c44bf6.png)

premult : 입력의 rgb채널을 알파로 곱하는 것.

unpremult : 입력의 rgb채널을 알파로 나누는 것.

불투명한 이미지의 알파 : 1

투명한 이미지의 알파 : 0

색상을 가진 이미지는 rgb값 보다 알파 값이 더 높기때문에 색상에 문제가 생김.


CG 렌더링에서는 경계선의 곡선처리에 대해 문제가 생겨 알파가 있는 3D 혹은 2D소스(연기, 파편, 파티클 등)를 사용시 엣지영역에 알파값을 좀 더 넓게 뽑아내기 위해 Unpremult 노드를 사용하여 원본소스 픽셀정보값들을 보존하여 기술적 문제를 해결함과 동시 색 보정을 실시를한다.

> 출처 : NO.14 Premult and Unpremult|작성자 Fighting MAN


Premult된 이미지에서 색보정을 하면 안되는 이유는 이미지 경계선에 있는 그라데이션 때문.


