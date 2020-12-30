# drone-vis-recog-datasets-2


## 1. 데이터 개요
- 동영상 정보 
  - 동영상 클립 수: 70
  - 해상도: 1920x1080(FHD)
  - Frame rate: 15fps (450frames/30seconds)

- 어노테이션
  - 동영상 클립의 각 이미지에 대하여 객체의 위치 및 클래스를 라벨링함

---

## 2. 데이터 어노테이션
### 2-1. 어노테이션 대상
- 동영상 클립 내 각 이미지(클립 당 450개 이미지)에서의 객체 어노테이션
  - 객체는 사람, 소화기, 소화전, 차량, 자전거 및 오토바이의 6가지로 한정함
  - 승용차, 승합차, 버스 및 트럭 등은 모두 차량으로 어노테이션함
- 개인정보 보호를 위하여 사람의 얼굴, 차량 번호판 등은 흐리게 처리함

### 2-2. 어노테이션 정보
- 각 객체의 클래스 ID, 객체 ID, 겹침 및 잘림 여부
- 하나의 클립에 등장하는 전체 객체 수를 클래스별로 중복 없이 계수하여 라벨링함

### 2-3. 어노테이션 방법
- 바운딩 박스 조건
  - 바운딩 박스 단축 크기가 최소 25px 이상인 경우만 객체로 인정함
  - 하나의 객체에 하나의 박스만 사용
  - 객체의 일부가 박스 영역을 벗어나지 않음
  - 바운딩 박스의 여백을 최소화함

- 대상이 겹치거나 잘리더라도 정해진 크기 기준을 만족하면 객체로 인정함
- 하나의 클립 내 동일한 객체가 여러번 등장할 경우, 동일한 객체 ID를 부여함

### 2-4. 데이터 구조
- 비디오 클립명으로 된 70개의 폴더는 각각, image 폴더, mp4 파일 및 json 파일로 구성되어 있음
  - image 폴더  
    - 폴더명: image
    - 하나의 비디오 클립을 나타내는 450개의 연속된 이미지 파일들로 구성되어 있음
    - 각 이미지 파일명: {비디오 클립명}_{프레임 시퀀스}.jpg
        
  - mp4 파일
    - 파일명: {비디오 클립명}.mp4
    - 해당 클립의 동영상 파일
      
  - json 파일
    - 파일명: {비디오 클립명}.json
    - 해당 클립의 어노테이션 결과 파일
    - 동영상에 등장하는 객체의 수와 각 프레임 별 객체의 바운딩 박스 좌표, 겹침 및 잘림 여부 등이 기록되어 있음    
    - 예시
    ```json
    {
    "0525_V0051": {
        "videos": {
            "id": "00001",
            "class_Count": [
                6,
                0,
                0,
                7,
                2,
                1
            ],
            "images": [
                {
                    "id": "00000",
                    "objects": [
                        {
                            "id": "00000",
                            "class_ID": "c_1",
                            "position": [
                                821,
                                64,
                                910,
                                291
                            ],
                            "obsecured": "False",
                            "truncated": "False"
                        },
                        {
                            "id": "00001",
                            "class_ID": "c_4",
                            "position": [
                                1859,
                                34,
                                1920,
                                205
                            ],
                            "obsecured": "False",
                            "truncated": "True"
                        },
                        ...
  
---

## 3. 데이터셋 통계
- 해당 표는 본 저장소의 데이터 통계로서, 전체 통계 및 상세 내용은 [데이터셋통계.xlsx](123)을 참고할 것
---
- 객체 통계


객체 | 클래스 아이디 | 객체 수
:------ | :---: | :---:
Person(사람) | c_1 | 0
Fire Extinguisher(소화기) | c_2 | 0
Fire Hydrant(소화전) | c_3|0
Car(차량) | c_4 | 0
Bicycle(자전거) | c_5 | 0
Motorcycle(오토바이) | c_6 | 0
합계 |  | 0

---

## 4. 데이터 구조

---

## 5. 알림
- 본 데이터셋은 과학기술정보통신부의 인공지능산업원천기술개발 사업(과제번호: 2019-0-01763)의 일환으로 구축되었으며, 공개 S/W로 제공됨
- 데이터셋은 대용량 다운로드를 고려하여 참여 업체당 1개씩, 총 3개의 저장소로 분리하여 저장하였으며, 각 저장소 마다 70개씩 전체 210개의 비디오 클립이 있음
- 본 저장소에는 71번째부터 140번째까지의 70개 비디오 클립에 대한 데이터셋이 저장되어 있음.
- 저장소 1 링크: [https://github.com/laonbud-grandsys/drone-vis-recog-datasets-1](https://github.com/laonbud-grandsys/drone-vis-recog-datasets-1)
- 저장소 3 링크: [https://github.com/MTCom-AI/drone-vis-recog-datasets-3](https://github.com/MTCom-AI/drone-vis-recog-datasets-3)
