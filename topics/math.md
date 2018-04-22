유니티로 배우는 게임 수학

# 사원수 Sir William Rowan Hamilton에 의해 발견되었고, 백터 개념이
파생되었다.  사원수를 채용한 첫 게임 개발 응용사례로는 1996년 툼레이더가 유명하다.


# Eulaer angles - x, y, z .
Quaternion클래스의 Euler메서드는 z - y - x 순서의 회전 생성.

유니티에서 직접 쓰이지는 않지만, Rodrigues' rotation formula라는 임의축 중심의 회전을 표현하는 방식이 있다.

Euler-Rodrigues formula

오일러(Euler) 문제 - gimbal lock

unity inspector - transform -rotation 90, 0, 0 - y, z값을 inspector상에서 드래그하여 변경하면, y값을 변경했을 때도, x값을 변경했을 때도 같은 축에서 오브젝트가 회전하여 짐벌락이 발생하는 것을 확인 할 수 있다.


# 회전행렬
3회의 회전 시점에서 짐벌락이 발생할때 한 번 더 다른 회전 행렬을 합성하면 됨으로 짐벌락이 문제 되지 않음.

* 부동 소수점 연산에서 발생하는 오차.
* 3 x 3 회전 행렬이 차지하는 메모리 영역.

# 사원수 - quaternion
* 짐벌락이 발생하지 않음
* 행렬보다 점유 메모리 영역이 작고 계산 부하도 낮다.
* x, y, z축에 국한되지 않는 임의의 회전 축에서의 회전을 손쉽게 할 수 있다.
* 두 개 회전 사이의 매끄러운 보간을 표현할 수 있다.

## 복소수 - complex number
z = x + i * y
z = r(cosA + i * sinA)

## 이원수 - dual number
이원수는 실 수 a, b와 양수인 정수 n에 대해 e^n = 0을 만족하는 실수가 아닌 멱영원(nilpotent element)인 epsilon을 조합한 수 z = a + b * e를 가리킨다.


a : 실수부
b : 이원수부(dual part)
