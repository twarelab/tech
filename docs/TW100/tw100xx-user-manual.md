---
sidebar_position: 3
---
# TW100xx User Manual

이 문서는 TW100xx 시리즈 제품의 각종 기능에 대한 정보를 제공합니다.

## Introduction
### Key Features
- 4 Port Serial-to-Ethernet
- Support DHCP IP Acquisition
- Support DNS Query
- Support NTP Time Query 
- Support Time Zone Setting
- TCP/UDP Data Communication
- Ethernet Data Packing Option
- Support Up to 3Mbps UART Baud Rate
### Product Specifications
| Item  | Specification |
|:-----:|:---------------|
|MCU| STM32F405RGT6 (RAM: 192KByte, FLASH: 1MByte) |
|LAN| W5500 (10/100Mbps Ethernet) |
|UART| 4 Ports (3.3V TTL Level) |
|Console Port| Supported |
|Dimension| TW100MJ: 48.26(W)x61.4(H)x22.0(D), TW100XR:48.26(W)x58.0(H)x15.0(D)|
|Connector|2.54mm pitch Pin Header. J5: 2x14, J6: 1x14 |
|Input Power| DC 3.3V |
|Power Dissipation| Typical: 100mA, Peadk: 150mA |
|Temperature| Operation: 0 ~ +70 (Celius), Storage: -40 ~ +85 (Celius)
|Humidity| 10 ~ 80% |
## Getting Started
### Hardware Setting
TW100xx EVB를 테스트 하기위한 절차는 아래 순서를 따른다.
* EVB Box에 동봉된 USB mini Cable의 mini 단자부분을 J7 USB mini socket에 연결한다.
* USB Type A 단자를 컴퓨터에 연결한다.
* 전원 Switch(SW4)를 [ON] 부분으로 변경한다.
* LD1 LED가 점등되면 전원이 정상적으로 인가된다는 의미이다.
* Windows에서는 장치관리자를 통해서 Linux의 경우에는 ‘ls /dev’ 명령을 통해서 EVB Debug port에 연결된 Com port를 확인한다.
* PC에서 Serial Terminal Program을 실행하고 확인한 Com port를 Open한다. Baud Rate는 2Mbps이다.
* 어떤 메시지도 출력되지 않는다면 SW1 (RESET SW)를 눌러서 모듈을 하드웨어 Reset한다.
* 아래 그림과 같은 메시지가 출력되면 Hardware Setting은 정상적으로 이루어진 것이다.

![부팅시 디버그 메시지 화면](./img/usermanual/figure-1.png)

#### Debug Port
| Item  | Value |
|:-----:|:---------------:|
|Baud Rate| 2Mbps |
|Data Bit| 8 bits |
|Stop Bit| 1 bit |
|Parity| None |
|Flow Ctrl| None |
### Factory Default Value
##### General Info
|    Item    | Specification |
|:-------------|:--------------|
| DHCP | Disable (Static IP) |
| Local IP Address  192.168.0.100 |
| Local Subnet | 255.255.255.0 |
| Local Gateway | 192.168.0.1 |
| DNS Server IP | 168.126.63.1 |
| HW Trigger | Enable |
| SW Input | Enable |

##### Channel Info
|    Item    | Specification |
|:-------------|:--------------|
| Mode | Server Mode |
| Connection Status | Disconnected |
| DNS | Disable |
| UDP | Disable |
| Remote IP | 0.0.0.0 |
| Local Port | 0 |
| Remote Port | 0 |
| Domain Name | NULL |
| Inactivity Time  | Disable (0) |

###### UART 
|    Item    | Specification |
|:-------------|:--------------|
| Baud Rate | 115200 |
| Data Bit | 8 |
| Stop Bit | 1 |
| Parity | None |
| Flow Ctrl | None |

###### Data Packing Option
|    Item    | Specification |
|:-------------|:--------------|
| Char | Disble (0x00) |
| Size | Disble (0) |
| Time | Disble (0) |

### Reset
모듈의 Reset에는 두 가지 방식이 있다.
MCU의 NRST 핀과 연결된 /RESET 핀을 제어하는 Hardware Reset과 MCU의 GPIO에 연결된 SW_INPUT 핀을 제어하는 Software Reset이다.
Software Reset은 SW_INPUT을 LOW로 유지하는 시간에 따라서 일반 Software Reset과 Factory Reset으로 나누어 진다.

