# Docker CLI 操作

### 產生與執行

1. docker run &lt;image name&gt;  \(&lt;command&gt;\)：由image檔產生container並執行指令，有&lt;command&gt; 實則此指令會取代預設指令執行
2. docker create &lt;image name&gt; \(&lt;command&gt;\)：透過image建立容器，回傳container id
3. docker start \(-a\)  &lt;container id&gt;：啟動指定容器，-a回傳執行結果，否則回傳container id，重啟時不可改變建立時的指令。

![docker start &#x4E0D;&#x53EF;&#x6539;&#x8B8A;create&#x6642;&#x4E0B;&#x7684;&#x6307;&#x4EE4;](../.gitbook/assets/jie-tu-20200825-xia-wu-2.45.19.png)

### 查詢

1. docker ps：取得所有正在運行中的 container。
2. docker ps --all \(or -a\)：取得所有container。
3. docker logs &lt;container id&gt;：不重複執行，取得container紀錄日誌。

### 刪除

1. docker system prune：刪除所有container \(不論狀態\)。
2. docker stop &lt;container id&gt;：停止container，由程序正常終止\(10秒後未終止呼叫kill\)。
3. docker kill &lt;container id&gt;：強制終止container \(不論狀態\)

### Container的生命週期

![credit to: https://github.com/docker/cli](../.gitbook/assets/cjzfmmgxaaqv1_x.png)


