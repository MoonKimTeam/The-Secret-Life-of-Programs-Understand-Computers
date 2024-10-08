# 프로그래밍 언어 처리

## 어휘 분석

어휘 분석은 코드를 기호로부터 단어와 같은 성격의 토큰으로 변환하는 과정이다. <br>
토큰을 추출하는 것만으로는 충분하지 않다. 실용적인 언어라면 이름, 숫자, 연산자 등 토큰 유형도 많기 때문에 토큰을 구분해야 한다. <br>


<img width="688" alt="스크린샷 2024-09-08 오후 5 17 30" src="https://github.com/user-attachments/assets/0debdaa8-2ac7-4bcb-9b86-faef5278ecc0">

## 파스 트리

고수준 언어를 컴파일할 수도 있지만 인터프리트할 수도 있다. <br>
컴파일러는 소스 코드를 구체적인 기계에 맞는 기계어로 변환한다. 같은 프로그램에 대해 다른 컴파일러를 사용하면 다른 대상 기계를 위한 프로그램을 만들어낼 수 있다. 프로그램을 컴파일하고 나면 실행할 준비가 된 것이다. <br>
인터프리터 언어는 가상 머신에서 실행된다.

일반적으로 컴파일이 된 코드는 기계어이기 때문에 더 빠르게 실행된다. <br>
인터프리터에 의해 실행되는 코드는 마치 누군가가 영어로 된 책을 보면서 우리말로 즉시 번역해 읽어주는 것처럼 수명이 짧다.

일반적으로 컴파일러나 인터프리터는 파스 트리를 구성한다. <br>
파스 트리는 언어 문법으로부터 만들어낸 유향 비순환 그래프 데이터 구조다.

## 인터프리터

<img width="695" alt="스크린샷 2024-09-08 오후 5 23 55" src="https://github.com/user-attachments/assets/70ddb56f-f589-4be9-8467-ed8506fc0595">

<img width="617" alt="스크린샷 2024-09-08 오후 5 24 33" src="https://github.com/user-attachments/assets/9e0f084e-af4c-4dad-9b0c-60ae1ad908bb">

## 컴파일러

<img width="787" alt="스크린샷 2024-09-08 오후 5 25 08" src="https://github.com/user-attachments/assets/9092ff56-6c0b-47ad-b266-05c71a16745b">

코드 생성기는 특정 대상 기계에 대한 기계어 코드를 만들어낸다. <br>
C 같은 일부 언어의 코드 생성기는 실제로 대상 기계의 어셈블리 언어코드를 만들어내고, 대상 기계의 에셈블러를 사용해 이 어셈블리 언어 코드를 대상 기계의 기계어로 번역한다.

## 최적화

대부분의 언어 도구에는 최적화기라는 추가 단계가 파스 트리와 코드 생성기 사이에 들어간다. <br>
최적화기는 파스 트리를 분석하고 이 결과를 활용해 더 효율적인 코드를 생성해내도록 파스 트리를 변환한다.






