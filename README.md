# 初入 Docker easy-to-know_Docker

### download Docker
先到Docker官網下載: <a href="https://www.docker.com/">Docker Desktop</a> 並建立帳戶<br>
windows要打開Hyper-V才能跑起來<br>
控制台/程式和功能/開啟或關閉windows功能 打開Hyper-V

### run docker
這邊示範如何在docker上跑靜態網站 先在docker拉nginx下來
```
    docker pull nginx
```
跑完後你會在Docker Desktop的Images看到nginx<br>
或是你習慣用cmd看 指令```docker images```列出Images<br>

到資料夾建立index.html 和 Dockerfile
```
<!-- Dockerfile -->
<!--
FROM 環境:版號
COPY 複製檔案位置 到哪裡
>
FROM nginx
COPY . /usr/share/nginx/html
```

docker Image 建立 html server
```
<!-- docker build -t name:版本號 docker位置 -->
docker build -t html-server-image:v1 .
```
### run docker container
執行後等個幾秒讓他建立環境就成功了
```
docker run -d -p 80:80 html-server-image:v1
```

