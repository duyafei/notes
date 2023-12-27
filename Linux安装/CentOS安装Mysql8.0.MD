#### 1. 查看mariadb是否安装
    rpm -qa | grep mariadb

#### 2. 如果mariadb存在则删除
    rpm -e --nodep mariadb

#### 3. 查看mysql是否安装
    rpm -qa | grep mysql

#### 4. 如果msyql存在则删除
    rpm -e --nodep mysql

#### 5. 下载rpm包
     wget http://repo.mysql.com/mysql80-community-release-el7-1.noarch.rpm

#### 6. 安装rpm包
    yum isntall mysql80-community-release-el7-1.noarch.rpm

#### 7. 安装mysql
    yum install mysql-server
    
#### 8. 如果出现源 "MySQL 8.0 Community Server" 的 GPG 密钥已安装，但是不适用于此软件包。请检查源的公钥 URL 是否配置正确。使用以下方法
    yum install mysql-server --nogpgcheck

#### 9. 运行mysql
    systemctl start mysqld

#### 10. 获取密码
    grep 'temporary password' /var/log/mysqld.log

#### 11. 登陆mysql
    mysql -uroot -p

#### 12. 修改密码
    ALTER USER 'root'@'localhost' IDENTIFIED BY 'Tjzs#2023';

#### 13. 开启对外访问
    use mysql;
    update user set host='%' where user='root';
    flush privileges;

