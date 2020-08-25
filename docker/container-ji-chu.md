# Container 基礎

Docker是用來管理Container的工具，真正內容或檔案的運行仍舊是透過container來執行，要了解container之前，要先提到作業系統運作的模式：

![credit to: Stephen Grider](../.gitbook/assets/jie-tu-20200825-shang-wu-11.13.23.png)

在電腦中，每一個應用程式都會透過系統呼叫 \(system call\) 來和作業系統的核心 \(kernel\)，再交由核心去調用需要使用的資源，如上圖中的CPU、Memory、硬碟空間等。

