2D 디지털 합성
===========
week 6
-----------

### KEYING ###

***CHROMA KEY NODES***

*KEING*

***- Utility***

- keyer (luminance key) : 루미넌스를 이용해 키 , 알파로 만드는 것. (루미넌스 키: rgb값을 그 자체를 알파 채널에 넣겠다.)

알파가 없는 플레이트에 keyer(luminance key)노드를 붙이면 hue 와 value 값을 이용해 루미넌스 값을 계산 후, 루미넌스 값을 알파값으로 사용.

operation :
 
<img width="133" alt="스크린샷 2021-11-23 오후 3 51 48" src="https://user-images.githubusercontent.com/90230587/142981752-70147ed2-215b-479b-8845-c60cc7b63c11.png">

red keyer를 사용하면 red채널의 값이 알파가 되고, green keyer를 사용하면 green채널의 값이 알파가 됨.

<img width="592" alt="스크린샷 2021-11-23 오후 3 51 36" src="https://user-images.githubusercontent.com/90230587/142981712-20be1e81-3c53-4a51-9ad6-18436c2772da.png">

range : 
        
        A = 키잉을 무슨 값으로 시작할지.(블랙 = 0 화이트 = 1), A 슬라이더를 만져도 화이트 값(밝은 부분)은 바뀌지 않음.

        B , C = 키잉 할 부분의 거리.

        D = 키잉을 무슨 값으로 끝낼지.

- HueKeyer :

 <img width="594" alt="스크린샷 2021-11-23 오후 3 55 41" src="https://user-images.githubusercontent.com/90230587/142982077-bab893b2-bb60-49e5-b89b-cc7c6f6ea950.png">

그래프에 해당하는 색상 값이 알파 값으로 전환.
실제 크로마키 작업보다 , 색이 조금 다른 부분만 휴 키어로 뺄 수 있기 때문에 유용함.

- Difference : 

<img width="591" alt="스크린샷 2021-11-23 오후 4 37 50" src="https://user-images.githubusercontent.com/90230587/142986137-80d6b6b5-2380-4a65-be31-bccbb722577b.png">

프레임과 프레임 사이의 차이만큼을 알파로 바꿈. 키어로 사용한다기보다, 둘간의 차이를 확인하기 위해 사용 (컬러그레이딩 시 디테일)

         offset : 아웃풋의 각 픽셀로부터 값을 빼냄 (디폴트 : 0)

         gain : 흰색인 픽셀들을 게인 값으로 고정 시킴 (디폴트 : 1)

------

***- (B,G) Screen ***

- **Keylight :

<img width="589" alt="스크린샷 2021-11-23 오후 5 00 20" src="https://user-images.githubusercontent.com/90230587/142988433-8847e22f-c524-4651-96f9-06cca7665833.png">

screen colour 설정 컬러피커 선택 후 command 클릭 , command + shift 클릭으로 범위 지정 (영역의 평균 값) -> 스크린 부분의 알파가 0으로 빠짐 

      screen gain (디폴트 1) : 스크린 전체의 게인 값 조절.
      screen balance (디폴트 0.5) : 레드 블루의 밸런스를 어떻게 조절할 것인지.
      clip black (디폴트 0) : 알파에 있는 가장 어두운 블랙 값을 어떻게 조절 할 것인지. 
      클립 블랙 값을 올리면 클립 블랙보다 낮은 값의 픽셀들은 0으로 취급
      clip white (디폴트 1) : 알파에 있는 가장 어두운 화이트 값을 어떻게 조절 할 것인지. 
      클립 화이트의 값을 내리면 클립 화이트보다 높은 픽셀들을 1로 취급.
      InM : 인사이드 마스크. 로토 등으로 마스킹 하면 매트로 간주. 그 부분을 제외하고 나머지 부분에서 키라이트 적용
      outM : 아웃사이드 마스크. 로토 등으로 마스킹 하면 매트로 간주. 그부분만 키라이트 적용.

- **primatte : 

fg input -  그린을 제외한 플레이트
operation -

       1. smart select BG color - 컬러피커 사용
       2. clean BG noise - 백그라운드 노이즈들 커맨드 클릭해서 백그라운드 노이즈 삭제 (알파가 먹고 들어가는 것 조심)
       3. clean FG noise - 포그라운드 노이즈를 커맨드 클릭하여 알파가 먹고 들어간 곳 재생.
       4. spill 

- **IBKGizmo : Image based keing

카메라 무빙이 디지털로 제어되는 시스템. 액터가 있는 플레이트와 없는 플레이트 둘다 촬영.

액터가 있는 플레이트와 없는 플레이트에서 이미지 차이를 이용해 알파 값을 만듦.

          bg input : plate 
          cf input : ibkcolour

          ibkcolour : screen type green(그린이 아닌 영역들 블랙으로 빠짐) - erode 값과 patchblack 값 이용하여
          액터부분 블랙으로 바꿈 - 남아있는 디테일한 알파값은 매트로
           

- **Ulitmatte : primatte과 유사 , 탭으로 기능들이 들어가 있음.

- Chromakeyer

-----

***- Noise reduction***

Denoise node : 영역을 설정하면 누크에서 노이즈 계산 후 노이즈가 제거됨. 디테일 뭉게질수도 있으니 유의.

neat video plug in : 학생용 버전 x 구매하려면 ofx hosts 버전 구매.

------

***- key mix pipeline***

1. noise reduction
2. keying
3. keymix (A input,B input = keying , mask = roto, etc)
4. copy node (A to keying node)
5. premult

***- soft key & hard key ***

- 하드키는 안쪽
- 소프트키는 바깥쪽
- channel merge  (alpha U alpha)
