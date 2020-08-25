# Container 基礎

### 作業系統運作方式

Docker是用來管理Container的工具，真正內容或檔案的運行仍舊是透過container來執行，要了解container之前，要先提到作業系統運作的模式：

![credit to: Stephen Grider](../.gitbook/assets/jie-tu-20200825-shang-wu-11.13.23.png)

在電腦中，每一個應用程式都會透過系統呼叫 \(system call\) 來和作業系統的核心 \(kernel\)，再交由核心去調用需要使用的資源，如上圖中的CPU、Memory、硬碟空間等。

### 切割命名空間

在Docker和container的概念出現之前，為了解決應用程式上環境需求的衝突，我們會使用命名空間的方式，在硬碟中切割出不同空間以存放不同的需求程式，如下圖所示。

![credit to: Stephen Grider](../.gitbook/assets/jie-tu-20200825-shang-wu-11.52.29.png)

### Container的概念

下圖闡述了一個container大致包含的概念，其實就是包含應用程式程序、作業系統核心以及相對應所需要的資源。

![credit to: Stephen Grider](../.gitbook/assets/jie-tu-20200825-shang-wu-11.57.02.png)

對應到Docker Image，一個Image可以分為兩個部分，第一部分是檔案系統的快照\(File System snapshot\)，就是將檔案系統的對應等等都複製存取，另一部分則是要對存取的程序下的指令 \(command\) 。

![credit to: Stephen Grider](../.gitbook/assets/jie-tu-20200825-shang-wu-11.58.29.png)

所以實際運行上，container會按照Docker CLI的指令建立，並獨立出一部分硬碟空間，再將檔案系統的快照放入該硬碟空間，最後再透過核心 \(kernel\) 拿取需要的資源並執行指令。

