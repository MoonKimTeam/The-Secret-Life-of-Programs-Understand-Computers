# 6장 입출력과 네트워킹

## 저수준 I/O

- I/O 포트
    - CPU가 읽거나 쓸 수 있는 비트와 물건을 연결한 단순한 I/O
- 버튼을 눌러라
    - 푸시버튼을 누르지 않으면 IRQ에 논리 1을 공급, 누르면 논리 0을 공급
    - 버튼 한번 누를 때 여러 번 인터럽트 발생하는 바운스 발생 가능 -> 디바운스 필요, 인터럽트 핸들러에타이머 설정 후 감지
- 빛이 있으라
    - 알람 시계나 식기세척기 등의 디스플레이의 7세그먼트 디스플레이
    - 공통 캐소드 디스플레이: 공통 연결 핀 사용해서 핀 개수 줄임
    - 멀티플렉스 이용해서 여러 숫자 디스플레이 제어
    - LED의 다이오드 성질 이용해서 애노드를 병렬하여 하나로 연결
    -
- 빛, 동작, 상호 연동
    - 버튼과 디스플레이가 결합된 경우 버튼과 디스플레이를 멀티플렉싱하면 핀 덜 써도 됨
- 밝기 조절
    - 디스플레이 듀티 사이클 조절하여 밝기 조절
    - 사이클 늘리면 어두워지고 줄이면 밝아짐
    - 밝기는 디스플레이가 켜져 있는 시간과 비례
- 그레이의 2^n가지 그림자
    - 로터리 인코더: 회전축의 위치를 2진수로 인코딩
    - 그레이 코드 로터리 인코더: 각도가 달라질 때 비트가 하나씩만 달라지는 인코딩 방법(000 ,001, 011, 010, 110, 111, 101, 110 순)
- 쿼드러처
    - 쿼드러처 인코딩: 절대적 위치 알 필요 없지만 위치, 방향이 어떻게 변했는지 알아야 할 때 사용
    - 두 개의 센서만 있으면 됨
    - 현재 위치와 이전 위치로부터 4비트 숫자만들어서 회전 방향을 알 수 있음
    - 볼마우스는 쿼드러처 인코더를 90도 엇갈려 놓고 고무공을 넣은 것
- 병렬 통신
    - 병렬: 컴포넌트 하나하나에 별도에 선이 있어서 동시에 모든 컴포넌트 제어 가능
    - 데이터 선에 올바른 데이터가 들어있는 순간 알아내기 위해 타이밍을 알려주는 다른 신호 필요(스트로브 신호)
    - 예전 프린터, 스캐너, 디스크 드라이브용 포트에 사용
- 직렬 통신
    - 비용 감소를 위해 선을 덜 쓰면 좋음 -> 한 선에 여러 신호 보내기
    - 시프트 레지스터 이용하기 -> 송신자, 수신자 서로 동기화 필요
    - 텔레타이프: 텔레그래프 + 타이프라이터. 한 곳에서 타이핑한 내용을 멀리 있는 프린터에서 출력하는 기계.
        - 데이터는 직렬 프로토콜을 통해 신호선 하나로 전달. 돌아오는 선 하나 더 필요
        - 마크-스페이스 방식
        - 동기화오류 발생 시 정해진 문자시간 동안 조용히 있다가 수신자가 동기화 할 때까지 기다리기
        - 시간 분할 멀티플렉싱: 시간을 나눈 슬롯을 만들고 슬롯마다 각기 다른 비트를 할당해서 데이터를 한 선에 멀티플렉
        - 직렬 인터페이스 예: SATA, SPI, TWI, 원와이어
- 파동에 올라타라
    - 마크 스페이스 방식의 문제: 전화선에서 작동하지 않음
    - 반송파(carrier)에 신호를 태워서 전송
    - 반송파를 마크 스페이스 파형처럼 변화시키는 변조 수행
    - 받는쪽에서는 다시 마크와 스페이스로 되돌리는 복조 수행
- 범용 직렬 버스(USB)
    - 단 4줄 뿐인 단일 커넥터로 기존 PS/2, RS-232, 병렬 포트 등을 대체함
    - 초기에는 두 줄의 전력선, 여러 데이터 신호에 사용하기 위한 연선(twisted pair)로 구성
    - C 타입은 선을 24개까지 사용
    - 데이터를 헤더와 페이로드가 담긴 패킷으로 나뉘어서 전송
    - 음향과 비디오를 동시성 전송을 통해 처리

