# horsedb
HorseDB是一款以rocksdb作为存储引擎的数据库,兼容了Mysql协议,适合写多读少场景  

# 依赖环境
| 软件	 | 要求 |
| ----- | ----- |
| gcc版本 | 需要支持c++14,最好7或以上 |
| cmake版本 | 3.10及以上版本 |
| horse-rpc版本 |  最新版本 |
| horse-raft版本 |  最新版本 |
| iguana版本 | 最新版本 |
| snappy | 1.1.7 |
# 特性
1, 支持Mysql协议  
2, 支持raft一致性协议多副本备份   
3, 适合写多读少场景  



# 编译和安装  
如果gcc 版本太旧,先升级gcc版本 到7.3    
1,yum -y install centos-release-scl     
2,yum -y install devtoolset-7-gcc devtoolset-7-gcc-c++ devtoolset-7-binutils   
3,scl enable devtoolset-7 bash  
scl命令启用只是临时的，退出shell或重启就会恢复原系统gcc版本,所以这种方式不会污染原来的编译环境。  
如果要长期使用gcc 7.3的话,执行：
echo "source /opt/rh/devtoolset-7/enable" >>/etc/profile   

以下步骤开始安装horsedb   
1,git clone https://github.com/hezhihua/horsedb.git  
2,mkdir build && cd build && cmake ..  && make 

# 用法  
安装完horsedb后,启动horsedb  
./horsedb-server ./config/server.cfg.yaml   
启动成功后，可以用Mysql客户端直接连接登录到horsedb ,如  
mysql  -u hzh -h 0.0.0.0  -P 8083 -p'hzh' test   

create database dbtest  
create table tbname  

show databases;  
show tables;  

insert into tbname() values();  
select * from tbname;  

# TODO   
1,delete、update语法,group by等语法  
2,事务实现  


# 感谢
1,horsedb底层用[RocksDB](https://github.com/facebook/rocksdb)作为存储引擎  
2,列和索引等数据的组织结构参考了[tidb](https://github.com/pingcap/tidb)的设计理念  

# 学习和交流
QQ群:1124085420  
