# 在 Linux 啟動 UEFI Secure Boot 導致不能 VirtualBox 不能起動虛擬機

## 問題

建立虛擬機並執行時，出現錯誤，導致不能起動虛擬機。

解法1: 直接從BIOS關閉secure boot，關閉後，即可直接執行VirtualBox。

解法2: 將VB的核心模組簽章。



* [https://ozlabs.org/docs/uefi-secure-boot-impact-on-linux.pdf](https://ozlabs.org/docs/uefi-secure-boot-impact-on-linux.pdf)
* [https://askubuntu.com/questions/1455974/signing-virtualbox-modules-with-efi-secure-boot-enabled](https://askubuntu.com/questions/1455974/signing-virtualbox-modules-with-efi-secure-boot-enabled)
