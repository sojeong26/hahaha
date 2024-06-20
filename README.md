# [하하하] 2024 오픈소스프로그래밍 팀프로젝트
### 시각장애인을 위한 페트병 분리수거 인식 AI

#### 0. 기술 개발 배경

- 2019년 기준 분리수거율은 87.1%에 달하지만, 환경부가 조사한 현황에 따르면 분리 배출한 플라스틱의 재활용률은 30%에 불가함.
- 원인은 올바르지 않은 분리수거와 그로 인한 투명 페트병의 오염.
- 투명 페트병만을 임의로 분류하여 수거한다면 순환경제에 큰 도움이 될 것임.
- 이미 시행되고 있는 분리수거 기계를 직접 사용해보니, 안내를 제공하지 않아 헤맬 수 있고 tts 기능이 없어 시각장애인과 사회적 약자의 사용이 불가능하다시피 함. 또한 앱을 설치해야 한다는 번거로움이 있음.
  

[올바른 분리수거를 위한 유의 사항]
![image](https://github.com/sojeong26/hahaha/assets/164765964/d32c23ec-42ce-4d72-95c4-944366c47c07)

  
#### 1. 시작 화면
- STTCode.ipnynb / website-> page1.html / QRcode
- STT 기술로, Whisper 이용
- whisper model 설정, 업로드 받은 파일을 텍스트로 변환
- 언어를 한국어로 설정
- 음성인식기에서 인식한 텍스트에서 "하이, 하하하"가 인식되거나 QR코드를 찍을 경우 실행됨.

  
![image](https://github.com/sojeong26/hahaha/assets/164765964/389bd954-0df8-4bbf-a0f3-025f578af631)

- 웹사이트의 의의를 보여주기 위해 투명 페트병의 중요성과 분리수거 방법이 포함.
- "적립(save)", "설명(manual)" 버튼을 누르면 해당 페이지 이동.

![image](https://github.com/sojeong26/hahaha/assets/164765964/bd5a312f-9e69-4c27-8196-c3ae920dd690)
  
  
#### 2. 페트병 투입 화면
- crawling.py / website-> page1-2.html, page2.html 

- 키패드를 이용하여 휴대폰 번호 입력.
- camera() 함수에 페트병을 비춤으로써 기계 투입을 가정함.
- captureImage() 함수로 이미지 캡처 후
- "투입 완료 (complete)" 버튼을 누르면 AI가 이미지 분석 시작하여 분리수거 가능여부 판별함.
    
- 페트병의 색, 라벨 여부 판별하여 라벨이 없는 투명 페트병일 경우에만 투입 종료를 누르도록 함.
- crawling.py로 수집한 페트병 이미지로 AI가가 학습, 학습 확인, 탐색함.
  
- "적립 종료 (finish)" 버튼을 누르면 적립 화면으로 이동함.
  
![image](https://github.com/sojeong26/hahaha/assets/164765964/057165df-4506-4758-9c4e-e813367b65d9)


#### 3. 적립 화면
- TTScode.ipynb / website-> page4.html

- 최근 적립 포인트(point)와 총 누적 포인트(totalpoint)를 표기함.
- tts기능을 통해 사용이 성공적으로 종료되었음을 알려줌. 

![image](https://github.com/sojeong26/hahaha/assets/164765964/5866b928-b661-40ca-bccd-8cd22cb394d8)


#### 4. 웹사이트 사용 설명서
- TTScode.ipynb / website-> page3.html

- tts기능을 통해 웹사이트 사용 방법을 설명함.
- tts 기술은 Google의 gtts 라이브러리 활용
- 사용 메뉴얼 텍스트 총 9개로 분류, 반복문을 통해, 오디오로 저장
- 반복문을 통해, 저장된 오디오 파일을 자동 재생
- time.sleep()를 통해 오디오 재생 간격 설정
  
  ![image](https://github.com/sojeong26/hahaha/assets/164765964/c8ed5809-5925-4d48-a0ee-76b7c1e672f7)
