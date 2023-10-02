# 初入 Docker easy-to-use_Docker

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
    -->
    FROM nginx
    COPY . /usr/share/nginx/html
```
這讓我想到當兵時的站住口令<br>
大概是當兵太精實一直在懷念...<br>

docker Image 建立 html server
```
<!-- docker build -t {{REPOSITORY_NAME}}:{{VERSION}} {{DOCKER_LOCATION}} -->
    docker build -t html-server-image:v1 .
```
### run docker container
執行後等個幾秒讓他建立環境就成功了
```
    docker run -d -p 80:80 html-server-image:v1
```
<hr>

### docker push
```docker images```找到你要上傳檔案<br>
![09-22_006](https://github.com/king707348/easy-to-know_Docker/assets/48721403/a8c556ae-06dd-4f2c-a330-a741a7376f23)<br>
如果沒tag記得賦予 才能上傳
```
<!-- docker tag {{IMAGE_ID}} {{ACCOUNT_NAME}}/{{REPOSITORY_NAME}}:{{VERSION}} -->
    docker tag ff6427fb7991 evanhsu1991/html-server-image:v1
```
沒給版本會顯示latest變成你指定版號<br>
最後用```docker push```指令就完成了
```
    docker push evanhsu1991/html-server-image:v1
```
很多指令跟github很像 難怪很多說會github就會docker 但我還是花很多時間XD

### docker save
儲存到本機
```
<!-- docker save {{ACCOUNT_NAME}}/{{REPOSITORY_NAME}} -o {{SAVE_TYPE}} -->
    docker save evanhsu1991/html-server-image:v1 -o js.tar  
```
