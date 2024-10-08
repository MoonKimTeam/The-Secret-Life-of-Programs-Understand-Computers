# 데이터 구조와 처리

## 기본 데이터 타입

기본 데이터 타입에는 크기(비트 수)와 해석(부호 여부, 부동소수점 여부, 문자 여부, 포인터 여부 등)이라는 두 가지 측면이 존재한다. <br>
포인터는 집 주소와 비슷하다. 집을 찾을때 주소를 쓸 수 있는것처럼 원하는 값이 있는 위치를 포인터로 알 수 있다. <br>
일부 언어는 잘못된 포인터 사용으로 인한 오류를 막기 위해 참조라는 개념을 구현하기도 한다.

## 배열

배열은 아파트와 같다. 아파트 한 동에는 주소가 있고, 한 아파트 동 안의 각 집에는 번호가 있다. <br>
프로그래머는 호수를 인덱스라고 하고, 각각의 집을 원소라고 한다.

<img width="332" alt="스크린샷 2024-09-08 오후 2 59 57" src="https://github.com/user-attachments/assets/35e64c08-1175-4071-a7f3-0fec1b7c0987">

## 문자열

여러 문자로 이뤄진 시퀀스를 문자열이라고 한다. <br>
배열과 마찬가지로 문자열을 연산할때도 그 길이를 알아야 한다. <br>
길이가 변할 수 있는 가변 문자열 데이터에 작용하는 프로그램이 많기 때문에, 문자열을 배열에 저장하기는 충분하지 않다. <br>
c는 다른 언어와 달리 문자열을 위한 전용 데이터 타입을 제공하지 않는다. 대신 1차원 바이트 배열을 사용한다. <br>
C 문자열은 길이를 저장하지 않고, 대신에 문자 배열에 들어 있는 문자열 데이터의 끝에 바이트를 하나 추가하고, 여기에 문자열의 끝을 표시하는 문자로 NUL을 넣는다.

<img width="389" alt="스크린샷 2024-09-08 오후 3 05 41" src="https://github.com/user-attachments/assets/d4fd073a-d982-49b7-8150-0ed4bb284d12">


## 단일 연결 리스트

데이터양이 정해져 있지 않은 경우에는 배열이 적합하지 않다. <br>
배열을 충분히 크게 만들지 않으면 데이터가 늘어났을 때 새로 더 큰 배열을 만들고 기존 배열의 내용을 새 배열로 복사해야 하기 때문이다. <br>
연결 리스트는 목록에 들어갈 원소 개수를 모르는 경우 배열보다 더 잘 작동한다. <br>
리스트 맨 앞은 헤드라고 하고, 마지막은 테일이다. 다음 원소가 정상적인 리스트 원소가 아니기 때문에 테일을 쉽게 알아볼 수 있다. 보통 NULL 포인터로 리스트 원소가 아님을 표현한다. <br>

## 동적 메모리 할당

배열 등의 변수가 사용하는 메모리는 정적이다. 이런 변수에 할당된 주소는 바뀌지 않는다. <br>
리스트 노드와 같은 존재는 동적이다. 이들은 필요에 따라 생기기도 하고 사라지기도 한다. 이런 동적인 대상에 사용할 메모리를 힙에서 얻는다.

## 가비지 컬렉션

자바나 자바스크립트 같은 언어에는 포인터가 없지만 직접 메모리 할당 헤제를 하지 않으면서도 동적 메모리 할당을 지원한다. <br>
이런 언어는 가비지 컬렉션을 구현한다.

자바 같은 언어는 포인터 대신 참조를 사용한다. 참조는 인터를 추상화해서 거의 비슷한 기능을 제공하지만 실제 메모리 주소를 노출하지는 않는다. <br>
가비지 컬렉션을 사용하는 언어에는 데이터 요소를 만들어내면서 이 요소가 사용할 메모리도 할당하는 new 연산자를 제공하는 경우가 자주 있다. <br>
이터 요소를 삭제하는 경우에 대응하는 연산자는 없다. 대신, 언어의 런타임 환경이 변수 사용을 추적해서 더 이상 사용하지 않는 메모리를 자동으로 해제해준다.

가비지 컬렉션도 트레이드 오프가 있다. <br>
한 가지 문제는 프로그래머가 가비지 컬렉션 시스템을 제어할 수 없다는 점이다. 

## 이중 연결 리스트