#### Hardware Reset
MCU의 NRST 핀의 규격과 동일하다.

#### Software Reset
SW_Input 핀을 최소 100ms LOW로 유지하면 Software Reset Enable 상태로 진입하게 되고 이 상태에서 SW_Input 핀을 HIGH로 올리면 모듈은 Software Reset된다.

![Software Reset Signal Timing Diagram](./img/usermanual/figure-2.png)

#### Factory Reset
SW_Input 핀을 5초 이상 연속으로 LOW로 유지하면 Factory Reset Enable 상태로 전환된다. 이후에 SW_Input 핀이 HIGH로 변환되면 모듈은 모든 옵션을 초기 설정 값으로 변경하고 Reset한다.

![Factory Reset Signal Timing Diagram](./img/usermanual/figure-3.png)

### Command Mode
HW_TRIGGER 핀을 제어해서 AT Command Mode를 On/Off 할 수 있다.
HW_TRIGGER 핀은 Active Low로 동작하기 때문에 HW_TRIGGER 핀을 LOW로 유지하면 AT Command를 통해서 모듈을 제어할 수 있다.
AT Command를 받아들이는 통신선은 UART1이다. HW_TRIGGER핀이 HIGH를 유지할 때 UART1은 데이터 통신용으로 사용되고 HW_TRIGGER핀이 LOW가 되면 UART1은 AT Command를 송수신하는 통로로 사용된다.
AT Command Set은 AT Commands를 참조하라.

## Configuration Tool

twareLAB Standard Configuration Tool은 twareLAB에서 공급하는 모듈을 설정하기 위해서 사용하는 PC Application이다. 
Windows용과 Linux용 두 가지 버전이 있으며 Freeware로 제공한다.
아래 그림 4는 Configuration Tool을 실행했으면 표시되는 초기 화면의 모습이다.

![부팅시 디버그 메시지 화면](./img/usermanual/figure-4.png)

디바이스 검색, 설정, 리셋, Factory Reset, 펌웨어 업데이트 기능을 수행할 수 있으며, 자세한 툴의 사용법은 “TW100XX Configuration Tool Manual”을 참고하라.
아래 그림은 Device 검색 이후의 화면이다.

![부팅시 디버그 메시지 화면](./img/usermanual/figure-5.png)

다음은 펌웨어 업데이트 화면이다.

![부팅시 디버그 메시지 화면](./img/usermanual/figure-6.png)

정상으로 수행되면 아래와 같은 메시지 창이 뜨게 된다.

![부팅시 디버그 메시지 화면](./img/usermanual/figure-7.png)

## AT Commands
HW_TRIGGER 핀 제어를 통해 AT Command 모드로 전환되면 UART1 포트로 다음과 같은 AT Command를 전송해서 각종 설정 값을 조회하거나 설정을 변경할 수 있다.
주의!) 모든 AT Command는 항상 마지막에 ‘\r\n’([CR][LF])으로 끝나야 한다.

|    Function    | Command Syntax |
|:-------------|:--------------|
| Command Mode 확인 | AT[CR][LF] |
| 모듈 재부팅 | AT+REBOOT[CR][LF] |
| Product ID 확인 | AT+PRODUCTID?[CR][LF] |
| 펌웨어 버전 확인 | AT+VER?[CR][LF] |
| MAC 주소 확인 | AT+MAC?[CR][LF] |
| 등록상태 확인 | AT+REG?[CR][LF] |
| 등록 요청 | AT+REG=[option][CR][LF] |
| 네트워크 정보 확인 | AT+DNETINFO?[CR][LF] |
| 네트워크 정보 설정 | AT+DNETINFO=[ip mode],[local ip],[subnet],[gateway][CR][LF] |
| DNS 서버 주소 확인 | AT+DNSIP?[CR][LF] |
| DNS 서버 주소 설정 | AT+DNSIP=[dns server ip][CR][LF] |
| DNS Query 요청 | AT+DNSQUERY?[domain name][CR][LF] |
| NTP 서버 주소 확인 | AT+NTP?[CR][LF] |
| NTP 서버 주소 설정 | AT+NTP=[ntp server url][CR][LF] |
| 현재 시간 확인 | AT+TIME?[CR][LF] |
| Time Zone 확인 | AT+TZONE?[CR][LF] |
| Time Zone 설정 | AT+TZONE=[time zone][CR][LF] |
| UART 정보 확인 | AT+UART?[CR][LF] |
| UART 정보 설정 | AT+UART=[uart num],[uart*1* setting],...,[uart*n* setting][CR][LF] |
| Peer 정보 확인 | AT+PEERINFO?[CR][LF] |
| Peer 정보 설정 | AT+PEERINFO=[peer num],[peer*1* setting],...,[peer*n* setting][CR][LF] |
| FWUP Start | AT+FWUPSTART=[file size][CR][LF] |
| FWUP Data | AT+FWUPDATA=[data][CR][LF] |
| FWUP Finish | AT+FWUPFINISH[CR][LF] |
| SW INPUT 확인 | AT+SWINPUT?[CR][LF] |
| SW INPUT 설정 | AT+SWINPUT=[option][CR][LF] |
| CRC16 사용 확인 | AT+USECRC16?[CR][LF] |
| CRC16 사용 확인 | AT+USECRC16=[option][CR][LF] |

