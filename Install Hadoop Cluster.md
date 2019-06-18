# Install CDH Cluster

### 1. Start Cloudera Manager Server
<pre>
sudo systemctl start cloudera-scm-server

sudo tail -f /var/log/cloudera-scm-server/cloudera-scm-server.log
</pre>

### 2. Server 접속
<pre>
http://<server_host>:7180
</pre>


### 3. 서비스 구성

![ex_screenshot](./캡처_cluster구성.png)
