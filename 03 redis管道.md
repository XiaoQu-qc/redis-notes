### 1.作用
用于解决频繁的redis请求，响应的往返带来的性能瓶颈，是一种批处理命令（mset）的优化措施，因为mset只针对string类型的key
### 2.用法
一句话在linux命令行中 cat pipe.txt | redis-cli -a 931886861 --pipe其中pipe.txt文件中存放各种类型的命令集合
