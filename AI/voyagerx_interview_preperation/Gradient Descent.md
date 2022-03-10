# Gradient Descent
* 함수의 최소값을 찾는 최적화 기법으로 함수의 미분값을 이용해 값을 조정하는 방식을 말한다. 이때 변하는 정도를 조절하기 위해 Learning Rate를 사용한다.

## 왜 Gradient Descent 에서는 기울기를 사용하는가?
* 기울기는 특별한 의미를 가지는 벡터장으로 방향 도함수가 최대의 변화를 갖는 방향이 기울기가 가리키는 방향이기 때문이다. 최대의 변화를 가지는 방향의 반대 방향으로 향하면 언젠가는 최소값을 찾을 수 있기 때문이다.

## 지역 극소점Local Optima에 빠지는 문제
* 과거에는 임의에 극소점에 빠지는 문제가 있었지만 깊이가 깊은 딥러닝 모델의 경우 지역 극소점을 가질 확률은 낮다. 최근에는 극소점으로 여겨지는 부분들이 경사가 완만한 saddle point로 여겨지는 부분으로 학습이 지연된다고 여기는것이 주류의 인식이다.


### 수학적인 설명
* 최적화할 함수 {\displaystyle f(\mathbf {x} )}{\displaystyle f(\mathbf {x} )}에 대하여, 먼저 시작점 {\displaystyle \mathbf {x} _{0}}\mathbf {x} _{0}를 정한다. 현재 {\displaystyle \mathbf {x} _{i}}{\mathbf  {x}}_{i}가 주어졌을 때, 그 다음으로 이동할 점인 {\displaystyle \mathbf {x} _{i+1}}{\displaystyle \mathbf {x} _{i+1}}은 다음과 같이 계산된다.

{\displaystyle \mathbf {x} _{i+1}=\mathbf {x} _{i}-\gamma _{i}\nabla f(\mathbf {x} _{i})}{\displaystyle \mathbf {x} _{i+1}=\mathbf {x} _{i}-\gamma _{i}\nabla f(\mathbf {x} _{i})}
이때 {\displaystyle \gamma _{i}}\gamma _{i}는 이동할 거리를 조절하는 매개변수이다.

이 알고리즘의 수렴 여부는 f의 성질과 {\displaystyle \gamma _{i}}\gamma _{i}의 선택에 따라 달라진다. 또한, 이 알고리즘은 지역 최적해로 수렴한다.

따라서 구한 값이 전역적인 최적해라는 것을 보장하지 않으며 시작점 {\displaystyle \mathbf {x} _{0}}\mathbf {x} _{0}의 선택에 따라서 달라진다.

이에 따라 다양한 시작점에 대해 하강법을 적용하여 그 중 가장 좋은 결과를 선택할 수도 있다.

### code
* 이하의 파이썬(3.7.3)언어로 작성한 경사 하강법 알고리즘은 f(x)=x4−3x3+2 함수의 극값을 미분값인 f'(x)=4x3−9x2를 통해 찾는 예를 보여준다.[2]
x_old = 0
x_new = 6 # The algorithm starts at x=6
eps = 0.01 # step size
precision = 0.00001

def f_prime(x):
    return 4 * x**3 - 9 * x**2

while abs(x_new - x_old) > precision:
    x_old = x_new
    x_new = x_old - eps * f_prime(x_old)

print("Local minimum occurs at: " + str(x_new))