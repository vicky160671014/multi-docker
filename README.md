## Docker課程練習筆記
此為Stephen Grider課程的實作練習-multi-container，以下為簡短紀錄以便於複習
<br>
### Development時期架構
![image](https://github.com/vicky160671014/multi-docker/blob/e31fa339a17c64211d525042b85c64b2253ceb08/dev_phase_diagram.jpg)
於docker-compose-dev.yml檔案中，在services寫入共六項服務: 
* nginx-做為總route的功能
* client-前端react
* api-後端api，存取postgres
* worker-存取redis
* postgres
* redis

### Production時期架構
![image](https://github.com/vicky160671014/multi-docker/blob/e31fa339a17c64211d525042b85c64b2253ceb08/prod_phase_diagram.jpg)
於docker-compose.yml檔案中，在services寫入共四項服務，然後推上github再經travisCI測試後佈署於AWS EB:
* nginx
* client
* server-api
* worker<br>
<br>
-postgres部分改接AWS RDS服務，redis部分改接AWS Elastic Cache；比起在EB裡面啟動容器自行維運資料庫，生產階段使用雲端資料庫服務有更多優點，例如:備份、擴展、安全性等等<br>
-圖片來源:Stephen Grider Udemy課程
