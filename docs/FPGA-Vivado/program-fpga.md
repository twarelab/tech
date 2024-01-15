---
sidebar_position: 2
---

# Program FPGA

실제 Vivado 툴을 이용하여 bit파일을 다운로드 해보자.

## 프로젝트 다운로드

먼저, 프로젝트 파일을 다운로드 한다.  

### Visit GitHub
주소는 다음과 같다.  
> https://github.com/twarelab/apsm1_hdl
![Code](image-20.png)

### Download

- “Download ZIP” 선택  
![Zip Download](image-21.png)

- Save & Extract zip file
![Save zip file](image-22.png)

## 프로젝트 열기

- 압축 푼 폴더의 .xpr 파일 더블클릭  
![Open project](image-23.png)

- 로딩 성공
![Open project vivado](image-24.png)

## Program on FPGA

Program and Debug 선택해서 프로그래밍

- Open Hardware Manager
![Alt text](image-25.png)
- Open Target
![Auto connect](image-26.png)

- Connected Target device
  - `xc7a100t_0` 는 FPGA
  - `s25fl128x...` 은 Flash 
![Connected target](image-27.png)

- Program Device 선택
![Program Device](image-28.png)
- Select bit or bin file
![Prgram popup](image-29.png)
원하는 비트파일을 선택한다. 기본적으로는 아래 폴더에 생성된다.
![select bit](image-30.png)

Bit 파일을 선택하고 “OK”버튼을 누른다.
![ok bit file](image-31.png)

이제 "Program" 버튼을 누르면 끝
![Program device end](image-32.png)

## Program on Flash

- Flash 추가
디바이스가 없으면 해당 디바이스를 추가해야 한다.  
먼저 “Add Configuration Memory Device” 메뉴를 선택하면, 해당 FPGA가 나오는 팝업이 뜬다. 선택하고 클릭한다.  
![add flash](image-33.png)
 
해당 Flash를 검색해서 선택해서 추가한다.
![Find Flash](image-34.png)

바로 프로그램 할 것인지 묻는 팝업에서 “OK”를 누르면, 바로 프로그램이 가능하다.  
![Direct program](image-35.png)

- Flash program
![Select flash and program](image-36.png)

프로그램하는 설정 창은 다음과 같다.
![Config program options](image-37.png)

이제 Erase & Program 과정이 수행된다.
![Erase](image-38.png)
![Program](image-39.png)

## 완료
모든 작업이 완료되면 다음과 같은 팝업창이 나타난다. "OK" 누르면 완료된다.
![Complete](image-40.png)
