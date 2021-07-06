---
title: "머신러닝 핵심 요약 1 (INTRODUCTION)"
category: 
- Machine Learning
tag: 
- 머신러닝
- Machine Learning
header:
 teaser: /assets/images/Machine_Learning.png


---

-----

<br/>

본 내용은 순천향대학교 정엽섭 교수님의 "머신러닝" 과목 수강시 정리했던 내용을 기반으로 포스팅하였습니다. 이 머신러닝 핵심 요약 포스팅 시리즈에서는 각 개념들에 대해 자세하게 설명하기 보다는, 말 그대로 핵심들만 집어서 살펴보려고 합니다.

<br/>

<br/>

- Machine Learning? 사람이 만든 기술을 구축하는 기술

<img src = "/assets/images/ML-studying/postfiles8.naver_.png">    

​       이미지 출처: [https://blogs.nvidia.co.kr](https://blogs.nvidia.co.kr/2016/08/03/difference_ai_learning_machinelearning/)

- 이제야 머신러닝/딥러닝이 뜨는 이유? 

  첫번째, 기계가 발전하면서 분산저장시스템이 발달

  두번째, GPU를 사용하면서 대용량데이터를 처리할 기술이 생김

- 머신러닝에서의 feature?

  feature == attribute == 열 == 차원  (즉, feature을 늘린다 == 차원을 늘린다.)

- 일반적으로 label 개수 (= class 개수) < feature 개수 < Data 개수 이다.

- feature 선택은 매우 중요하다. feature에 대한 도메인 지식(전문지식)이 요구된다 

  e.g.) 일본어 문장에 대한 감정 분석시, 일본어에 대한 전문지식이 요구됨

