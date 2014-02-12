centos6-redis-init
==================

### init script for Redis on Centos

#### Install Redis

Check the redis laster version http://redis.io/download

```bash
wget http://download.redis.io/releases/redis-2.8.5.tar.gz
tar xzf redis-2.8.5.tar.gz
cd redis-2.8.5
make
```

#### Redis config
```bash
# 下載redis配置sample文件，根據實際需要修改
wget https://raw.github.com/JackLam/centos6-redis-init/master/redis.conf.sample
cp redis.conf.sample /etc/redis.conf
```

#### Add to service
```bash
wget https://raw.github.com/JackLam/centos6-redis-init/master/script/redis-server
mv redis-server /etc/init.d
chmod 755 /etc/init.d/redis-server
chkconfig --add redis-server
chkconfig --level 345 redis-server on
vi /etc/sysctl.conf
# vm.overcommit_memory = 1
sysctl vm.overcommit_memory = 1
service redis-server start
```
