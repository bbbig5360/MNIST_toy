# MNIST_toy

### 1차 목표 : 검은 배경에 흰색 글씨의 이미지를 입력하면 모델의 정확도만큼의 정확도 나오도록 처리과정 구성
### 2차 목표 : 배경과 구분되는 색의 숫자 이미지를 입력하면 숫자 검출

## 1차 목표를 위한 여정

- 시작 : MNIST 데이터를 이용해 모델 제작
  - Dense만을 이용해 1차원 데이터로 학습
  - 결과 : Accuracy와 Loss는 괜찮았지만 실제 이미지 입력해서 나온 결과값이 좋지 않은 현상 발생
  - 개선 방안 : 1차원 -> 2차원 또는 3차원으로 변경해 이미지의 특정을 이용해 학습시킬 예정
  
- 1차 개선 : Grayscale한 이미지를 학습(28,28,1)시켜 추후 RGB입력까지 가능할 수 있도록 모델 구성
  - Accuracy와 Loss는 괜찮았지만 실제 이미지 입력해서 나온 결과값이 여전히 좋지 않은 결과 발생
  - 개선 방법 
    - ReLU -> LeakyReLU로 변경. alpha=0.1
    - Dropout : 0.1 -> 0.05로 변경
    - 신경망의 길이와, 넓이 조정
  - 결과
    - 실제 이미지를 입력했을 때 이전보다 훨씬 좋은 결과값 도출.( 컴퓨터 숫자에서 40~50% -> 80~90% )
    - 하지만 여전히 테스트돌린 99%에 미치지 못해 전처리과정을 추가하여 성능 조정 예정
    
- 2차 개선 : 큰 이미지 -> (28,28)의 작은 사이즈로 변환할 때 생기는 픽셀의 깨짐현상을 보정할 것
  - 블러링 처리 : 너무 작은 이미지여서 필터 사이즈가 조금만 커져도 이미지 훼손 심각
  - 블러링 + 샤프닝 : 실제 눈으로 봤을 경우엔 괜찮으나 실제 성능에는 영향을 주지 못함
  
 
# 계속 개선 중