- feature에 비해 데이터가 너무 적으면 overfitting 과적합 발생 가능성 증가 (curse of dimensionality; 차원의 저주) (새로운 테스트 데이터에 대해 잘못된 예측을 할 가능성이 커짐)

  <img src = "/assets/images/ML-studying/The-curse-of-dimensionality.png" width="700px"> 

  이미지 출처: [www.researchgate.net](https://www.researchgate.net/figure/The-curse-of-dimensionality-a-11-objects-in-one-unit-bin-b-6-objects-in-one-unit-bin_fig1_264823819)

- 딥러닝은 feature을 자동으로 정의 해준다. => 딥러닝은 어떤 식으로 학습하여 좋은 결과가 나오는지 해석하기가 힘들다. 이러한 현상 때문에, 블랙박스라고도 한다. (반대로 학습과정이 해석되는 것은 화이트박스라고 한다.)

  <img src = "/assets/images/ML-studying/image-20210706214949629.png" width="450px">  

  이미지 출처: [https://ichi.pro/ko](https://ichi.pro/ko/haeseog-ganeunghan-meosin-leoning-gaideu-233158916486863)

- 머신러닝에서의 model?

  model == method == algorithm == hypothesis (임의의 목적을 달성하기 위한 hypothesis)

- computational complexity(계산복잡도)는 낮을수록, data sample complexity는 높을수록 좋음

  computational complexity: 데이터가 증가할 때 계산량이 얼마나 많아 지는가

  data sample complexity: 데이터가 증가할 때 정답의 품질이 얼마나 증가하는가

- 비지도학습은 parametric, Non-parametric으로 나눌 수 있다.

  parametric: 데이터가 어떤 분포로부터 생성된건지 임의로 가정. 즉, 모델을 가정하여 파라미터를 통해 문제에 접근하는 경우

  Non-parametric: 어떤 분포인지 가정이 없고, 파라미터 개수가 변하기도 한다.  e.g.) KNN 알고리즘, Decision Tree 등

- Discriminative model와 Generative model

  Discriminative model : Conditional Probaility(조건부확률) P(xㅣy) 학습. class들의 경계선 찾기. 즉, classification이 목표 

   e.g.) 선형회귀, SVM

  Generative model: Joint Probability인 P(x, y) = P(x∩y) 를 학습. 데이터 범주의 분포를 학습 

  e.g.) 가우시안, 나이브베이즈

  <img src = "/assets/images/ML-studying/image-20210706214307635.png">

  이미지 출처: [https://stanford.edu](https://stanford.edu/~shervine/teaching/cs-229/cheatsheet-supervised-learning)

- 머신러닝과 관련된 유명한 말

  No Free Lunch: “모든 것에 최선인 알고리즘은 없다”

  <img src = /assets/images/ML-studying/Firmin-fig1-no-free-lunch.jpg width ="390">

  이미지 출처 : [www.kdnuggets.com](https://www.kdnuggets.com/2019/09/no-free-lunch-data-science.html)     

  Occam’s Razor: “단순함이 의외로 진리일 수 있다”

  <img src = /assets/images/ML-studying/occam.gif width ="200">

  이미지 출처: [www.chrismadden.co.uk](http://www.chrismadden.co.uk/cartoon-gallery/occams-razor-ockhams-razor-too-complicated/)

- 정성평가: 눈으로 보고 느끼는 결과/성과. 주관적인 평가방식

  정량평가: 정답과 비교해서 성능 수치를 비교. 객관적인 평가방식

- 기계학습에서의 정량평가 방법들

  Accuracy = 1 - Error 

  Precision(정밀도): 예측이 정답이 것중 실제로도 정답인 비율

  Recall(재현율): 실제 정답인 것중 예측도 정답인 비율 (얼마나 잘 재현했는지)

  <img src = "/assets/images/ML-studying/confusion-matrix.png" width="600">

  이미지 출처: [www.researchgate.net](https://www.researchgate.net/figure/Calculation-of-Precision-Recall-and-Accuracy-in-the-confusion-matrix_fig3_336402347)

  > e.g.) 총 10명 중 실제 마피아 2명 일 때, 이 중 4명을 마피아로 예상하였다. 그 4명 중 실제 마피아는 1명 이었다고 하자.
  >
  > => Precision은 1/4 (마피아라고 예측한 사람 중 실제 마피아인 비율)
  >
  > ​      Recall은 1/2 (실제 마피아 중 예측도 마피아였던 비율)

  <img src = "/assets/images/2021-07-06-ML-studying/image-20210706223706455.png">

  AUC: ROC curve에서 그래프 아래 면적 (값이 클수록 성능이 좋은 것)

  <img src = "/assets/images/ML-studying/img.png" width="350px">

  이미지 출처: [https://glassboxmedicine.com](https://glassboxmedicine.com/2019/02/23/measuring-performance-auc-auroc/)

  > ROC curve는 False Positive Rate(FPR)이 x축이고, True Positive Rate(TPR)이 y축인 그래프
  >
  > False Positive Rate(FPR): 실제 negative 중에서 알고리즘 예측값은 positive인 것
  >
  > True Positive Rate(TPR): 실제 postive 중에서 알고리즘 예측값도 postive인 것 (= Sensitivity = Recall)

- Validation? 연습용 테스트 데이터 (트레이닝 데이터에서 떼어내어 마치 테스트 데이터인 양 쓰는 것) => 이를 이용하여 test accuracy를 가늠. 

  따라서 좋은 성능을 내는지 확인 후, 실제 새로운 데이터에 대해 모델 사용 가능

- Bias: 평균에서 멀어진 것 (e.g., 소방호스의 방향이라고 생각) / Variance: 어떤 예측을 할 때 결과가 다양하게 나오는 것 (e.g., 호스물의 응집도라고 생각)

  <img src = "/assets/images/ML-studying/image-20210706205423963.png">

  (이 Bagging과 Boosting에 대해서는 나중에 머신러닝 핵심 요약 포스팅 시리즈에서 다시 더 자세하게 다룰 예정입니다.)

- 오버피팅이 되면, Bias는 작지만 variance는 커짐

- test data가 Variance가 커서 과적합(오버피팅)됐다면? 

  1. 데이터 수 늘리기  2. 모델 경량화

- test data가 Bias가 커서 과소적합(언더피팅)됐다면? 모델 복잡도 높이기

- 머신러닝에서의 학습이란? 모델이 가진 **파라미터를 최적화**(최소화 or 최대화)하는 것

- 파라미터를 최적화하기 위한 함수들 정리

  > **Loss function**: <font style="color:#cc3333">하나의 input 데이터</font>의 오차 계산
  >
  > **Cost function**: <font style="color:#cc3333">Loss를 총 데이터에 대해 평균</font> 낸 것
  >
  > **Objective function**: 가장 일반화된 용어. 학습을 통해 <font style="color:#cc3333">최적화하려는 모든 종류의 함수</font>