### Command 모드 확인
#### 명령
*AT[CR][LF]*

#### 응답
*OK[CR][LF]*

#### 예제

### 모듈 재부팅
#### 명령
*AT+REBOOT[CR][LF]*

#### 응답
*+REBOOT[CR][LF]*

*OK[CR][LF]*

#### 예제

### Product ID 확인
#### 명령
*AT+PRODUCTID?[CR][LF]*

#### 응답
*+PRODUCTID=[productid][CR][LF]*

*OK[CR][LF]*

#### 예제

### 펌웨어 버전 확인
#### 명령
*AT+VER?[CR][LF]*

#### 응답
*+VER=[version][CR][LF]*

*OK[CR][LF]*

#### 예제

### MAC 주소 확인
#### 명령
*AT+MAC?[CR][LF]*

#### 응답
*+MAC=[mac addr][CR][LF]*

*OK[CR][LF]*

#### 예제

### 등록 상태 확인
#### 명령
*AT+REG?[CR][LF]*

#### 응답
*+REG=[status][CR][LF]*

*OK[CR][LF]*


### 등록 요청
#### 명령
*AT+REG=[option][CR][LF]*

#### 응답
*+REG=[option][CR][LF]*

*OK[CR][LF]*

#### 예제

### 네트워크 정보 요청
#### 명령
*AT+DNETINFO?[CR][LF]*

#### 응답
*+DNETINFO=[ip mode],[local ip],[subnet],[gateway][CR][LF]*

*OK[CR][LF]*

#### 예제

### 네트워크 정보 설정
#### 명령
*AT+DNETINFO=[ip mode],[local ip],[subnet],[gateway][CR][LF]*

#### 응답
*+DNETINFO=[ip mode],[local ip],[subnet],[gateway][CR][LF]*

*OK[CR][LF]*

#### 예제

### DNS 서버 주소 확인
#### 명령
*AT+DNS?[CR][LF]*

#### 응답
*+DNS=[dns server ip][CR][LF]*

*OK[CR][LF]*

### DNS 서버 주소 설정
#### 명령
*AT+DNS=[dns server ip][CR][LF]*

#### 응답
*+DNS=[dns server ip][CR][LF]*

*OK[CR][LF]*

### NTP 서버 주소 확인
#### 명령
*AT+NTP?[CR][LF]*

#### 응답
*+NTP=[ntp server domain][CR][LF]*

*OK[CR][LF]*

### NTP 서버 주소 설정
#### 명령
*AT+NTP=[ntp server domain][CR][LF]*

#### 응답
*+NTP=[ntp server domain][CR][LF]*

*OK[CR][LF]*

### 현재 시간 확인
#### 명령
*AT+TIME?[CR][LF]*

#### 응답
*+TIME=YYYY/MM/DD/hh:mm:ss,[Day of Week],[Time Zone][CR][LF]*

*OK[CR][LF]*

### Time Zone 설정
#### 명령
*AT+TZONE=[Time Zone][CR][LF]*

#### 응답
*+TZONE=[Time Zone][CR][LF]*

*OK[CR][LF]*

### UART 정보 확인
#### 명령
*AT+UART?[CR][LF]*

#### 응답
*+UART=[uart num],[uart1 setting],...,[uartn setting][CR][LF]*

*OK[CR][LF]*

