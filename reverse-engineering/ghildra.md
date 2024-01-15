# Ghildra

## 簡介

在 2019 年的 RSA 會議上，NSA 高級網路安全顧問 Rob Joyce 發表了 Get Your Free NSA Reverse Engineering Tool 的議題，解釋了 Ghidra 的獨特功能和特性，並行布了 Ghidra 二進位程式。在當年的 4 月 4 日，NSA 在 GitHub 上公佈了 Ghidra 原始碼。

Ghidra是一個軟體逆向工程（SRE）框架，包括一套功能齊全的高階軟體分析工具，使使用者能夠在各種平台上分析編譯後的程式碼，包括Windows、Mac OS和Linux。功能包括反組譯，組譯，反編譯，繪圖和指令碼，以及數百個其他功能。Ghidra支援各種處理器指令集和可執行格式，可以在使用者互動模式和自動模式下執行。使用者還可以使用公開的API開發自己的Ghidra外掛和指令碼。

軟體逆向工程工具本就不多，特別是在軟體靜態分析工具方面，Ghidra 是少數能與 IDA Pro 比肩的軟體。

## 修改軟體字型

[https://github.com/NationalSecurityAgency/ghidra/issues/83](https://github.com/NationalSecurityAgency/ghidra/issues/83)

修改檔案`$GHIDRA_HOME/support/launch.properties` 中的`VMARGS_LINUX=-Dsun.java2d.uiScale=1`改為`VMARGS_LINUX=-Dsun.java2d.uiScale=2`

或是 `VMARGS=-Dfont.size.override=18`

## 參考資料

* [Ghidra官方網站](https://ghidra-sre.org/)
  * [Ghidra快速鍵](https://ghidra-sre.org/CheatSheet.html)
  * [Ghidra github](https://github.com/NationalSecurityAgency/ghidra)
* [\[平安銀河實驗室\] 使用Ghidra P-Code進行輔助逆向分析](https://galaxylab.pingan.com.cn/%E4%BD%BF%E7%94%A8ghidra-p-code%E8%BF%9B%E8%A1%8C%E8%BE%85%E5%8A%A9%E9%80%86%E5%90%91%E5%88%86%E6%9E%90/)
* [CTF 競賽入門指南(CTF All In One)：Ghidra](https://www.bookstack.cn/read/CTF-All-In-One/doc-2.2.6\_Ghidra.md)
* [Chris Eagle and Kara Nance, The Ghidra Book: The Definitive Guide, No Starch Press, 2020.](https://www.amazon.com/Ghidra-Book-Definitive-Guide-ebook/dp/B0852N9Y4Q)
  * [\[中文\] Ghidra權威指南](https://github.com/firmianay/ghidra-book)。

#### Ghidra extension

* [\[github\] GhidRust](https://github.com/DMaroo/GhidRust)
