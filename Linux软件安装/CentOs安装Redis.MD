#### 1. 安装redis
    yum install redis

#### 2. 启动redis
    systemctl start redis

#### 3. 开启对外访问
    vim /etc/redis.conf
    
    # 注释下面这行
    bind 127.0.0.1
    
#### 4. 重启redis
    systemctl restart redis