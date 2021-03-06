2D 디지털 합성
===========
week 4
-----------

### MERGE 

<img width="468" alt="스크린샷 2021-10-12 오후 4 34 09" src="https://user-images.githubusercontent.com/90230587/136912007-d908b7ac-a63a-40cd-971e-1f2a897519f2.png">

A: Input A

a: alpha of A

B: Input B

b: alpha of B

1: alpha

0: alpha x

---

### ROTOSCOPING

실제 촬영한 영상을 바탕으로 하여 각각의 프레임 위에 덧붙여 그리는 기법. 

> 출처 : https://terms.naver.com/entry.naver?docId=863220&cid=42346&categoryId=42346

오브젝트와 배경을 합성할때 , 오브젝트가 촬영된 원래의 배경을 분리 시켜야함. 
오브젝트가 그린스크린에서 촬영되지 않았을경우 rotoscoping을 이용해 배경을 분리시키고자 함.

오브젝트를 한 개의 베지어로 따면 생기는 이슈 - 오브젝트가 움직이거나 시점이 바뀔때 대처하기 어려움.

베지어를 만들때 오브젝트의 구조를 생각하고 분석해서 만드는 것이 유리하다.


***- pipeline***

1. read node 이용 - 푸티지 임포트
2. 단축키 [O] - roto node (팁 : 루미넌스 값 이용하여 쉐입이 배경과 더 잘 분리되어 보이게 만들 수 있음.)
3. roto 작업 후 shuffle 노드 - properties : rbb/a 값 중 왼쪽 알파와 오른쪽 R값 연결
4. 보통 dpx로 추출. dpx란 vfx업계에서 표준으로 사용하는 rgb값을 가진 파일. 추출시 반드시 rgb데이터로 추출해야 에러가 없음.
5. 반드시 파일명.####.dpx 형식으로 저장해야함 (####란? - 추출할 프레임의 범위)

**내가 dpx를 받았을땐?**

1. 원본 플레이트 파일(B)과 dpx파일(A) copy 노드 붙임.

2. copy 노드 properties에서 copy channel 세팅을 rgba.red to rgba alpha로 바꿈

3. premult 노드와 merge노드 이용하여 합성

***- rotoscoping shortcut***

1. [O] : roto node
2. [P] : rotopaint node
3. [Z] : increase smoothness
4. [E] : feather (cmd + E 페더삭제)

 
 ---
 
### ROTOPAINT
**roto node** : 알파의 쉐입을 만들어내는 작업을 할때 주로 사용

**rotopaint node** : rgb컬러를 스탬프하는 클론작업 , 혹은 지워내는 작업을 사용할때 사용

두가지 노드는 거의 유사한 노드이며 rotopaint 노드가 기능이 조금 더 많다.
