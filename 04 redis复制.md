<img width="804" alt="0ab671561266401637f80bce241d62d1" src="https://github.com/user-attachments/assets/d962c6c4-942f-4b87-bbb6-757f00246c61" />
只用对从库的conf进行配置，而不配置主库
<img width="613" alt="e463abcf2c5505f98101bafe1d0c92ea" src="https://github.com/user-attachments/assets/1c2fe0ec-e4d8-4321-b9e6-17e2c96485a6" />
<img width="729" alt="13b1e11eaa946dff45f1892d8dcd1283" src="https://github.com/user-attachments/assets/4365223f-55df-4722-b1b3-ea61d244588d" />
<img width="275" alt="56c16294a39795319c5d75c44c96c3d1" src="https://github.com/user-attachments/assets/b53014e5-7ba5-4993-b454-bb7eb9383698" />
<img width="616" alt="ec8847b44c522da051b6a5c8d33394bd" src="https://github.com/user-attachments/assets/55adf357-71f2-489b-b0c5-c1d9f71af94b" />
master宕机后，如果没有配置哨兵的话，其他的slave是不能上位的，因为无法触发投票机制
<img width="513" alt="d931465f2fb1692ab69b092aec90edc2" src="https://github.com/user-attachments/assets/22d4a6c6-2b78-4a60-bb90-5417a4bde158" />
主从复制配置在文件中永久生效，启动即生效，而使用slaveof命令在重启后就不生效了
A->B->C,虽然B是c的master但是B仍然不能进行写操作
<img width="632" alt="94d08c6f13f3be8715f7dc75262ae913" src="https://github.com/user-attachments/assets/a8d80a64-a293-4c12-9fe8-a23a72420f60" />
<img width="592" alt="77f32b2e2d3619fb5ccc44d4504591f3" src="https://github.com/user-attachments/assets/16bb9600-f6f7-4715-8784-406368dc1c0a" />
<img width="351" alt="97e210c0e42ab386d4e5d6945e0ed0fc" src="https://github.com/user-attachments/assets/2cf490d6-3f59-48f5-a727-464eba3830c0" />
<img width="596" alt="f65f82477532bee646146bc2cfd96f2f" src="https://github.com/user-attachments/assets/91898a5f-65db-4a05-a7e4-c5b1af5b3dac" />
### 复制的缺点
<img width="495" alt="e8b4b5c93bac0a29b3d1bf3dff7ddc8b" src="https://github.com/user-attachments/assets/1c37219b-5969-40b7-9f05-8b8c2e0c9ecc" />
