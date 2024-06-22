---
date: 2021-07-22
sidebar_position: 2
---

# TWF-100 Script Grammar

## IpType
- USE_JIG_ID_AND_CH_INDEX

## MacType
- USE_JIG_ID_AND_CH_INDEX

## CustomVariableType
- STRING
- INTEGER
- FLOAT
- MAC
- MAC1

## Operator
- NONE
- PLUS
- MINUS
- MULTIPLIED
- DIVIDED

## LogicalOperator
- AND
- OR

## CameraCommand
- READ

## CameraObject
- Enable
- ScanTimeMs

## ChannelBoardConfigObject
- UartConfig:[UartConfig](#uartconfig)
- GpioConfig:[GpioConfig](#gpioconfig)
- AdcConfig:[AdcConfig](#adcCcnfig)
- SpiConfig:[SpiConfig](#spiconfig)
- FirmwareConfig:[FirmwareConfig](#firmwareconfig)

## UartConfig
- ConsoleUart:[ConsoleUart](#consoleuart)
- TargetUart1:[TargetUart](#targetuart)
- TargetUart2:[TargetUart](#targetuart)
- TargetUart3:[TargetUart](#targetuart)
- TargetUart4:[TargetUart](#targetuart)

## ConsoleUart
- BaudRate
- FlowControl

## TargetUart
- Enable
- Baudrate
- FlowControl
- index

## GpioConfig
- InputGpioList:List
- OutputGpioList:List

## AdcConfig
- EnableAdcList:List
- SamplingIntervalMs
- ValueCondition

## FirmwareConfig
- FirmwareType
- FirmwareName

## SpiConfig
- Enable

## TestScheduleObject
- TestName:str
- CustomFunctionControl:[CustomFunctionControl](#customfunctioncontrol)
- CameraContro:[CameraControl](#cameracontrol)
- GpioControl:[GpioControl](#gpiocontrol)
- UartControl:[UartControl](#uartcontrol)
- targetControl:[TargetControl](#targetcontrol)
- lockControl:[LockControl](#lockcontrol)
- NextTestList:List[NextList]

## CustomFunctionControl
- createDummySerial:[CreateDummySerial](#createdummyserial)

## CreateDummySerial
- Enable
- SerialPrefix

## CameraControl
- targetQrRead:[TargetQrRead](#targetqrread)

## TargetQrRead
- Enable:bool
- TimeoutMs:int
- SerialPrefix:str
- SaveDataToCustomVarialbe:SaveDataToCustomVariable

## GpioControl
- TargetGpioRead:[TargetGpioRead](#targetgpioread)
- TargetGpioWriteList:List[TargetGpioWrite](#targetgpiowrite)
- TargetGpioWriteToggle:[TargetGpioWriteToggle](#targetgpiowritetoggle)
- DelayMsBeforeGpioControl:int
- DelayMsAfterGpioControl:int

## TargetGpioRead
- Enable:bool
- GpioName
- WantedValue

## TargetGpioWrite
- Enable
- GpioName
- Value

## TargetGpioWriteToggle
- Enable
- GpioName
- ActiveMethod
- KeepingTimeMs

## UartControl
- TargetUartName:str
- SerialTxInfo:[SerialTxInfo](#serialtxinfo)
- SerialTxListInfo:[SerialTxListInfo](#serialtxlistinfo)
- SerialRxInfo:[SerialRxInfo](#serialrxinfo)
- SerialIterateTxRx:[SerialIterateTxRxInfo](#serialiteratetxrxinfo)

## SerialTxInfo
- Enable:bool
- TxData:bytearray
- TxRepeatCount:int
- TxRepeatIntervalMs:int
- DelayMsBeforeTx:int
- DelayMsAfterTx:int
- TxDataWithCustomVariable:[TxDataWithCustomVariable](#txdatawithcustomvarible)
- TargetGpioWriteToggle:[TargetGpioWriteToggle](#targetgpiowritetoggle)

## TxDataWithCustomVarible
- Enable:bool
- TxDataWithVariable:str
- LoadDataFromCustomVariableList:List[str]

## SerialTxListInfo
- Enable:bool
- TxDataList:List[bytearray]
- DelayMsBeforeTx:int
- DelayMsAfterTx: int

## SerialRxInfo
- Enable:bool
- ExpectedRxDataList:List[str]
- TimeoutMs:int
- LogicalOprator:[LogicalOperator](#logicaloperator)
- SaveDataToCustomVariable:[SaveDataToCustomVariable](#savedatatocustomvariable)

## SerialTxListInfo
- Enable:bool
- TxDataList:List[bytearray]
- DelayMsBeforeTx:int
- DelayMsAfterTx:int

## SerialIterateTxRxInfo
- Enable
- SerialTxListInfo:[SerialTxListInfo](#serialtxlistinfo)
- SerialRxInfo:[SerialRxInfo](#serialrxinfo)

## SaveDataToCustomVariable
- Enable:bool
- CustomVariableList:List[CustomVariable](#customvariable)

## SplitPattern
- SplitPattern:ch
- IndexForUse:int

## RemovePattern
- RemovePattern:ch

## CustomVariable
- LookUpString:str
- SplitPatternList:List[SplitPattern](#splitpattern)
- RemovePatternList:List[RemovePattern](#removepattern)
- CustomVariablename:str
- CustomVariableType:[CustomVariableType](#customvariabletype)
- CustomVariableOperator:str

## TargetControl
- TargetEthernetControl:[TargetEthernetControl](#targetethernetcontrol)
- TargetFirmwareUpdateControl:[TargetFirmwareUpdateControl](#targetfirmwareupdatecontrol)
- TargetCustomControl:[TargetCustomControl](#targetcustomcontrol)

## TargetEthernetControl
- ResetEthernetTarget:[ResetEthernetTarget](#resetethernettarget)
- SetTargetIp:[SetTargetIp](#settargetip)
- SetTargetMac:[SetTargetMac](#settargetmac)
- RunTcpClientTest:[RunTcpClientTest](#runtcpclienttest)
- RunLoopbackServerTest:[RunLoopbackServerTest](#runloopbackservertest)

## ResetEthernetTarget
- Enable:bool
- timeoutMs:int

## SetTargetIp
- Enable:bool
- IpPrefix:str
- IpType:IpType
- SaveDataToCustomVariable:[SaveDataToCustomVariable](#savedatatocustomvariable)
- UseChannelBoard:bool

## SetTargetMac
- Enable:bool
- MacPrefix:str
- MacType:MacType
- SaveDataToCustomVariable:[SaveDataToCustomVariable](#savedatatocustomvariable)
- UseChannelBoard:bool

## ConnectTcp
- Enable:bool

## CloseTcp
- Enable:bool

## SendTcpData
- Enable:bool
- EthernetUseDummyData:[EthernetUseDummyData](#ethernetusedummydata)
- EthernetUseUserData:[EthernetUseUserData](#ethernetuseuserdata)

## VerifyWithSentData
- Enable:bool

## RecvTcpData
- Enable:bool
- RecvTimeoutMs:int
- VeryfyWithSentData:[VerifyWithSentData](#verifywithsentdata)
- VerifyWithUserData:[EthernetUseUserData](#ethernetuseuserdata)

## EthernetUseDummyData
- Enable:bool
- DummyDataSize:int

## EthernetUseUserData
- Enable:bool
- UserData:str

## TcpClientDestinationIp
- Value:str
- LoadDataFromCustomVariableList:List[str]

## RunTcpClientTest
- Enable:bool
- DestinationIp:[TcpClientDestinationIp](#tcpclientdestinationip)
- DestinationPortNumber:int
- ConnectTcp:[ConnectTcp](#connecttcp)
- SendTcpData:[SendTcpData](#sendtcpdata)
- RecvTcpData:[RecvTcpData](#recvtcpdata)
- CloseTcp:[CloseTcp](#closetcp)

## RunLoopbackServerTest
- Enable:bool
- PortNum:int
- DummyDataSize:int
- TimeoutMs:int
- DelayMsAfterNetworkInit:int
- SaveDataToCustomVariable:[SaveDataToCustomVariable](#savedatatocustomvariable)

## TargetFirmwareUpdateControl
- Enable:bool
- Xmodem:[XmodemProtocol](#xmodemprotocol)
- Swd:[SwdProtocol](#swdprotocol)
- Stm32BootProtocol:[Stm32BootProtocol](#stm32bootprotocol)
- W7500BootProtocol:[W7500BootProtocol](#w7500bootprotocol)

## XmodemProtocol
- Enable:bool
- TargetuartName:str
- TargetUartBaudrate:int
- TargetFirmwareNumber:int
- TimeoutMs:int

## SwdProtocol
- Enable:bool
- StartFlashAddress:int
- TargetFirmwareNumber:int
- TimeoutMs:int

## Stm32BootProtocol
- Enable:bool
- BootGpioName:str
- TargetUartName:str
- TargetUartBaudrate:int
- EnableFlashReadProtect:int
- EnableFlashWriteProtect:int
- TargetReset:[TargetReset](#targetreset)
- FirmwareInfoList:List[FirmwareInfo](#firmwareinfo)

## W7500BootProtocol
- Enable:bool
- BootGpioName:str
- TargetUartname:str
- TargetUartBaudrate:int
- EnableFlashReadProtect:int
- EnableFlashWriteProtect:int
- TargetReset:[TargetReset](#targetreset)
- FirmwareInfoList:List[FirmwareInfo](#firmwareinfo)

## FirmwareInfo
- StartFlashAddress:int
- TargetFirmwareNumber:int

## TargetReset
- Enable:bool
- GpioName
- ActiveMethod
- KeepingTimeMs:int

## CheckStringBeforeCommand
- Enable:bool
- Data:str
- TimeoutMs:int

## InputMacAddress
- Enable:bool
- Command:str
- LoadDataFromCustomVariableList:List[str]
- CheckStringBeforeCommand:[CheckStringBeforeCommand](#checkstringbeforecommand)

## TargetFirmwareUpdateControl
- Enable:bool
- Xmodem:[XmodemProtocol](#xmodemprotocol)
- Swd:[SwdProtocol](#swdprotocol)
- StmreBootProtocol:[Stm32BootProtocol](#stm32bootprotocol)
- W7500BootProtocol:[W7500BootProtocol](#w7500bootprotocol)

## WiznetWIZ107SRConfigTool
- Enable:bool
- MacAddress
- Command
- LoadDataFromCustomVariableList:List[str]
- TimeoutMsCommand:int

## WiznetWIZ750SRConfigTool
- Enable:bool
- MacAddress
- Command
- LoadDataFromCustomVariableList:List[str]
- TimeoutMsCommand:int

## WiznetWIZ750SRSearch
- Enable:bool
- MacAddress
- LoadDataFromCustomVariableList:List[str]
- TimeoutMsSearchCommand:int

## WiznetWIZ750SRFactoryReset
- Enable:bool
- MacAddress
- LoadDataFromCustomVariableList:List[str]
- TimeoutMsSearchCommand:int

## WiznetWIZ550SRFactoryReset
- Enable:bool
- MacAddress
- LoadDataFromCustomVariableList:List[str]
- TimeoutMsSearchCommand:int

## WiznetWIZ1XXSRSearch
- Enable:bool
- MacAddress
- LoadDataFromCustomVariableList:List[str]
- TimeoutMsSearchCommand:int
- CheckDefaultValues:bool
- DefaultIpAddress:str
- DefaultGwAddress:str

## WiznetWIZ1XXSRSetting
- Enable:bool
- MacAddress
- LoadDataFromCustomVariableList:List[str]
- TimeoutMsSearchCommand:int
- IpAddress:str
- GwAddress:str

## TargetCustomControl
- WiznetWIZ107SRConfigTool:[WiznetWIZ107SRConfigTool](#wiznetwiz107srconfigtool)
- WiznetWIZ750SRConfigTool:[WiznetWIZ750SRConfigTool](#wiznetwiz750srconfigtool)
- WiznetWIZ550SRFactoryReset:[WiznetWIZ550SRFactoryReset](#wiznetwiz550srfactoryreset)
- WiznetWIZ1XXSRSearch:[WiznetWIZ1XXSRSearch](#wiznetwiz1xxsrsearch)
- WiznetWIZ1XXSRSetting:[WiznetWIZ1XXSRSetting](#wiznetwiz1xxsrsetting)

## LockControl
- LockOrWaitForRelease:[LockOrWaitForRelease](#lockorwaitforrelease)
- LockRelease:[LockRelease](#lockrelease)

## LockOrWaitForRelease
- Enable:bool
- TimeoutMs:int

## LockRelease
- Enable:bool

## NextTest
- NextTestname:str
- LogicalOperator:[LogicalOperator](#logicaloperator)
- CompareRxData:[CompareRxData](#comparerxdata)
- IncludedStringInRxData:[IncludedStringInRxData](#includedstringinrxdata)
- IncludedCustomVariableInRxData:[IncludedCustomVariableInRxData](#includedcustomvariableinrxdata)

## CompareRxData
- Enable:bool
- ConditionString:str
- CustomVariableForConditionStringList:List[str]

## IncludedStringInRxData
- Enable:bool
- ValueList:List[str]
- LogicalOperator:[LogicalOperator](#logicaloperator)

## IncludedCustomVariableInRxData
- Enable:bool
- CustomVariablenameList:List[str]
- LogicalOperator:[LogicalOperator](#logicaloperator)
- RemoveSeperate:str
- ChangeUpperCase:bool





