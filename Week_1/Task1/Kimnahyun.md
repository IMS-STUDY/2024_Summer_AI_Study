# 인공지능 1주차 과제

- ~~딥러닝 기초~~
    - ~~딥러닝 개요~~
        - ~~MLP란?~~
    - ~~합성곱 연산~~
    - ~~비용함수란?, 손실함수란?~~
    - ~~과적합이란?~~
        - ~~방지 방법~~
- ~~pytorch 다루기~~
    - ~~환경설정~~
    - ~~pytorch 구성요소, 문법, 특징~~
- ~~데이터 전처리~~
    - ~~데이터 전처리란?~~
    - ~~데이터 전처리 목적성~~
    - ~~데이터 전처리 절차 및 방법~~
    - ~~데이터 전처리 기초 문법 (시각화는 안보셔도 됩니다.)~~
- ~~코랩 사용법~~

## 1. 딥러닝 기초

### **1) 딥러닝 개요**

- 딥러닝이란?

→ 머신러닝의 한 분야로, 신경망을 사용하여 인간에게 자연스러운 학습 방법, 즉 예시를 통해 배우는 방식으로 컴퓨터가 학습하게 하는 방법이다. 딥러닝에서 모델은 영상, 텍스트 또는 소리 등의 데이터에서 직접 분류 또는 회귀 작업을 수행하는 방법을 학습한다.

 딥러닝 모델은 신경망 아키텍처 기반. 여기서 신경망 아키텍처는 인간의 뇌에서 뉴런이 서로 신호를 주고받는 방식에서 영감을 받은 일종의 머신러닝 접근법이다. 

→ 신경망은 분류 또는 회귀 작업에서 모두 사용할 수 있으며 모델 파라미터는 훈련 데이터를 **학습**하여, 신경망에 가중치를 부여하는 방식으로, 일반적으로 가중치를 최적화하여 예측 오차를 최소화하는 방식을 통해 설정된다.

![일반적인 신경망 아키텍처](https://blog.kakaocdn.net/dn/cgET4W/btsIhOqqRin/SuBpkbNeTvuVIv9fvUjYcK/tfile.svg)

일반적인 신경망 아키텍처

- 머신러닝이란?

→ 주어진 데이터 집합에 대한 예측을 하는데 사용되는 메커니즘. 머신러닝 모델은 데이터에서 직접 정보를 학습하는 식으로 이루어지고, 알고리즘은 제공되는 입력데이터와 데이터에 대한 출력을 가지고 머신러닝 모델을 훈련시켜 새 데이터에 대한(실제 데이터에 대한) 출력을 예측한다.

머신 러닝의 종류는 두 가지 주요 유형이 있는데 각각 분류와 회귀가 존재한다. 분류라는 출력값이 클래스 집합에 속하는 경우와 (특정 집단에 분류, 속하게 됨) 회귀라는 출력값이 연속적인 경우를 각각 의미한다.

회귀 예시)

