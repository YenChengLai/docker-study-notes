# Docker Compose操作複數容器

### 管控複數容器

在操作docker的時候，假設架構上需要啟多個服務以提高使用者體驗，就會遇到多個container溝通的問題，畢竟，**container之間預設是不能相互溝通的**。舉例來說，假設一個Node的系統要紀錄使用者造訪次數，如果各自在container中建立redis紀錄，就會有下圖的問題：

![credit to: Stephen Grider](../.gitbook/assets/jie-tu-20200831-xia-wu-2.42.06.png)

比較好的架構則則會是下圖的架構，Node系統可以由多個container負責操控，而紀錄造訪次數的Redis則僅架設在一個container中供所有人共用，類似於Design Pattern中Singleton的概念。

![credit to: Stephen Grider](../.gitbook/assets/jie-tu-20200831-xia-wu-3.26.35.png)

### Docker Compose是什麼

要使Container之間彼此能夠溝通，開發人員可以透過對本機溝通來達到這個目的，譬如指定各container對應到本地端的指定port號，但這麼做的代價就是我們要使用複雜的指令才能做到。然而使用docker compose可以幫助我們輕鬆做到這件事，究竟什麼是docker compose：

1. 是docker中的另一套獨立的CLI，在安裝docker時已一併安裝。
2. 用來同時啟動多個docker container。
3. 自動設定container溝通時需要傳給docker run的複雜參數。





