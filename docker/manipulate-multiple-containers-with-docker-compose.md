# Docker Compose操作複數容器

### 管控複數容器

在操作docker的時候，假設架構上需要啟多個服務以提高使用者體驗，就會遇到多個container溝通的問題，畢竟，**container之間預設是不能相互溝通的**。舉例來說，假設一個Node的系統要紀錄使用者造訪次數，如果各自在container中建立redis紀錄，就會有下圖的問題：

![credit to: Stephen Grider](../.gitbook/assets/jie-tu-20200831-xia-wu-2.42.06.png)

比較好的架構則則會是下圖的架構，Node系統可以由多個container負責操控，而紀錄造訪次數的Redis則僅架設在一個container中供所有人共用，類似於Design Pattern中Singleton的概念。

![credit to: Stephen Grider](../.gitbook/assets/jie-tu-20200831-xia-wu-3.26.35.png)



