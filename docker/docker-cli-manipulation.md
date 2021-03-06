# Docker CLI 操作

### 產生與執行

1. docker run &lt;image name&gt;  \(&lt;command&gt;\)：由image檔產生container並執行指令，有&lt;command&gt; 實則此指令會取代預設指令執行
2. docker create &lt;image name&gt; \(&lt;command&gt;\)：透過image建立容器，回傳container id
3. docker start \(-a\)  &lt;container id&gt;：啟動指定容器，-a回傳執行結果，否則回傳container id，重啟時不可改變建立時的指令，如下圖一。
4. docker exec \(param\) &lt;container id&gt; &lt;command&gt;：以某個**已建立**的container執行指令，param可以為以下三種情況：

* -i：代表input，可以將指令輸入至指定的container中執行，即透過Linux程序溝通的STDIN輸入，如下圖二。此指令常用於同個Image起多個container時彼此溝通用。
* -t：給container配置一個虛擬的終端機，簡言之，讓輸出的排版更好看，通常會搭配-i以-it的形式一起使用。
* -d：讓container進入背景執行。

![&amp;lt;&#x5716;&#x4E00;&amp;gt;  docker start &#x4E0D;&#x53EF;&#x6539;&#x8B8A;create&#x6642;&#x4E0B;&#x7684;&#x6307;&#x4EE4;](../.gitbook/assets/jie-tu-20200825-xia-wu-2.45.19.png)

![&amp;lt;&#x5716;&#x4E8C;&amp;gt;  credit to: Stephen Grider](../.gitbook/assets/jie-tu-20200825-xia-wu-4.02.16.png)

#### 圖二說明

在Linux的作業系統中，每個執行程序都有三種溝通方式，分別為STDIN\(standard input\)、STDOUT \(standard output\) 和STDERR \(standard error\)，docker exec -i 指令即代表透過開啟STDIN將指令輸入至container中操作。

### 查詢

1. docker ps：取得所有正在運行中的 container。
2. docker ps --all \(or -a\)：取得所有container。
3. docker logs &lt;container id&gt;：不重複執行，取得container紀錄日誌。

### 刪除

1. docker system prune：刪除所有container \(不論狀態\)。
2. docker stop &lt;container id&gt;：停止container，由程序正常終止\(10秒後未終止呼叫kill\)。
3. docker kill &lt;container id&gt;：強制終止container \(不論狀態\)。

### 在container內執行終端機

1. docker run -it &lt;image name&gt; -sh：在啟動時用shell在container中執行終端機介面。
2. docker exec -it &lt;container id&gt; -sh：在已啟動的container用shell在container中執行終端機介面。

最常用的模式為2，因為使用1時無法執行該container中其他程序，而2可以**另外開啟**一個終端機執行而不影響主程序。

### Container的生命週期

![credit to: https://github.com/docker/cli](../.gitbook/assets/cjzfmmgxaaqv1_x.png)



