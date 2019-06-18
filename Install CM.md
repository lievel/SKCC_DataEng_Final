# Install CM

### 1. repo file download - 모든 host
<pre>
sudo yum install wget

sudo wget https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/cloudera-manager.repo -P /etc/yum.repos.d/

sudo rpm --import https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/RPM-GPG-KEY-cloudera
</pre>

### 2. jdk 설치
<pre>
sudo yum install oracle-j2sdk1.7

export JAVA_HOME=/usr/java/jdk1.7.0_67-cloudera
export PATH=$PATH:$JAVA_HOME/bin

</pre>

### 3. CM server install
CM Server 설치
<pre>
sudo yum install cloudera-manager-daemons cloudera-manager-server
</pre>

agent 설치 및 실행 - 모든 host
<pre>
sudo yum install cloudera-manager-daemons cloudera-manager-agent

sudo vi /etc/cloudera-scm-agent/config.ini

# Hostname of the CM server의 host 명으로 수정
server_host=host1

sudo systemctl start cloudera-scm-agent

sudo service cloudera-scm-agent restart //start 되었는지 확인
</pre>
