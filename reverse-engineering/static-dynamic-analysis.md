# 靜態/動靜分析

## 靜態分析動態分析

簡單的說：

* 靜態分析：在不執行目標程式下的情況進行分析。
* 動態分析：在執行目標程式下的情沿進行分析。

靜態分析會檢視存在於磁碟上的特定檔案的內容，而不是觸發時出現的特定檔案。靜態分析會剖析資料，擷取模式、屬性和構件，並標記異常。

透過動態分析，可以在虛擬機器器 (例如惡意軟體分析環境) 中觸發可疑的檔案，並對其進行分析以檢視其行為。根據執行時的操作對檔案進行分級，而不需要倚靠特徵碼來識別威脅。動態分析因此能夠識別與以往不同的威脅。

## 靜態分析

* \[Win, Linux, Mac] [IDA pro](https://hex-rays.com/ida-pro/)
* \[java平台] [Ghidra](https://ghidra-sre.org/)
* [Radare2](https://rada.re/n/)
* [binary ninja](https://binary.ninja/)

## 除錯器(debugger)

* \[Win] [OllyDbg (已停止開發)](https://www.ollydbg.de/)

## 系統監控

* \[Win] [Process monitor](https://learn.microsoft.com/en-us/sysinternals/downloads/procmon)即時監視檔案系統、登入、程序、執行緒和DLL 活動。

## 網路監控

* [Wireshark](https://www.wireshark.org/)
* [tcpdump/libpcap](https://www.tcpdump.org/)

## 指令
