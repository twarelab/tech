---
sidebar_position: 1
---

# Install Vivado tool
FPGA 에 프로그래밍 할 수 있는 툴인 Vivado를 설치해 보자.

## 사용자 계정 생성
우선 툴 제공 업체인 AMD 사이트에서 계정을 먼자 만들고 로그인 해야 한다.

계정 생성하는 방법은 AMD 사이트에서 로그인 버튼은 누르면, 아래와 같이 생성할 수 있는 "계정 만들기" 버튼을 볼 수 있다. 클릭해서 생성작업을 해보자.
<p align="center"><img src="/img/FPGA-Vivado/image.png" width="80%"/></p>

정보를 입력하고 생성이 완료되면, 꼭 로그인을 하도록 한다.
<!-- <p align="center"><img src="image-1.png" width="80%"/></p> -->

## Vivado Download
이제 Vivado 툴을 다운로드 하면 된다. 해당 툴을 다운로드 하는 경로는 아래와 같다. 
- 다운로드 주소
  > https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools.html

<p align="center"><img src="image-2.png" width="80%"/></p>

사용자 환경에 따라 맞는 버전을 다운로드 하면 된다. 윈도우 사용자는 아래 그림처럼 윈도우 버전을 다운로드하면 된다.

<p align="center"><img src="image-3.png" width="80%"/></p>

다운로드를 위해서는 몇가지 정보를 AMD사이트에서 요구한다. 해당 정보를 입력하고 다운로드 버튼 선택하면 다운로드 완료된다.

<p align="center"><img src="image-4.png" width="80%"/></p>

## 설치

이제 다운로드 받은 파일을 실행하여 설치 과정을 수행해보자. 아래 과정을 쭉 따라가면 된다.

우선, 설치 전에 JDK 방화벽 예외 허용 이라는 팝업이 나타나면 "엑세스 허용"를 눌러 허용하도록 한다.
<p align="center"><img src="image-5.png" width="80%"/></p>

설치화면의 시작화면은 다음과 같다. 다음 "Next" 버튼을 클릭한다.
<p align="center"><img src="image-6.png" width="80%"/></p>

아래 입력창에 자신이 가입한 로그인 정보 입력하고 "Download and Install Now"를 선택하고 "Next" 버튼을 클릭한다.
<p align="center"><img src="image-7.png" width="80%"/></p>

- Vivado 툴 선택
<p align="center"><img src="image-8.png" width="80%"/></p>

- VivadoML Standard 선택
<p align="center"><img src="image-9.png" width="80%"/></p>

- 필요한 디바이스 설치 (Artix-7필수)
<p align="center"><img src="image-10.png" width="80%"/></p>

- 사용 동의를 전체 동의 하고,
<p align="center"><img src="image-11.png" width="80%"/></p>

- 설치 폴더와 디스크 용량 확인 작업을 수행한다.
- 디스크 용량이 필수로 만족해야 설치된다. 설치 전에 용량 확인을 필수로 하자.
<p align="center"><img src="image-12.png" width="80%"/></p>

- 이제 설치 작업을 시작한다. "Install" 버튼을 클릭한다.
<p align="center"><img src="image-13.png" width="80%"/></p>

- 다운로드 시작 및 설치 작업이 진행된다.
<p align="center"><img src="image-14.png" width="80%"/></p>

- 설치 후반부 쯤에 케이블 소프트웨어 설치와 관련된 팝업이 나타난다. "설치" 버튼을 클릭한다.
<p align="center"><img src="image-15.png" width="80%"/></p>

- 마찬가지로 WinPcap 설치 팝업이 나타나면 반드시 설치해 준다. "Next" 버튼을 몇 번 눌러 작업을 완료한다.
<p align="center"><img src="image-16.png" width="80%"/></p>

- 특별한 문제가 없다면 아래처럼 설치가 완료된다.
<p align="center"><img src="image-17.png" width="80%"/></p>

## Vivado 프로그램 실행

이제 설치가 완료된 Vivado 툴을 실행해 보자.
실행하는 메뉴 위치는 아래 그림을 참고하세요.
<p align="center"><img src="image-18.png" width="40%"/></p>

성공적으로 설치가 되었다면 아래와 같은 화면이 나타난다. 
<p align="center"><img src="image-19.png" width="80%"/></p>

끝.
