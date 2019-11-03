<h2 id="-">수치 예측</h2>

<h3 id="-">선형 회귀</h3>

&nbsp;선형 회귀(Linear Regression)란 종속 변수 y와 한 개 이상의 독립 변수 X와의 선형 상관 관계를 모델링하는 회귀분석 기법이다.
선형 회귀를 수식으로 표현하면 H(x) + Wx + b인데, H(x)는 가설(Hypothesis)을 의미하고 W는 가중치(Weight), b는 편향(bias)를 의미한다.
선형회귀란 바로 이 가중치와 편향을 조절하여 얻은 가설의 값이 실제 값과의 차이가 가장 적은 모델을 찾는 것이다.

<h3 id="-">손실 함수, 경사 하강법</h3>

&nbsp;가설 값이 실제 값과의 차이가 얼마나 적은지 판단하는 함수를 손실 함수(Loss Function)혹은 비용 함수(Cost Function)라 하는데, 선형회귀에서는 평균제곱오차(MSE)를 이용하여 손실 함수를 구한다. 평균제곱오차를 이용하여 손실 함수를 구하면 아래의 식과 같이 된다. 

<p><img src="/Image/cost_function.png"></p>

&nbsp;위의 함수로 cost값을 구했으면 이 값을 최소화 시켜 최적의 함수를 찾아야 한다. 이 때 cost값을 최소화 시키기 위해서 최적화 알고리즘인 경사하강법(Gradient Descent)이나 유전 알고리즘(Genetic Algorithm)을 사용한다. 하지만 이 글에서는 경사 하강법만 설명하겠다.

<p><img src="/Image/GradientDescent.png"></p>

경사 하강법을 그래프로 표현하면 위의 그림과 같이 된다.

<br>&nbsp;경사 하강법이 cost의 최솟값을 구하는 과정을 설명해 보자면 처음에 W와 b의 시작점을 정한다. 시작점의 값은 별로 중요하지 않기 때문에 0이나 임의의 값으로 설정한다. 그 다음 기울기를 편미분 하여 어느 방향이 더 정확한지 혹은 부정확한지 알려준다. 기울기는 항상 손실 함수 값이 크게 증가하는 방향을 향하기 때문에 이 방향의 반대 방향으로 이동한다. 이와 같은 과정을 반복하여 cost값이 최소인 W와 b의 값을 구한다.

&nbsp;위의 과정을 통해 아래와 같은 최적의 일차 함수를 구하게 된다.

<p><img src="/Image/Linear_Regression.png"></p>

<h2 id="-">이진 분류</h2>

<h3 id="-">퍼셉트론</h3>

&nbsp;퍼셉트론(Perceptron)은 프랑크 로젠블라트(Frank Rosenblatt)가 1957년에 제안한 초기 형태의 인공 신경망으로 다수의 입력으로부터 하나의 결과를 내보내는 알고리즘이다.

<p><img src="/Image/Perceptrons.jpg"></p>

&nbsp;위 그림의 오른쪽은 인공 신경망인 퍼셉트론을 표현한 것인데, 그림에서 x는 입력값을 의미하며, W는 가중치, 출력값은 x와 W를 계산 했을 때, 임계값이 넘었을 때, 1을 출력하고 넘지 못하면, 0 또는 -1을 출력한다. 이렇게 뉴런에서 출력값을 변형시키는 함수를 활성화 함수라고 한다.

&nbsp;위의 퍼셉트론을 단층 퍼셉트론이라고 하는데, 이 퍼셉트론은 or이나 and같은 선형적인 구분은 가능하지만 xor같은 비선형적인 문제를 풀지는 못하였다. 하지만 Paul Werbos가 다층 퍼셉트론을 이용하여 xor같은 비선형 문제를 푸는데 성공하였다.

<h3 id="-">로지스틱 회귀</h3>

&nbsp;로지스틱 회귀(Logistic Regression)은 지도학습 중 분류(Classification)에 사용되는 알고리즘이다. 로지스틱 회귀는 분류하려는 범주가 2가지 범주로 나눠진 경우에 적용된다.
<br>&nbsp;로지스틱 회귀는 선형 회귀와는 다른 방법으로 모델을 구축하는데, 그 이유는 선형 회귀에서의 연속적인 숫자인 Y값은 그 값 자체로 의미를 갖지만, 범주형 변수는 의미를 갖지 않는다. 0과 1사이에 중간 범주가 없고 0과 1을 바꿔도 큰 상관이 없다. 만약 선형 회귀에 범주형 변수를 적용시키면 아래와 같은 그래프가 그려진다.

<p><img src="/Image/wrongLogistic.png"></p>

또한 손실함수를 선형 회귀 모델 때와 마찬가지로 경사하강법을 이용하면 아래와 같은 울퉁불퉁한 그래프가 그려져 실제로 구해야 할 전역 최적값(Global Optima)를 구하지 않고 지역 최적값(Local Optima)의 값에 갖혀버리게 된다.

<p><img src="/Image/wrongCost.png"></p>

&nbsp;그러면 이 함수에 맞는 모델과 손실 함수는 무엇일까?
<br>&nbsp;일단 로지스틱 회귀에 맞는 손실 함수는 아래와 같다.

<p><img src="/Image/Logistic_cost.png"></p>

&nbsp;이 식을 그래프로 표현하면 아래 사진과 같다.

<p><img src="/Image/Logistic_cost_graph.png"></p>



<h3 id="-">Sigmoid Function</h3>
