### 1.作用
用于解决频繁的redis请求，响应的往返带来的性能瓶颈，是一种批处理命令（mset）的优化措施，因为mset只针对string类型的key
### 2.用法
一句话在linux命令行中 cat pipe.txt | redis-cli -a 931886861 --pipe其中pipe.txt文件中存放各种类型的命令集合
<img width="788" alt="6a84c8ef9c936165476823427b836381" src="https://github.com/user-attachments/assets/6ab56c08-3b7d-4322-b9a2-a70bc33c5bfb" />
执行管道中的命令不会阻塞其他命令的执行，但是会占用redis服务器（阻塞服务器），因此管道中的命令太多要分多批次处理
