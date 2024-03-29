# 保護環(protection rings)

## 簡介

<figure><img src="../.gitbook/assets/protection_rings-min.png" alt="" width="500">
<figcaption>CPU rings</figcaption>
</figure>


保護環是一種用來在發生故障時保護資料和功能，提升容錯度，避免惡意操作 ，提升計算機安全的設計方式。這是一種與能力基礎安全（capability-based security）完全相反的方式。

在計算機體系結構中，保護環是由兩個或更多的特權態組成。在一些硬體或者微代碼級別上提供不同特權態模式的CPU架構上，保護環通常都是硬體強制的。保護環是從最高特權級（通常被叫作0級）到最低特權級（通常對應最大的數字）排列的。在大多數作業系統中，Ring 0擁有最高特權，並且可以和最多的硬體直接交互（比如CPU，記憶體）。

Rings之間的特殊門是被提供用來允許外層Ring在預定義的方式內訪問內層Ring的資源用的，內層Ring可以隨便使用外層Ring的資源。正確使用Rings間的門可以阻止某個Ring或者特權級的程序故意濫用其他程序的資源，提升安全性。例如，某個間諜軟體作為一個在Ring 3運行的使用者行程，它在不通知用戶的時候打開攝影機應該會被阻止，因為訪問硬體需要使用被驅動程序保留的Ring 1的方法。瀏覽器一類在高Ring級別運行的程序必須請求權限才能訪問網絡，也就是受低Ring級別限制的資源。

在 x86 CPU 的保護模式底下，根據處理器權限的不同，又可區分為 Ring 0, 1, 2, 3 等 4 種權限等級。Ring 0 的權限最大，可以直接存取所有硬體；而 Ring 3 的權限最小，沒有任何硬體權限。處理器權限的設計，主要是為了增強容錯的能力。譬如在意外錯誤發生時保護資料內容，或保護系統不被惡意的軟體侵害。

* 對應於作業系統與應用軟體，作業系統的核心 (kernel) 是運行在 Ring 0 的權限下，Ring 1, 2 則都給驅動程式使用，應用程式則運行在 Ring 3。
* 相對作業系統來說，則是簡單分成核心模式(kernel mode)與使用者模式(user mode)。在 模心模式下執行的是可以存取硬體支援的指令動作，而在使用者模式底下的程式，則是只能透過作業系統所提供的系統呼叫函式 (system call)，切換到核心模式下取得資源。

## 為什麼稱為陷入內核 (trap to kernel)?

使用者狀態與內核狀態對CPU 來說的，是指CPU 執行在Ring 3 級還是Ring 0 ，
很多人誤以為是對使用者程式來講的。

**使用者程序式陷入內核狀態是指：由於內部或外部中斷發生，目前程式被暫時終止執行，其上下文被內核的
中斷程式儲存起來後，開始執行一段內核的程式碼**。是內核的程式碼，不是使用者程式在內核的程式碼，使用者程式碼
怎麼可能在內核中存在，所以「使用者狀態與內核狀態」是對CPU 來說的。

當應用程式陷入內核後，以後發生的事，應用程式完全不知道，它的上下文環境已
經被儲存到自己的Ring 0 堆疊中了，那時在CPU 上執行的程式已經是內核程式了。所以要清楚，內核程式碼並不
是成了應用程式的內核化身，作業系統是獨立的部分，使用者程序永遠不會因為進入內核狀態而變身為作業系統。

## 虛擬化層級: Ring -1

當應用程式需要使用到硬體資源時，必須透過作業系統將指令/資料切換到 ring 0 執行，完畢後再將結果送回 ring 3 的應用程式。而中間的轉換過程勢必會降低效率，但是為了安全這也是必要的。然而在虛擬化的需求下，這樣傳統的做法就會導致效能的問題。

虛擬化的應用程式，透過特殊的驅動程式來模擬出硬體層來讓虛擬的作業系統使用，也就是說虛擬作業系統試運行在 ring 3 並沒有直接觸及 ring 0，因此相關硬體動作還是要經過指令切換的動作才能完成。這會導致虛擬作業系統的效能變差，也無發真正發揮硬體的效能而失去實用性。

所以 Intel 在 x86 CPU 上就加上了 VT 虛擬化技術 (AMD 也有類似的 AMD-V 技術)，也就是創造一個新的 CPU 權限 Ring -1，比 ring 0 還要更低，讓虛擬化的軟體執行在這個等級上，而所有虛擬化的指令透過他直接存取硬體，以增強運作的效能。