![https://blog.kakaocdn.net/dn/VQPni/btsIiQgxfFe/Z9HPI3zGhaBFM0sp8mVTX1/img.png](https://blog.kakaocdn.net/dn/VQPni/btsIiQgxfFe/Z9HPI3zGhaBFM0sp8mVTX1/img.png)

![https://blog.kakaocdn.net/dn/bIxU79/btsIhURrKi8/tjvHX72XFKIkv4HE0iu9pK/img.png](https://blog.kakaocdn.net/dn/bIxU79/btsIhURrKi8/tjvHX72XFKIkv4HE0iu9pK/img.png)

이걸 보면 우리는 2020.1.8의 판매량을 예상할 수 있다. 그리고 보통 이렇게 숫자관련된 데이터는 보통 회귀를 많이 사용한다. 회귀는 이렇듯 예측하고 싶은 결과가 숫자인 경우에 사용된다.

분류 예시)

![Untitled](https://github.com/IMS-STUDY/AI-Study/assets/127017020/74a88c01-8340-48da-aff8-17642f8ec915)

![Untitled 1](https://github.com/IMS-STUDY/AI-Study/assets/127017020/9526a4f8-5847-4037-8562-7eab27631e31)

분류는 이렇게 결과값이 문자같은 걸로 표현될 때 사용된다. 

추가로, 양적 데이터는 숫자로 취급하여 회귀. 범주 데이터는 분류를 사용한다.  

다시 딥러닝으로 돌아가면, 딥러닝 모델은 레이블에 지정된 대규모 데이터셋을 사용하여 훈련되며, *수작업*으로 특징 추출을 수행할 필요 없이 데이터에서 직접 특징을 학습할 수 있다. 

![Untitled 2](https://github.com/IMS-STUDY/AI-Study/assets/127017020/a42032df-887c-4862-af6c-b2f14571b780)

딥러닝과 머신러닝, 인공지능은 이런 구조.

추가로, 딥러닝 모델의 유형은 총 3가지로, CNN/RNN/트랜스포머 모델이 존재한다. 

간단하게 이 세가지를 정리해보자면 **CNN**은 합성곱 연산, Pooling 계층 등을 이용해 영상과 같은 2차원 데이터 처리에서 직접 특징을 추출하는 방식으로 작동한다. 아래에 설명할 MLP와 다른점은 기존의 MLP에서는 공간적 특성이 무시되는 문제점을 CNN을 통해 개선시켰다는 점이다.

RNN은 시계열 또는 순차 데이터를 예측하는 딥러닝의 신경망 아키텍처다. RNN은 자연 신호 분류, 언어 처리, 비디오 분석 등의 문제를 해결하는 데 특히 효과적이다. (시간, 시계열 데이터 처리 특화이기 때문.) 인코더-디코더 구조로 되어있음도 알아두자.

LSTM 신경망은 RNN이 시간의 흐름에 따라 기존 정보를 잃어버린다는 점을 개선시키기 위해 메모리를 추가한 방식으로, 단순한 RNN과 비교하여 장기 종속성(기억력)에 대한 학습력이 더 우수한 유형의 RNN이라고 볼 수 있다.

트랜스포머는 순차 데이터에서 관계를 추척하도록 설계되었다. 여기서 사용되는 것이 바로 attention이라는 개념인데, 이 attention을 통해 인코더-디코더 구조에 추가로 데이터 사이의 유사성을 분석할 수 있게 된다. 이런 입력과 출력 사이의 전역 종속성(유사성)을 수집하기 위해 self-attention을 활용하는데, (Q,K,V 값 존재.) 이로써 트랜스포머는 자연어 처리에 사용되는 경우가 많으며, BERT 및 ChatGPT와 같은 LLM(대규모 언어모델)의 기반이 된다.  

- (추가자료) 트랜스포머 논문 정리
    
    [2022156007_김나현_트랜스포머.pdf](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%201%E1%84%8C%E1%85%AE%E1%84%8E%E1%85%A1%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A6%207808855968fb47c7b171f74ea8af5eb0/2022156007_%25EA%25B9%2580%25EB%2582%2598%25ED%2598%2584_%25ED%258A%25B8%25EB%259E%259C%25EC%258A%25A4%25ED%258F%25AC%25EB%25A8%25B8.pdf)
    

 

- MLP란?

→ MLP란 지도학습에 사용되는 인공 신경망의 한 형태이다. MLP는 일반적으로 최소 하나 이상의 비선형 은닉 계층을 포함하며, 이러한 계층은 학습 데이터에서 복잡한 패턴을 추출하는 데 도움이 된다. MLP는 주로 분류 및 회귀 문제에 적용되며, 그 학습 알고리즘으로는 **역전파**가 주로 사용된다. 

 MLP는 입력 계층, 하나 이상의 은닉 계층, 그리고 출력 계층으로 구성된다.  각 계층은 노드(또는 뉴런)로 구성되며, 이들은 다음 계층에 있는 노드로 완전히 연결되어 있다. MLP의 핵심 개념은 “깊이” 혹은 “층”에 있는데, 이는 복잡한 패턴을 학습하는 데 필요한 노드의 개수와 결합의 복잡성을 증가시킨다. 

### **2) 합성곱 연산**

- 합성곱 연산이란?

→ CNN의 합성곱층에서 사용되는 연산으로, 이 합성곱 연산을 통해서 **이미지의 특징을 추출**하는 역할을 한다. 

합성곱의 연산은 **커널 또는 필터**라고 하는 n*m 크기의 행렬로 높이*너비 크기의 이미지를 처음부터 끝까지 겹치며 훑으면서 n*m 크기의 겹쳐지는 부분의 각 이미지와 커널의 원소 값을 곱해서 모두 더한 값을 출력으로 하는 것을 말한다. 이때, 이미지의 가장 왼쪽 위부터 가장 오른쪽 아래까지 순차적으로 훑는 과정을 거친다. 

아래는 그림과 예제를 통해 이해해보도록 하자.

![conv4](https://github.com/IMS-STUDY/AI-Study/assets/127017020/15b03e17-2d42-4f62-8ec4-42ca661659ba)

커널(필터)는 일반적으로 3*3 혹은 5*5를 사용한다.

합성곱은 이러한 계산과정을 거친다.

이 과정을 코드로 구현해보면 이러한 코드를 작성할 수 있다.

```python
image_height, image_width = image.shape #이미지의 크기
filter_height, filter_width = filter.shape #필터(커널)의 크기

#결과값을 담을 특징맵(feature map)의 크기 지정
output_image = np.zeros((image_height - filter_height +1, image_width - filter_width +1))

#for문을 돌며 합성곱의 결과를 output_image에 담는다.
for i in range(image_height - filter_height + 1):
	for j in range(image_width - filter_width + 1):
		output_image[i, j] = np.sum(image[i:i+filter_height, j:j+filter_width] * filter)
```

 위와 같이 입력으로부터 커널을 사용하여 합성곱 연산을 통해 나온 결과를 특성 맵(feature map)이라고 한다.

 여기에 추가로 입력에 있어서 커널이 이동하는 step을 설정할 수 있는데 이 step을 **스트라이드(stride)**라고 한다. 

![conv9](https://github.com/IMS-STUDY/AI-Study/assets/127017020/731e761b-e715-4afd-88be-5643b9ea173b)

스트라이드를 지정한 입력과 커널의 특징맵 추출 과정

스트라이드가 있는 경우또한 코드로 작성해보겠다. 

```python
stride = 2 #stride가 2인 경우
image_height, image_width = image.shape #이미지의 크기
filter_height, filter_width = filter.shape #필터(커널)의 크기

#stride가 존재하기 때문에 나누기를 통해 feature map의 크기를 계산.
output_height = (image_height - filter_height) // stride + 1
output_width = (image_width - filter_width) // stride + 1

output_image = np.zeros((output_height, output_width)) #특징맵 크기 설정

#range(n,m,k) -> n부터 m-1까지 k만큼의 step을 가짐.
for i in range(0, image_height - filter_height + 1, stride):
	for j in range(0, image_width - filter_width + 1, stride):
		#i와 j의 값이 stride 배 만큼 커지기 때문에 그만큼 값을 나눠줘야함.
		output_image[i // stride, j // stride] = np.sum(image[i:i+filter_height, j:j+filter_width] * filter)
```

- 가중치와 편향

이 합성곱에서 필터(커널)은 결국 MLP의 가중치를 의미하는 것과 같다. 

![conv13](https://github.com/IMS-STUDY/AI-Study/assets/127017020/8cc43500-fab0-4f26-80cc-f1c6b31688ae)

이러한 특징은 CNN에서는 더 적은 가중치 수로 공간적 구조 정보를 보존한다는 특징이 있다.

추가로, 편향을 구현하기 위해서는 합성곱을 진행하고 나온 결과값에 편향 값을 더해주기만 하면된다.

![conv14](https://github.com/IMS-STUDY/AI-Study/assets/127017020/211f2298-1276-4964-9dbe-03acb295cb2e)

편향은 하나의 값만 존재.

- 패딩

패딩은 합성곱 연산 이후에도 특성 맺의 크기가 입력의 크기와 동일하게 유지되도록 하기위해 사용된다. 

![conv10](https://github.com/IMS-STUDY/AI-Study/assets/127017020/53a44c30-59f1-4fc0-b486-f40fb2572e03)

가장 간단한 zero padding

패딩은 합성곱 연산을 하기 전에 입력의 가장자리에 지정된 개수의 폭만큼 행과 열을 추가해주는 것을 의미한다. 지정된 개수의 폭만큼 테두리를 추가하고, 주로 값을 0으로 채우는 제로 패딩을 사용한다. 

### **3) 비용함수와 손실함수**

- 손실&비용함수란?

 = 머신 러닝에서 ‘손실’은 예측 값과 실제 값의 차이를 이해하는데 도움을 준다. 

= 실제 y값에 비해 가정한 모델의 출력값이 얼마나 잘 예측했는지 판단하는 함수며, 이렇게 훈련 단계에서 손실을 단일 실수 형태로 정량화하는데 사용되는 함수를 손실 함수라고 한다.

- 손실함수 : 한 개의 데이터 포인트에서 나온 오차를 최소화하기 위해 정의되는 함수.

→ ex. SE(제곱오차) / AE(절대 오차) / log loss(비용함수 형태로도 사용)

- 비용함수 : 모든 오차를 일반적으로 최소화하기 위해 정의되는 함수.

→ ex. MSE(평균 제곱 오차) / MAE(평균 절대 오차) / Binary Cross-Entropy / Multinomial-logloass 

왜 손실&비용 함수를 사용하는 것일까?

![신장 및 체중에 대한 산점도](https://miro.medium.com/v2/resize:fit:231/0*I49TAeMj_XjV31DB.png)

신장 및 체중에 대한 산점도

![분류 문제의 가능한 솔루션](https://miro.medium.com/v2/resize:fit:582/0*pfCimErPK1MM1eZr.JPG)

분류 문제의 가능한 솔루션

= 기본적으로 세 가지 분류기 모두 정확도가 매우 높지만 세 번째 솔루션은 어떤 지점도 잘못 분류하지 않기 때문에 가장 좋다. 

모든 지점을 완벽하게 분류하는 과정에서 비용함수의 개념이 쓰이는 것이다. 바로, 비용함수를 통해 최적의 솔루션을 판단할 수 있고, 즉, **비용함수란 “알고리즘/모델의 성능”을 평가하는 기술**이다.

- 비용함수의 종류
1. 회귀 비용 함수
2. 이진 분류 비용 함수
3. 다중 클래스 분류 비용 함수

1. **회귀 비용 함수**

: 회귀 모델은 직원의 급여, 자동차 가격 등 연속적인 값(숫자)을 예측하는 것을 다룬다. 이런 회귀 문제에서 사용되는 비용함수를 “회귀 비용 함수”라고 한다. 

**1.1 평균 오차(ME)**

- 각 훈련 데이터에 대한 오차가 계산된 다음 모든 오차의 평균값이 도출된다.
- 오차의 평균을 계산하는 방법은 다른 방법들 중 가장 직관적인 방법이다.
- 오류는 음수와 양수가 전부 가능하며 , 따라서 총합을 구하는 과정에서는 모델에 따라서 평균 오류가 0이 되는 문제가 발생할 수도 있다.

**1.2 평균 제곱 오차(MSE)**

![1_mAcMWhOZkBk_UGXgbTl68Q.webp](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%201%E1%84%8C%E1%85%AE%E1%84%8E%E1%85%A1%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A6%207808855968fb47c7b171f74ea8af5eb0/1_mAcMWhOZkBk_UGXgbTl68Q.webp)

- 평균 오차의 단점을 개선한 ㅎ마수로, 실제 값과 예측 값의 차이의 제곱을 계산하여 음수값을 방지한다.
- 이는 예측값과 실제 출력값의 차이를 제곱한 값들의 평균으로 측정된다.
- 작은 편차에도 민감하게 반응한다는 점이 있지만 그만큼 데이터 셋에 이상치가 존재하는 경우 오차가 몇 배는 더 커지는 문제가 있다.

**1.3 평균 절대 오차(MAE)**

![1_K7eGZjXIup312GuvJnyPyw.webp](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%201%E1%84%8C%E1%85%AE%E1%84%8E%E1%85%A1%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A6%207808855968fb47c7b171f74ea8af5eb0/1_K7eGZjXIup312GuvJnyPyw.webp)

- 예측값의 절대 차이를 계산하여 음수값을 방지한다.
- 이 비용함수에서 MAE는 예측과 실제 관찰 간의 절대 차이의 합의 평균으로 측정된다.
- 이상치에 강하므로, 데이터 셋에 노이즈나 이상치가 있는 경우 더 나은 결과를 제공한다.

** **이상치 : 데이터 세트에서 다른 관찰값들과 크게 다른 값을 가진 관찰 결과**

1. **분류 문제에 대한 비용 함수**

: 분류 문제는 회귀 문제에서 사용하는 비용함수와 다르다. 분류에 일반적으로 사용되는 손실함수는  Cross-entropy loss로,  cross-entropy는 예측된 확률 분포가 실제 분포에서 얼마나 떨어져있는지 계산하는 도구다. 

![이 그림을 통해 이해하면 더 쉽다. ](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%201%E1%84%8C%E1%85%AE%E1%84%8E%E1%85%A1%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A6%207808855968fb47c7b171f74ea8af5eb0/1_J7tFGJ8o7JfHDYZPAn9_rQ.webp)

이 그림을 통해 이해하면 더 쉽다. 

### 4) 과적합

- **과적합이란?**

= 머신러닝에서 학습 모델이 학습 데이터에 지나치게 잘 맞춰져, 새로운 데이터에 대해 일반화하는 능력이 떨어지는 현상을 의미한다. 

과적합된 모델은 학습 데이터의 노이즈나 불필요한 세부 사항까지 학습해버려, **실제 데이터나 검증 데이터셋에서는 성능이 저하**될 수 있다. 이는 모델이 학습 데이터의 특정 패턴을 너무 자세히 학습하여, 일반적인 실제 결과를 확인하는 데 실패하게 되는 것이다.

과적합은 특히 모델이 너무 복잡하거나 학습 데이터가 제한적인 경우에 자주 발생한다. 복잡한 모델은 많은 수의 매개변수를 가지고 있어 더 미묘한 패턴을 학습할 수 있지만, 이로 인해 학습 데이터에만 특화되어 새로운 데이터에 대한 예측 능력이 떨어질 수 있다. 

반면, 간단한 모델은 과적합의 위험이 적지만, 이 경우 모델이 학습 데이터의 중요한 특성을 충분히 학습하지 못하는 underfitting 문제가 발생할 수 있다. 

이러한 과적합을 방지하기 위한 방법으로는 **교차검증, 정규화, 데이터셋의 크기 증가, 조기 종료** 등이 있다. 이러한 방법들은 모델의 복잡성을 조절하거나, 학습 과정을 적절히 제한하여 모델이 학습 데이터에 지나치게 최적화되는 것을 방지한다. 

- **과적합 방지**
1. **데이터의 양을 늘리기**

: 모델은 데이터 양이 적을 경우, 해당 데이터의 특정 패턴이나 노이즈까지 쉽게 암기하게 되므로, 과적합 현상이 발생할 확률이 늘어난다. 그렇기 때문에 데이터의 양을 늘릴 수록 모델은 데이터의 일반적인 패턴을 학습하여 과적합을 방지할 수 있다.

만약, 데이터의 양이 적을 경우에는 의도적으로 기존의 데이터를 조금씩 변형하고 추가하여 데이터의 양을 늘리기도 하는데, 이를 데이터 증식 또는 증강(**Data Augmentation**)이라고 합니다. 

- 이미지의 경우 이미지를 돌리거나 노이즈 추가, cropping, 일부분 수정 등으로 데이터를 증식시킴.
- 텍스트 데이터의 경우, 데이터를 증강하는 방법으로 번역 후 재번역을 통해 새로운 데이터를 만들어내는 역번역 등의 방법이 있음.

1. **모델의 복잡도 줄이기**

: 인공 신경마으이 복잡도는 은닉층의 수나 매개변수의 수 등으로 결정된다. 과적합 현상이 포착되었을 때, 인공 신경망 모델에 대해서 할 수 있는 한 가지 조치는 인공 신경망의 복잡도를 줄이는 것이다.

 **= 인공 신경망에서는 모델에 있는 매개변수들의 수를 모델의 수용력이라고 하기도 한다.**

1. **가중치 규제 적용하기**

: 복잡한 모델이 간단한 모델보다 과적합될 가능성이 높다. 그리고 간단한 모델은 적은 수의 매개변수를 가진 모델을 말한다. 복잡한 모델을 좀 더 간단하게 하는 방법으로 가중치 규제가 있다.

![Untitled 3](https://github.com/IMS-STUDY/AI-Study/assets/127017020/453bd16b-0966-481b-aa31-127da647ab29)

- L1 규제 : 가중치 w들의 절대값 합계를 비용함수에 추가한다. L1 노름이라고도 한다.
- L2 규제 : 모든 가중치 w들의 제곱합을 비용함수에 추가한다. L2 노름이라고도 한다.

```python
# L1, L2 Norm
def norm(A, order={1, 2}):
    # L1 Norm
    if order == 1:
        return np.sum(np.abs(A))
    
    # L2 Norm
    elif order == 2:
        return np.sqrt(np.sum(np.square(A)))
    
    # exception handling (예외 처리)
    else:
        raise ValueError("Invalid order. Choose from 1, 2.")
```

예를 들어 𝐻(𝑋)=𝑤1𝑥1+𝑤2𝑥2+𝑤3𝑥3+𝑤4𝑥4 라는 수식이 있다고 할 때,  여기에 L1 규제를 사용하였더니, 𝑤3 의 값이 0이 되었다고 하자. 이는 𝑥3 특성은 사실 모델의 결과에 별 영향을 주지 못하는 특성임을 의미한다.

L2규제는 L1과는 달리 가중치들의 제곱을 최소화하기 때문에 w의 값이 완전히 0이 되기보다는 0에 가까워지는 경향을 띈다. 

이런식으로 비용함수가 최소가 되게하는 가중치와 편향을 찾는 동시에 가중치들의 절대값의 합도 최소가 되어야한다. 이렇게 되면, 가중치 w의 값들은 0또는 0에 가까이 작아져야 하므로, 어떤 특성들은 모델을 만들 때 거의 사용되지 않게 할 수 있다.

1. **드롭 아웃**

드롭 아웃은 학습 과정에서 신경망의 일부를 사용하지 않는 방법이다. 

![드롭아웃.png](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%201%E1%84%8C%E1%85%AE%E1%84%8E%E1%85%A1%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A6%207808855968fb47c7b171f74ea8af5eb0/%25EB%2593%259C%25EB%25A1%25AD%25EC%2595%2584%25EC%259B%2583.png)

위의 그림은 드롭 아웃 전과 후의 신경망을 비교하고 있는 그림으로, 예를 들어 드롭 아웃의 비율을 0.5로 한다면 학습과정마다 랜덤으로 절반의 뉴런을 사용하지않고 절반의 뉴런만을 사용한다. 

드롭 아웃은 신경망 학습 시에만 사용하고 예측 시에는 사용하지 않는 것이 일반적이다. 학습 시에 인공 신경망이 특정 뉴런 또는 특정 조합에 너무 의존적이게 되는 것을 방지해주고, 매번 랜덤 선택으로 뉴런들을 사용하지 않으므로, 서로 다른 신경망들을 앙상블하여 사용하는 것과 같은 효과를 내어 과적합을 방지한다.

ex) 케라스에서 드롭아웃 코드

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dropout, Dense

max_words = 10000
num_classes = 46

model = Sequential()
model.add(Dense(256, input_shape=(max_words,), activation='relu'))
model.add(Dropout(0.5)) # 드롭아웃 추가. 비율은 50%
model.add(Dense(128, activation='relu'))
model.add(Dropout(0.5)) # 드롭아웃 추가. 비율은 50%
model.add(Dense(num_classes, activation='softmax'))
```

---

## 2. pytorch 다루기

### 1) 환경설정

: anaconda 설치 → 가상환경 설정 → 

conda version 확인 → 

```python
>conda --version
conda 4.6.4
```

conda update → 

```python
>conda update conda
Collecting package metadata : done
Solving environment : 
....
```

가상환경 생성 →

```python
>conda create --name(or --n) 가상환경이름 설치할 패키지
 
# 예시1 : python 3.6버전으로 하고 가상환경 이름은 pytest로 하는 가상환경 생성
>conda create --name pytest python=3.6
# 예시2 : python 3.5버전으로 하고 가상환경 이름은 pytest2로 하는 가상환경 생성
>conda create --n pytest2 python=3.5
```

패키지 설치하기 →

```python
# 가상환경 활성화 후에 진행
# 안하면 base(or root)에 패키지 설치됨
 
# 패키지 설치하기(기본)
>conda install 패키지명
 
# 패키지 설치 명령어는 보통 검색하면 나옵니다.
 
# 해당 가상환경에 설치된 패키지 목록 보기
>conda list
 
# 가상환경 캐시 정리
# 인덱스 캐시, 잠긴 파일, 사용하지 않는 패키지, 소스 캐시 등을 삭제한다
>conda clean -all(or -a)
```

가상환경 만들고 활성화 →

```python
# 가상환경 생성
>conda create -n 가상환경이름
 
# 활성화
>conda activate 가상환경이름
```

PyTorch 설치 → [https://pytorch.org/get-started/locally/](https://pytorch.org/get-started/locally/)

![image-8](https://github.com/IMS-STUDY/AI-Study/assets/127017020/635e01e0-794d-47ca-9be3-3269aa232dd6)

### 2) pytorch 구성요소, 문법, 특징

1. PyTorch란?

= 파이토치는 파이썬 기반의 오픈소스 머신러닝 라이브러리로, 간결하고 구현이 빨리되며, 텐서플로우보다 사용자가 익히기 훨씬 쉽다는 특징이 있다.

```python
import torch
import numpy as np
```

→ 파이토치 라이브러리 불러오기. 

1. PyTorch 패키지

![Untitled 4](https://github.com/IMS-STUDY/AI-Study/assets/127017020/e38c5efb-8c82-435c-9b72-2e7e435e9e23)

1. Tensors 다루기
- tensor들을 만드는 방법

```python
z = torch.zeros(5, 3)
print(z)
print(z.dtype)
```

```python
#output
tensor([[0., 0., 0.],
        [0., 0., 0.],
        [0., 0., 0.],
        [0., 0., 0.],
        [0., 0., 0.]])
torch.float32
```

위에서, 0으로 채워진 5*3 행렬을 만들고, 파이토치의 기본 타입인 0으로 채워진 32비트 부동소수점 데이터 타입인지 확인했다.

만약 정수형 데이터 타입을 원한다면 기본값의 재정의 또한 가능하다.

```python
i = torch.ones((5, 3), dtype=torch.int16)
print(i)
```

```python
#output
tensor([[1, 1, 1],
        [1, 1, 1],
        [1, 1, 1],
        [1, 1, 1],
        [1, 1, 1]], dtype=torch.int16)
```

dtype의 기본값을 변경하면 tensor가 출력될 때 데이터 타입을 확인가능하다. 

- 학습가중치 초기화

= 학습 가중치를 무작위로 초기화하는 것이 일반적이며, 종종 결과의 재현성을 위해 특정 시드로 초기화하는 경우도 있다.

```python
torch.manual_seed(1729)
r1 = torch.rand(2, 2)
print('랜덤 tensor 값:')
print(r1)

r2 = torch.rand(2, 2)
print('\n다른 랜덤 tensor 값:')
print(r2) # 새로운 2x2 행렬 값

torch.manual_seed(1729)
r3 = torch.rand(2, 2)
print('\nr1과 일치:')
print(r3) # 동일한 시드값으로 인해 r1 값이 반복되어 행렬값으로 나옵니다.
```

```python
#output
랜덤 tensor 값:
tensor([[0.3126, 0.3791],
        [0.3087, 0.0736]])

다른 랜덤 tensor 값:
tensor([[0.4216, 0.0691],
        [0.2332, 0.4047]])

r1과 일치:
tensor([[0.3126, 0.3791],
        [0.3087, 0.0736]])
```

- 산술연산

tensor는 산술 연산을 직관적으로 수행한다. 유사한 shape의 tensor들을 더하거나, 곱하거나 그 외 연산도 가능하다. 스칼라를 사용한 연산은 tensor 분산되어 나타난다.

```python
ones = torch.ones(2, 3)
print(ones)

twos = torch.ones(2, 3) * 2 # 모든 원소에 2를 곱합니다.
print(twos)

threes = ones + twos       # shape이 비슷하기 때문에 더할 수 있습니다.
print(threes)              # tensor의 원소별 더한 값이 결과로 나옵니다.
print(threes.shape)        # 입력 tensor와 동일한 차원을 가지고 있습니다.

r1 = torch.rand(2, 3)
r2 = torch.rand(3, 2)
# 런타임 오류를 발생시키려면 아래 줄의 주석을 해제합니다.
# r3 = r1 + r2
```

```python
tensor([[1., 1., 1.],
        [1., 1., 1.]])
tensor([[2., 2., 2.],
        [2., 2., 2.]])
tensor([[3., 3., 3.],
        [3., 3., 3.]])
torch.Size([2, 3])
```

- 추가적인 수학 연산 예제

```python
r = (torch.rand(2, 2) - 0.5) * 2 # -1과 1 사이의 값을 가집니다.
print('랜덤 행렬값, r:')
print(r)

# 일반적인 수학적 연산은 다음과 같이 지원됩니다:
print('\nr의 절대값:')
print(torch.abs(r))

# 삼각함수를 사용할 수 있습니다:
print('\nr의 역 사인 함수:')
print(torch.asin(r))

# 행렬식 및 특이값 분해와 같은 선형 대수 연산을 사용할 수 있습니다.
print('\nr의 행렬식:')
print(torch.det(r))
print('\nr의 특이값 분해:')
print(torch.svd(r))

# 통계 및 집합 연산 등을 사용할 수 있습니다:
print('\nr의 평균 및 표준편차:')
print(torch.std_mean(r))
print('\nr의 최대값:')
print(torch.max(r))
```

```python
#output
랜덤 행렬값, r:
tensor([[ 0.9956, -0.2232],
        [ 0.3858, -0.6593]])

r의 절대값:
tensor([[0.9956, 0.2232],
        [0.3858, 0.6593]])

r의 역 사인 함수:
tensor([[ 1.4775, -0.2251],
        [ 0.3961, -0.7199]])

r의 행렬식:
tensor(-0.5703)

r의 특이값 분해:
torch.return_types.svd(
U=tensor([[-0.8353, -0.5497],
        [-0.5497,  0.8353]]),
S=tensor([1.1793, 0.4836]),
V=tensor([[-0.8851, -0.4654],
        [ 0.4654, -0.8851]]))

r의 평균 및 표준편차:
(tensor(0.7217), tensor(0.1247))

r의 최대값:
tensor(0.9956)
```

tensor의 간단한 연산 및 예제는 이렇게 확인할 수 있다.

---

## 3. 데이터 전처리

### 1) 데이터 전처리란?

= 데이터 전처리란, 데이터 분석을 위해 수집한 데이터를 분석에 적합한 형태로 가공하는 과정이다. 

데이터 전처리를 통해 불필요한 데이터를 제거하고, 결측치나 이상치를 처리하여 데이터의 질을 향상시킬 수 있다. 이렇게 가공된 데이터는 분석 모델을 구축하고 결과를 도출하는 데에 더욱 유용하게 활용될 수 있다. 

### 2) 데이터 전처리 목적성

= 데이터 전처리의 주요 목적은 원시 데이터로부터 유용한 정보를 추출하고, 머신러닝 모델이 이를 효과적으로 학습하고 일반화할 수 있도록 데이터의 품질을 향상시키는 것이다. 

- 데이터 품질 향상
    - 결측치 처리 : 결측치는 모델의 학습을 방해하고, 결과의 정확성을 떨어뜨린다. 데이터 전처리를 통해 결측치를 적절하게 처리하여 데이터의 품질을 향상시킨다.
    - 이상치 처리 : 이상치는 모델이 잘못된 패턴을 학습하게 할 뿐만 아니라 예측을 왜곡시킬 수 있다. 따라서, 데이터 전처리는 이상치를 탐지하고 처리하여 데이터의 일관성을 유지하고 모델의 안정성을 향상시킨다.
- 모델의 성능 향상
    - 특성 공학 : 데이터 전처리는 적절한 특성을 추출하고 생성하여 모델이 더 나은 성능을 발휘할 수 있도록 한다. 도메인 지식을 활용하여 새로운 특성을 만들거나, 기존의 특성을 변형함으로써 모델이 데이터의 본질적인 패턴을 더 잘 파악할 수 있게 돕는다.
    - 스케일링 : 모델의 성능은 특성의 스케일에 영향을 받을 수 있다. 데이터 전처리는 스케일링을 통해 특성 간의 크기 차이를 줄여주고, 모델이 각 특성을 고르게 반영하도록 돕는다.
- 일반화 증진
    - 오버피팅 방지 : 모델이 특정 데이터에 지나치게 적응하는 것을 방지하여 일반화 능력을 향상시킨다. 데이터 증강, 드롭아웃, 정규화 등의 기법을 활용하여 모델이 새로운 데이터에 더 잘 대응할 수 있도록 돕는다.
    - 클래스 불균형 다루기 : 분류 문제에서 클래스 간의 불균형은 모델의 학습을 방해할 수 있다. 데이터 전처리는 클래스 불균형을 다루어 모델이 각 클래스를 골고루 학습하게 돕는다.
    

### 3) 데이터 전처리 절차 및 방법

= 데이터 전처리는 다양한 단계로 구성되며, 각 단계는 데이터의 품질을 향상시키고 모델의 성능을 개선하는 데 기여한다.

![데이터-전처리-3.png](%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%B5%E1%84%82%E1%85%B3%E1%86%BC%201%E1%84%8C%E1%85%AE%E1%84%8E%E1%85%A1%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A6%207808855968fb47c7b171f74ea8af5eb0/%25EB%258D%25B0%25EC%259D%25B4%25ED%2584%25B0-%25EC%25A0%2584%25EC%25B2%2598%25EB%25A6%25AC-3.png)

- 결측치 처리
    - 삭제 : 결측치가 존재하는 행 또는 열을 삭제하는 방법. 주로 결측치의 수가 상대적으로 적을 때 사용된다.
    - 대체 : 결측치를 다른 값으로 대체하는 방법이다. 평균, 중앙값, 최빈값 등을 활용하여 결측치를 대체할 수 있다.
    - 보간  : 시계열 데이터와 같이 연속적인 값에서 사용되며, 주어진 데이터의 패턴을 기반으로 결측치를 추정한다.
- 이상치 처리
    - 통계적 방법 : 평균과 표준편차를 이용하여 데이터의 분포를 고려하고, 특정 범위를 벗어나는 데이터를 이상치로 간주하여 처리한다.
    - IQR 기반 : 제 1 사분위수 제 3 사분위수를 이용하여 IQR을 계산하고, 일정 범위를 벗어나는 데이터를 이상치로 간주한다.
- 특성 공학
    - 다항 특성 추가 : 기존의 특성을 이용하여 새로운 특성을 생성한다. 주로 회귀모델에서 사용되며, 다항 회귀를 구성하는 데 활용된다.
    - 상호 작용 특성 추가 : 두 특성 간의 상호작용을 나타내는 새로운 특성을 생성한다. 두 특성의 조합이 결과에 미치는 영향을 고려하는데 사용된다.
- 스케일링
    - 표준화 : 데이터의 평균을 0으로, 표준편차를 1로 변환하여 스케일을 조정한다.
    - 정규화 : 데이터의 범위를 [0,1] 또는 [-1,1]로 변환하여 스케일을 조정한다.
- 일반화 증진
    - 데이터 증강 : 기존 데이터를 활용하여 새로운 데이터를 생성한다.  주로 이미지나 텍스트 데이터에서 사용되며 모델의 일반화 능력을 향상시킨다.
    - 드롭아웃 : 위에서 한 번 설명한 방법.

### 4) 데이터 전처리 기초 문법 (시각화는 안보셔도 됩니다.)

**4.1 결측치 처리**

- 삭제(Deletion)

```python
# 결측치가 있는 행 삭제
df.dropna(inplace=True)
```

- 대체(Imputation)

```python
# 결측치를 평균값으로 대체
mean_value = df['column_name'].mean()
df['column_name'].fillna(mean_value, inplace=True)	
```

- 보간(Interpolation)

```python
# 선형 보간을 사용하여 결측치 보간
df['column_name'].interpolate(method='linear', inplace=True)
```

**4.2 이상치 처리**

- 통계적 방법

```python
# 평균과 표준편차를 이용한 이상치 탐지 및 처리
mean_value = df['column_name'].mean()
std_dev = df['column_name'].std()

# 상한치와 하한치 설정
upper_bound = mean_value + 2 * std_dev
lower_bound = mean_value - 2 * std_dev

# 이상치를 상한치와 하한치로 대체
df['column_name'] = np.where(df['column_name'] > upper_bound, upper_bound, df['column_name'])
df['column_name'] = np.where(df['column_name'] < lower_bound, lower_bound, df['column_name'])
```

- IQR기반

```python
# IQR을 이용한 이상치 탐지 및 처리
Q1 = df['column_name'].quantile(0.25)
Q3 = df['column_name'].quantile(0.75)
IQR = Q3 - Q1

# 상한치와 하한치 설정
upper_bound = Q3 + 1.5 * IQR
lower_bound = Q1 - 1.5 * IQR

# 이상치를 상한치와 하한치로 대체
df['column_name'] = np.where(df['column_name'] > upper_bound, upper_bound, df['column_name'])
df['column_name'] = np.where(df['column_name'] < lower_bound, lower_bound, df['column_name'])
```

**4.3 특성 공학**

- 다항 특성 추가

```python
# 다항 특성 추가 (2차항)
df['column_name_squared'] = df['column_name'] ** 2
```

- 상호작용 특성 추가

```python
# 두 특성 간의 상호 작용 특성 추가
df['interaction_feature'] = df['feature1'] * df['feature2']
```

**4.4 스케일링**

- 표준화

```python
from sklearn.preprocessing import StandardScaler

# StandardScaler를 이용한 표준화
scaler = StandardScaler()
df['column_name_scaled'] = scaler.fit_transform(df[['column_name']])
```

- 정규화

```python
from sklearn.preprocessing import MinMaxScaler

# MinMaxScaler를 이용한 정규화
scaler = MinMaxScaler()
df['column_name_normalized'] = scaler.fit_transform(df[['column_name']])
```

4.5 일반화 증진

- 데이터 증강

```python
from tensorflow.keras.preprocessing.image import ImageDataGenerator

# 이미지 데이터 증강을 위한 ImageDataGenerator 생성
datagen = ImageDataGenerator(
    rotation_range=40,
    width_shift_range=0.2,
    height_shift_range=0.2,
    shear_range=0.2,
    zoom_range=0.2,
    horizontal_flip=True,
    fill_mode='nearest'
)

# 이미지 데이터에 증강 적용
augmented_data = datagen.flow(X_train, y_train, batch_size=32)
```

- 드롭아웃

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Dropout

# 드롭아웃을 적용한 모델 생성
model = Sequential()
model.add(Dense(64, input_dim=10, activation='relu'))
model.add(Dropout(0.5))
model.add(Dense(1, activation='sigmoid'))
```

---

[데이터 전처리 참고 링크](https://velog.io/@kphantom/2.-%EB%8D%B0%EC%9D%B4%ED%84%B0%EC%A0%84%EC%B2%98%EB%A6%AC%EB%9E%80)

---

## 4. 코랩 사용법

### 1) 코랩이란?

= 구글이 제공하는 클라우드 기반 Jupyter Notebook 환경을 말한다. 

즉, 웹 브라우저에서 파이썬 코드를 작성하고 실행할 수 있는 웹 에디터라고 이해하면 된다. 클라우드 기반이기 때문에 따로 프로그램을 설치할 필요가 없고, 구글 계정만 있으면 GPU까지 무료로 구글 코랩으로 사용할 수 있다. 

- 구글 코랩 🛜링크
    
    https://colab.research.google.com/
    

2) 환경설정 및 사용법

- 해당 블로그 🕶️ 참고
    
     https://theorydb.github.io/dev/2019/08/23/dev-ml-colab/