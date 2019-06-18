# Install Mysql

### 1. MySQL  install
<pre>
sudo wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm

sudo rpm -ivh mysql-community-release-el7-5.noarch.rpm
sudo yum update
sudo yum install mysql-server
sudo systemctl start mysqld

sudo /usr/bin/mysql_secure_installation

[...]
Enter current password for root (enter for none):
OK, successfully used password, moving on...
[...]
Set root password? [Y/n] Y
New password:
Re-enter new password:
Remove anonymous users? [Y/n] Y
[...]
Disallow root login remotely? [Y/n] N
[...]
Remove test database and access to it [Y/n] Y
[...]
Reload privilege tables now? [Y/n] Y
All done!

</pre>

### 2. JDBC Driver install
<pre>

tar zxvf mysql-connector-java-5.1.47.tar.gz

sudo mkdir -p /usr/share/java/
cd mysql-connector-java-5.1.47
sudo cp mysql-connector-java-5.1.47-bin.jar /usr/share/java/mysql-connector-java.jar

</pre>

### 3. Creating Databases for Cloudera Software
<pre>
mysql -u root -p

CREATE DATABASE scm DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;
GRANT ALL ON scm.* TO 'scm'@'%' IDENTIFIED BY 'training';

CREATE DATABASE amon DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;
GRANT ALL ON amon.* TO 'amon'@'%' IDENTIFIED BY 'training';

CREATE DATABASE rman DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;
GRANT ALL ON  rman.* TO 'rman'@'%' IDENTIFIED BY 'training';


CREATE DATABASE hue DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;
GRANT ALL ON hue.* TO 'hue'@'%' IDENTIFIED BY 'training';

CREATE DATABASE metastore DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;
GRANT ALL ON metastore.* TO 'hive'@'%' IDENTIFIED BY 'training';

CREATE DATABASE sentry DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;
GRANT ALL ON sentry.* TO 'sentry'@'%' IDENTIFIED BY 'training';

CREATE DATABASE nav DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;
GRANT ALL ON nav.* TO 'nav'@'%' IDENTIFIED BY 'training';

CREATE DATABASE navms DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;
GRANT ALL ON navms.* TO 'navms'@'%' IDENTIFIED BY 'training';

CREATE DATABASE oozie DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;
GRANT ALL ON oozie.* TO 'oozie'@'%' IDENTIFIED BY 'training';

SHOW GRANTS FOR 'amon'@'%';

</pre>

### 4. Preparing the Cloudera Manager Server Database
<pre>
sudo /usr/share/cmf/schema/scm_prepare_database.sh <databaseType> <databaseName> <databaseUser>

sudo /usr/share/cmf/schema/scm_prepare_database.sh mysql scm scm training
sudo /usr/share/cmf/schema/scm_prepare_database.sh mysql amon amon training
sudo /usr/share/cmf/schema/scm_prepare_database.sh mysql rman rman training

sudo /usr/share/cmf/schema/scm_prepare_database.sh mysql hue hue training
sudo /usr/share/cmf/schema/scm_prepare_database.sh mysql metastore hive training
sudo /usr/share/cmf/schema/scm_prepare_database.sh mysql sentry sentry training

sudo /usr/share/cmf/schema/scm_prepare_database.sh mysql nav nav training
sudo /usr/share/cmf/schema/scm_prepare_database.sh mysql navms navms training
sudo /usr/share/cmf/schema/scm_prepare_database.sh mysql oozie oozie training

</pre>