단일 연결 리스트의 delete 함수에서는 포인터를 제대로 변경하기 위해 삭제하려는 원소의 바로 앞 원소를 찾아야만 한다. <br>
이로 인해 단일 연결 리스트의 delete는 상당히 느리다.

이중 연결 리스트는 노드에 다음 원소에 대한 포인터뿐만 아니라 이전 원소에 대한 포인터도 들어 있는 리스트다. <br>
이로 인해 노드당 부가 비용은 2배가 되지만, delete 시 노드를 앞에서부터 방문할 필요가 없어진다. <br>
이중 연결 리스트의 장점은 리스트 전체를 방문하지 않아도 원하는 위치에 노드를 추가하거나 삭제할 수 있다는 점이다.

## 대용량 저장장치

데이터를 메모리상에서 관리할 때는 포인터를 통해 메모리를 참조하더라도 충분하다. <br>
하지만 메모리에 있는 정보는 일시적이고 데이터를 장기적으로 저장할 때는 디스크를 사용하므로, 데이터를 디스크에 저장하기 위해서는 영구적인 어떤 존재가 필요하다. (파일이름) <br>
이런 파일 이름을 디스크에 저장할 방법과 파일 이름과 파일의 데이터가 저장된 디스크 블록을 연결해줄 방법이 필요하다.

이 모두를 처리하는 방법은 블록 중 일부를 아이노드로 따로 지정한다. <br>
아이노드는 디스크 블록에 대한 인덱스와 노드를 합친 단어이다. <br>
아이노드에는 파일에 대한 여러 가지 정보가 들어간다. 이런 정보에는 파일 이름, 파일 소유자, 파일 크기, 파일에 대한 허가 내역 등이 포함된다.

## 데이터베이스

2진 트리는 데이터를 메모리에 저장할 때는 훌륭한 방법이지만, 메모리 안에 들어갈 수 없을 정도로 커다란 데이터를 저장할 때는 그리 잘 작동하지 않는다. <br>
데이터베이스는 정해진 방식으로 조직화된 데이터 모음이다. DBMS는 이터베이스에 정보를 저장하고 읽어올 수 있게 해주는 프로그램이다. <br>
데이터베이스는 B 트리라는 데이터 구조를 활용한 시스템이다. <br>
B 트리는 균형 2진 트리보다는 공간을 덜 효율적으로 사용하지만 성능이 더 낫고, 특히 디스크에 데이터를 저장할 때 균형 2진 트리보다 더 성능이 좋다. 

<img width="523" alt="스크린샷 2024-09-08 오후 3 23 22" src="https://github.com/user-attachments/assets/7ad0c95a-d466-47fa-a3d5-6cd8417c3561">

내부 노드는 균형이 잡혀 있고 이로 인해 검색 시간을 미리 예측할 수 있다.


## 해시

해시 함수가 계산하기 쉽고 각 키를 벽에서 유일한 위치에 뿌려준다면, 검색을 아주 빠르게 할 수 있다. <br>
해시 함수의 결괏값을 사용해 키에 대응하는 데이터를 메모리에 저장할 수 있다. <br>
따라서 해시 함수는 메모리 크기보다 작은 범위의 값을 만들어내야 한다. <br>
해시 함숫값의 범위가 너무 크면 데이터를 너무 많이 사용하거나, 데이터가 너무 여기저기 흩어져서 메모리 접근 성능이 떨어질 수 있다.

저장장치에 데이터를 저장하는 방법 중에는 해시 함수의 결과를 배열 인덱스로 활용하는 방법이 있다. <br>
이런 배열을 해시 테이블이라고 말한다.

좋은 해시 함수는 계산하기 쉬워야 하고, 키를 골고루 버킷에 뿌려줘야 한다. <br>
텍스트에 대해 꽤 잘 동작하는 해시 함수로는 문잣값을 모두 더하는 함수가 있다. <br>
이런 함수는 합계가 해시 테이블 인덱스 최댓값보다 커질 수 있다는 문제가 있지만 , 합계를 해시 테이블 크기로 나눈 나머지를 사용하면 쉽게 이 문제를 해결할 수 있다. <br>
이런 방식은 해시 충돌이 발생할 수도 있는데, 해시 체인을 이용해 이런 문제를 해결한다. <br>

<img width="427" alt="스크린샷 2024-09-08 오후 3 28 34" src="https://github.com/user-attachments/assets/858159da-44e5-4fec-99c3-df9440b6547e">













