# Docker Volume 基礎

### Container 會遇到的問題

前面提過docker image會將檔案的快照\(snapshot\)保存，並以此建立container來運作；也就是說，container中的**環境並不會跟外界產生連動**，而是在image建立的當下就決定了。

![credit to: Stephen Grider](../.gitbook/assets/jie-tu-20200825-shang-wu-11.58.29.png)

這個情境下會有資料無法轉移的痛點。舉例而言，假設我今天要把建立在docker container中的My SQL DB升級，如果關掉原本的container後再啟動另一個新版本的container，資料就會全部留在舊的container中。

### Docker Volume

上述資料轉移，或者說是容器內部資料的對應，都可以透過Docker Volume得到解決，Docker Volume的運作概念如下圖：

![credit to: Stephen Grider](../.gitbook/assets/jie-tu-20200904-shang-wu-11.52.02.png)

以指定參照的方式取代檔案快照，這麼一來container中操作的資料就會和本地的資料產生連動，container操作的資料也會留在本地端檔案路徑中，如此一來，當本地端的檔案有變動時，也會連動到container中的檔案，而不用一直跑docker run來重包image檔。

#### Docker Volume的指令如下：

![credit to: Stephen Grider](../.gitbook/assets/jie-tu-20200904-xia-wu-3.11.11.png)

-v指令代表volume

* -v /app/node\_modules  =&gt;  設定書籤，該路徑不做任何參照
* -v $\(pwd\):/app  =&gt;  以：做為參照對應，前代表本地路徑，後代表container內路徑
* $\(pwd\) =&gt; present working directory，這個系統參數會取得目前工作目錄的路徑

### 使用Docker Compose簡化指令

在docker compose的章節有提到，docker compose可以用來設定需要傳給docker run的複雜參數，因此我們也可以在docker-compose.yml中設定docker volume的設定：

![](../.gitbook/assets/jie-tu-20200904-xia-wu-4.48.21.png)

在 -v 指令中的參數直接寫在docker compose檔案的volumes中，就能夠直接簡化我們下docker run的指令了，唯一不同的是$\(pwd\)是系統參數指令，在docker compose中因為會直接在該路徑執行，以 . 代表現在目錄位置即可。