## 네트워킹

- LAN, WAN
- 회선 교환: 통화가 끝나면 필요에 따라 회로를 만들 수 있음
- 패킷 교환: 같은 전선을 공유하면서 패킷을 보낼 수 있음 -> 효율적
- 여러 연구소나 회사들이 LAN을 만들었고 다른 LAN들 간에 소통하기 위한 방법으로 인터넷이 등장

- 최근의 LAN들
    - 이더넷: 초기에는 LAN
        - 네트워크 인터페이스에 MAC 주소를 부여
        - 프레임(송신 주소, 수신 주소, 오류 검증)이라는 이름의 패킷이 포함된 헤더와 페이로드가 들어감
        - 어떤 장치가 이야기하면 연결된 모든 장치들은 들을 수 있지만 MAC 주소가 일치하지 않으면 무시
        - 랜덤 백오프 후 재시도: 말하고 싶은 장치는 충돌 발생 시 임의 시간 기다린 후 다시 말함
        - 옛날엔 반이중, 지금은 전이중
        - 라우터에 연결하면 패킷을 정확히 배달해줌

- 인터넷
    - TCP/IP: 인터넷이 사용하는 두가지 프로토콜.
    - IP/주소: 인터넷 상의 각 컴퓨터 또는장치에 할당된 유일한 주소
    - 도메인 이름 시스템(DNS): 이름을 IP 주소로 바뀌주는 시스템
    - 월드 와이드웹: HTTP, HTTPS 를 사용해 HTML로 구성된 하이퍼 텍스트(웹 페이지) 전송

## 아날로그 처리 방법

샘플링(시간이나 공간상 일정한 간격으로 값을 읽기)을 이용한 아날로그, 디지털 간 변환

- 디지털을 아날로그로 변환 - DA 변환기(DAC)
    - 오디오 플레이어, 신디사이저 -> 톱니 파형 만들기
- 아날로그를 디지털로 변환 - AD 변환기
    - 샘플 앤 홀드라는 회로 이용해서 아날로그 파형 잡아냄
    - 문턱값과 신호 비교하는 비교기
    - 비교기를 여러 기준 전압과 쌓아서 플래시 변환기 만들 수 있음
- 디지털 오디오
    - 샘플링을 통해 오디오를 디지털화 가능
    - 푸리에 변환을 통해 코드의 각 부분을 구분 가능
- 디지털 이미지
    - 그림 요소를 픽셀로 이뤄진 직사각형 배열로 표현
    - 각 픽셀은 세가지 색의 조합으로 표현
    - 포인트 샘플링, 슈퍼샘플링(한 정사각형 안에서 여러 지점의 색을 얻어서 평균 내는 방법)
    - JPEG
- 비디오
    - 2차원 이미지를 일정한 시간 간격으로 샘플링한 시퀀스
    - 옛날 영화는 24fps로 이미지 샘플링
    - 비디오는 이미지나 오디오보다 높은 데이터 비율 -> 압축이 매우 중요
    - 움직임 보상: 프레임이 변할 때 이미지 중 변한 일부분만 저장 혹은 송신
    - 데이터에 키프레임을 추가해서 이미지 손상 시에 복구 가능

## 휴먼 인터페이스 장치

- 터미널
    - 컴퓨터가 저렴하고 작아지면서 회사나 부서마다 작은 컴퓨터, 텔레타이프를 갖게 되었고 이를 터미널이라고 부름
- 그래픽 터미널
    - 화면을 사용하는 컴퓨터 등장
- 벡터 그래픽
    - 모눈종이가 아니라 벡터로 그림 그리기
- 래스터 그래픽
    - 텔레비전의 작동방식. 왼쪽 위부터 한줄 그리고 다시 다음 줄 그림. 마지막 줄에서 다시 첫줄로 이동해서 반복.
- 키보드와 마우스
    - 데이터를 받아들이는 역할
    - 키보드는 여러스위치와 논리회로 묶은 것
    - 마우스는 x, y좌표 담당하는 쿼드러처 인코더 사용