# Hand Gesture

웹캠을 활용하여 손 제스처를 인식하고, 가위바위보 동작을 실시간으로 출력하는 프로젝트입니다.
MediaPipe를 이용해 손의 랜드마크를 추출하고, KNN 알고리즘으로 제스처를 분류합니다.

---

## 주요 기능

* 웹캠을 통한 실시간 손 인식
* 손 관절 각도 기반 제스처 분석
* KNN 모델을 활용한 제스처 분류
* 가위/바위/보 텍스트 출력
* 손 랜드마크 시각화

---

## 사용 기술

* Python
* OpenCV (`cv2`)
* MediaPipe
* NumPy
* KNN (OpenCV ML)

---

## 프로젝트 구조

```
project/
│
├── data/
│   └── gesture_train.csv   # 제스처 학습 데이터
│
├── main.py                 # 실행 파일
└── README.md
```

---

## 설치 방법

```bash
pip install opencv-python mediapipe numpy
```

---

## 실행 방법

```bash
python main.py
```

* 실행 후 웹캠이 켜집니다.
* 손을 화면에 비추면 제스처가 인식됩니다.
* `q` 키를 누르면 종료됩니다.

---

## 동작 원리

1. **손 랜드마크 추출**

   * MediaPipe를 이용해 21개의 손 좌표 추출

2. **벡터 계산**

   * 관절 간 벡터를 계산하고 정규화

3. **각도 계산**

   * 벡터 간 내적을 이용해 각도(15개) 추출

4. **KNN 분류**

   * 학습 데이터(`gesture_train.csv`) 기반으로 제스처 예측

---

## 제스처 종류

| Label     | 의미    |
| --------- | ----- |
| fist      | 주먹    |
| one       | 숫자 1  |
| two       | 숫자 2  |
| four      | 숫자 4  |
| five      | 숫자 5  |
| rock      | 바위    |
| spiderman | 스파이더맨 |
| yeah      | 브이    |
| ok        | OK    |

---

## 주의사항

* `gesture_train.csv` 파일이 필요합니다.
* 카메라 번호(`VideoCapture(1)`)는 환경에 따라 `0`으로 변경해야 할 수 있습니다.
* 조명이나 손 위치에 따라 인식 정확도가 달라질 수 있습니다.

---

## 결과 예시

* 손을 펼치면 → `FIVE`
* 주먹 → `FIST`
* 브이 → `TWO`