##### Uart Setting
Uart setting은 개별 옵션을 0 ~ 9 사이의 숫자형 문자로 표현하고 옵션 간에는 Dash(‘-‘) 문자로 연결한다.

옵션의 순서는 다음과 같다.

[BaudRate]-[DataBit]-[StopBit]-[Parity]-[FlowCtrl]-[PackCH]-[PackSize]-[PackTime]-[InactivityTime]

###### BaudRate
|    Baud Rate (bps)    | Value |
|:-------------:|:--------------:|
| 300 | 0 |
| 600 | 1 |
| 1,200 | 2 |
| 2,400 | 3 |
| 4,800 | 4 |
| 9,600 | 5 |
| 19,200 | 6 |
| 38,400 | 7 |
| 57,600 | 8 |
| 115,200 | 9 |
| 230,400 | 10 |
| 460,800 | 11 |
| 921,600 | 12 |
| 1,000,000 | 13 |
| 2,000,000 | 14 |
| 3,000,000 | 15 |

###### DataBit
|    Data Bit    | Value |
|:-------------:|:--------------:|
| 7 (Not Supported Yet) | 0 |
| 8 (Default) | 1 |

###### StopBit
|    Stop Bit    | Value |
|:-------------:|:--------------:|
| 0.5 (Not Supported Yet) | 0 |
| 1 (Default) | 1 |
| 1.5 (Not Supported Yet) | 2 |
| 2 (Not Supported Yet) | 3 |

###### Parity
|    Parity    | Value |
|:-------------:|:--------------:|
| None | 0 |
| ODD | 1 |
| EVEN | 2 |

###### FlowCtrl
|   Flow Ctrl    | Value |
|:-------------:|:--------------:|
| None | 0 |
| XON/XOFF | 1 |
| RTS/CTS | 2 |
| RTS ONLY | 3 |
| Reverse RTS ONLY | 4 |

###### PackCH
문자를 Hex 값으로 표현한다.
Space(= 20), ‘+’ (= 32)

###### PackSize
0 ~ 1000 사이의 값을 문자열로 지정할 수 있다.

###### PackTime
0 ~ 1000 사이의 값을 문자열로 지정할 수 있다.
단위는 millisecond이다.

###### InactivityTime
0 ~ 3600 사이의 값을 문자열로 지정할 수 있다.
단위는 second이다.

### UART 정보 설정
#### 명령
*AT+UART=[uart num],[uart1 setting],...,[uartn setting][CR][LF]*

#### 응답
*+UART=[uart num],[uart1 setting],...,[uartn setting][CR][LF]*

*OK[CR][LF]*

### PEER 정보 확인
#### 명령
*AT+PEERINFO?[CR][LF]*

#### 응답
*+PEERINFO=[peer num],[peer1 setting],...,[peern setting][CR][LF]*

*OK[CR][LF]*

##### Peer Setting
Peer setting은 개별 옵션을 0 ~ 9 사이의 숫자형 문자로 표현하고 옵션 간에는 Dash(‘-‘) 문자로 연결한다.

[Operation Mode]-[Connection Status]-[bDNS]-[bUDP]-[Local Port]-[Remote IP]-[Remote Port]-[Remote Domain]

###### Operation Mode
|    Operation Mode   | Value |
|:-------------:|:--------------:|
| Server Mode | 0 |
| Client Mode | 1 |

###### Connection Status
|    Connection Status    | Value |
|:-------------:|:--------------:|
| Disconnected | 0 |
| Connected | 1 |

###### bDNS
|    DNS    | Value |
|:-------------:|:--------------:|
| Disable | 0 |
| Enable | 1 |

###### bUDP
|    UDP   | Value |
|:-------------:|:--------------:|
| TCP Mode | 0 |
| UDP Mode | 1 |

###### Local Port
0 ~ 65535 사이의 값을 문자열로 표현한다.

###### Remote IP
xxx.xxx.xxx.xxx 형식의 문자열로 표현한다.

###### Remote Port
0 ~ 65535 사이의 값을 문자열로 표현한다.

###### Remote Domain
문자열로 표현한다.
Null 문자열 또는 Domain name을 지정한다.

### PEER 정보 설정
#### 명령
*AT+PEERINFO=[peer num],[peer1 setting],...,[peern setting][CR][LF]*
#### 응답
*+PEERINFO=[peer num],[peer1 setting],...,[peern setting][CR][LF]*
*OK[CR][LF]*