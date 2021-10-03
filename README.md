# Week-03

## Gamma
화면의 밝기. <br> 
감마값이 1인 경우는 입력의 출력의 밝기가 같지만, 1보다 크면 화면이 좀 더 어둡게 표현이되고, 1보다 작으면 밝게 표현된다. <br> 
[감마란 무엇인가](https://blog.daum.net/trts1004/12109543)<br> 

![캡처](https://user-images.githubusercontent.com/90567312/135766013-0811d372-f74d-418c-a15f-3ccd67ac841e.JPG)


**감마 보정 (Gamma Correction)**

비디오, 컴퓨터 등에서 빛의 강도 신호를 변형하는 것

영상장치에서는 가장 밝은 빛의 밝기 정도를 1로, 가장 어두운 빛의 밝기는 0으로 본다.

CRT 보정을 위한 값: 감마값 2.2 (콘트라스트가 매우 높게 표현된다)

이미지 촬영 시: 감마값 0.45 (감마 2.2에서 이미지가 제대로 보이기 위해서 감마 0.45인 상태로 이미지 촬영)

![캡처2](https://user-images.githubusercontent.com/90567312/135766384-2b87d135-283a-4eb2-bc59-010fc3c66d1e.JPG)


**컴퓨터 모니터에서 감마 보정**

방송용 장비 감마값: 2.2 
 - 애플 감마값 1.72는 어둡고 색감이 강하게 보인다.

IBM 컴퓨터의 감마값: 2.5
 - 방송용 장비 감마값 2.2는 다소 어둡게 보인다.

애플 컴퓨터 감마값: 1.72
 - IBM 감마값 2.5는 너무 밝게 나타난다.

![캡처3](https://user-images.githubusercontent.com/90567312/135766576-98018757-b146-422a-b8a9-17d44476524d.JPG)




## Linear Workflow  
모든 그래픽 작업이 **선형 색 공간 Linear Color Space** 에서 이루어지는 방식.    
선형 색 공간과 감마 색 공간(Gamma Color Space) 의 차이 

![118788622-ecc46600-b8ce-11eb-843c-c985eb6be98e](https://user-images.githubusercontent.com/90567312/135766738-fbab83a8-51dd-4744-b799-7f313403ea4d.png)


사람의 눈은 어두운 색에 훨씬 민감하기 때문에 감마 색 공간의 그라데이션이 더 자연스럽다고 느껴지지만, 실제로 정확한건 선형 색 공간이다.

선형 색 공간의 그라데이션을 감마 색 공간처럼 눈에 자연스럽게 만드려면 감마값Gamma를 조정해야 한다.


![캡처4](https://user-images.githubusercontent.com/90567312/135766902-0054ed5b-2059-4212-aefe-ab5b37ad75c6.JPG)


감마값을 2.2로 조정할 시 이미지가 어두워지기 때문에

jpeg와 같은 이미지 파일들은 자체적으로 감마 보정이 된 채 저장된다.


감마 색 공간에서의 이미지들은 이미 한 번 밝아진 이미지 이기 때문에, 선형 색 공간에서 작업을 하는 것이 권장된다.

[선형 워크플로우 완벽 이해](https://kyoungwhankim.github.io/ko/blog/color_linearworkflow/)



## ACES - (Academy Color Encoding System)
**색에 대한 업계 표준으로 설계되었으며, 영상 제작의 모든 과정을 다룬다.** 

촬영부터 후반작업, 배급에 이르기까지 모든 유형의 컬러 매니지먼트 (color management)에 대한 가이드라인이다.

ACES 컬러 스페이스는 인간이 볼 수 있는 보든 색을 포함하고 있다.

컬러 스페이스의 제약이나 제한이 없다.

![Gamuts_Plot_ACEScg_sRGB](https://user-images.githubusercontent.com/90567312/135767250-d6770240-447f-4aa6-9335-d327a02d22f7.jpg)


[Color Grading: What is ACES?](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=baekhyebin&logNo=222092359528)


## Premultiplication  

RGB 색상으로 시작해 투명도 개념을 추가하는 것.

![캡처5](https://user-images.githubusercontent.com/90567312/135767420-d68144fb-9dd3-4553-90e1-769986054ae0.JPG)

[Cinematic Color - 3.3. Compositing](https://cafe.naver.com/dcinemalab/1408)
[What is Premultiplication? - School of Motion](https://www.schoolofmotion.com/blog/premultiplication/)

## RGBA
투명한 효과가 필요할 경우: Transparent로 처리 <br>
투명도의 정도와 색상을 조절할 경우: RGBA를 사용

[기초) background 속성 및 투명도 RGBa 정리](https://blog.naver.com/takudaddy/221925844631)

**RGBA의 두가지 형식**

_1. non-premultiplied alpha_

알파 값만이 화소의 투명한 정도를 나타내며, RGB 각각의 값은 투명도와 관계 없이 빨강, 초록, 파랑의 강도를 표현한다.
이 방식에서의 RGBA는 알파 값만이 투명도를 나타내며 RGB는 각각 투명도에 관계 없이 빨강, 초록, 파랑의 강도만을 표현한다.

![9975123B5C0FD14335](https://user-images.githubusercontent.com/90567312/135767658-b4d1b3f5-fff2-4b34-8b1d-13bfaee0d125.png)


_2. Premultiplied alpha_

Premultiplied alpha 방식의 RGBA 인코딩은, 그 이름이 암시하듯이 알파 값을 RGB에 미리 곱해둔 것이다.
이 방식의 RGBA에서 RGB의 값은 그 자체만으로도 색상과 더불어 이미 투명도를 반영하고 있으며, 알파 값은 복잡한 그래픽 처리를 위해서 덤으로 딸려 들어오는 것이라고 볼 수 있다.

![99C8A5495C0FD14314](https://user-images.githubusercontent.com/90567312/135767737-c234312d-f4af-4e8c-841a-fac9f666302f.png)

이 방식의 특징은 RGB 각각의 값이 알파의 값보다 항상 작거나 같다.

[알파 채널(투명도)의 두 가지 표현 방식](https://nanite.tistory.com/98)     

