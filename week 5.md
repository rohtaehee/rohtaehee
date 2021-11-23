2D 디지털 합성
===========
week 5
-----------

### CHROMA KEY

***크로마키란?***

색상 차이를 이용하여 움직이는 피사체를 다른 화면에 합성하는 텔레비전의 화면 합성 기법. 일기 예보, 선거 방송, 역사 스페셜 등의 프로그램에서 많이 사용된다. 컬러 텔레비전의 카메라에서 얻을 수 있는 RGB 신호를 이용하여 그 색(chroma)의 차이를 키(key)로 하여 빼내고 싶은 피사체와 배경을 분리하고, 그것을 다른 화면에 합성하는 원리이다.

> 출처 : [네이버 지식백과] 크로마 키 [chroma key] (IT용어사전, 한국정보통신기술협회)

--------------------

***크로마키의 시작***

조르주 멜리에스가 A man has multiple heads(1898)를 세상에 공개. 서로 다른 노출에 "매트" 기법을 활용 

<img width="1010" alt="스크린샷 2021-10-18 오후 2 01 28" src="https://user-images.githubusercontent.com/90230587/137671905-ad085b85-0309-4ca0-a533-25047410b4cc.png">

> 출처 : https://www.youtube.com/watch?v=RzsdqsiJQ6Y

멜리에스는 검은색 페인트로 유리를 칠한 후 프레임의 특정 부분을 유리를 이용해 노출을 막음. 이후 필름을 되감고 나머지는 모두 어둡게 하여 매트 아래에 있던 필름 부분만 드러내어 이중 노출을 시킴.

이후 에드윈 포터의 1903년 영화 Great Train Robbery에서도 매트 기법을 사용함. 

<img width="1008" alt="스크린샷 2021-10-18 오후 2 42 51" src="https://user-images.githubusercontent.com/90230587/137675186-3be35612-42b3-40fe-b173-787b91f59b9c.png">

> 출처 : https://www.youtube.com/watch?v=Bc7wWOmEGGY

해당 영화에선 단순히 마술 기법이 아니라 사실적인 세계를 만들기 위해 사용. 움직이는 기차 컷에서 창문 밖을 보면 합성된 배경이 적용되었음. 이중노출과 매트를 사용.

![Williams-Process-600x262](https://user-images.githubusercontent.com/90230587/142374708-9c56ac00-73ff-44eb-9ec8-4a8a240b2032.jpeg)

1918년 frank williams가 영화 'sunrise'에 합성을 사용하기 위해 개발. 검은색 배경에서 촬영 후 높은 대비의 네거티브로 복사.

이후 파란색 크로마키 , 노란색 크로마키로 발전 후 90년대 후반 디지털 필름 후처리가 시작되며 그린 크로마키가 자리를 잡음.

----------

***크로마키에서 green을 사용하는 이유?***


![253E363F522E7C5724](https://user-images.githubusercontent.com/90230587/142792788-1623848a-653c-4bd9-a26d-e0afefa6f1b0.jpeg)
![272C1640522E7C3C2F](https://user-images.githubusercontent.com/90230587/142792792-93b458e2-feeb-4bcc-a95f-1333687a4809.png)

> 출처 : http://www.unc.edu/~rjean/demosaicing/demosaicing.pdf

디지털 시대로 넘어오며 픽셀 단위에서 Bayer pattern을 사용하게 됨. bayer pattern이란 한 픽셀을 네개의 구역으로 나눈 것.
네개 중 두개가 그린이고 나머지 각각 하나씩을 레드와 블루가 가지고 있기때문에 초록색 크로마키를 사용하는 것이 보편화되고 효율적이기때문.
**결국은 크로마키나 로토나 매트를 추출하여 알파채널을 만들기 위함이다.**

---------------
***CHROMA KEY LIGHTING***

![How-to-Light-a-Green-Screen-With-Two-Lights-StudioBinder](https://user-images.githubusercontent.com/90230587/142798131-61594362-487f-43f1-8a06-89b4bd05b762.jpeg)

>출처 : https://www.studiobinder.com/blog/green-screen-lighting-setup-techniques/

------------
