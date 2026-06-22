## Replicator 기본 개념과 사용법, 나만의 데이터로 YOLO 모델 훈련하기

26/06/18  (3개 강의)

- YOLOv11 학습용 자동 레이블링 데이터셋 구축 -2
- 나만의 데이터로 YOLO 모델 훈련하기
- YOLOv11 전이 학습 및 성능 시각화 - Bounding Box

## 오늘의 학습 목표 

- YOLO 아키텍처의 이해
- 객체 탐지 모델의 성능 평가 지표
- 전이 학습 (Transfer Learning)
- Ultralytics 프레임워크

## Algorithm vs. Framework 

### YOLO (Algorithm)

- 정의: 객체 탐지를 위한 독창적인 신경망 아키텍처 및 방법론.
- 철학: "You Only Look Once" 라는 개념하에 객체 탐지를 단일 회귀(Regression) 문제로 재구성.
- 핵심: Grid-based Prediciton, Bounding Box Regression, Class Probability Estimation.

### Ultralytics (Framework)

- 정의: YOLO 알고리즘을 PyTorch 기반으로 구현한 고성능 SDK (Software Development Kit)
- 역할: 추상화된 알고리즘을 실제 훈련, 검증, 배포가 가능한 엔지니어링 도구로 구체화.

---



## YOLO Architecture (2): Confidence Score

각 예측 Bounding Box는 Confidence Score를 통해 예측의 유효성을 평가
Confidence = Pr(Object) x IoU truth pred

### 구성 요소

- Pr(Object): Bounding Box 내에 객체가 존재할 확률
- IoU truth pred: 예측된 Box와 실제 Ground Truth Box 간의 Intersection over Union

Confidence Score는 해당 예측이 '객체를 포함하는가'와 '위치가 정확한가'를 동시에 고려하는 정량적 지표로 기능

### Key Conclusions

- YOLO는 Unified Detection을 통해 속도와 효율성을 확보한 One-Stage Detector 입니다.
- 모델의 평가는 mAP, Latency 등 다차원적 지표를 통해 종합적으로 이루어져야 합니다.
- 제한된 데이터 환경에서는 전이 학습(Fine-tuning)이 가장 효과적인 훈련 전략 입니다.
- Ultralytics는 YOLO 알고리즘을 효율적으로 구현할 수 있는 강력한 프레임워크 입니다.
