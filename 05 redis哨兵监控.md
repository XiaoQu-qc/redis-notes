### 1.哨兵的作用
1）监控redis运行状态，包括master和slave
2）当master宕机时，根据某一种选举算法，使其中一个slave成为master（master宕机时，无法向redis写入数据，此时系统将会瘫痪，因此必须立刻重新产生以master）
<img width="638" alt="aa8893a821b392f471a276418843afbc" src="https://github.com/user-attachments/assets/9f5dfb4d-7e33-4b74-bc7e-bf5b659395b0" />

自己的理解：主从复制+哨兵是一套组合拳，主要是用来解决master宕机时，重新选举master的。另一套是用redis集群。
哨兵的作用只是监控，无法做数据的处理
配置多个哨兵的目的是防止master和哨兵同时宕机，这种情况就起不到哨兵监控的作用
<img width="561" alt="3ab62638bf01676617d6c9efc459d2fb" src="https://github.com/user-attachments/assets/75f50f20-97f1-493d-8545-795824fa771a" />

<img width="484" alt="39ef769a069c990dfe984ad81c6adf0d" src="https://github.com/user-attachments/assets/b0e678af-a913-4d9d-adb4-4c497b699cf1" />

哨兵通过master发送的心跳包确认master没有宕机，但是由于网络等问题，某些master可能无法即时收到心跳包而误以为master宕机了，这时候就要有哨兵之间进行投票避免把master给替换了

<img width="542" alt="5681236e4609c6a7d639d2ce3ea7effc" src="https://github.com/user-attachments/assets/1effb244-5a65-49cf-aa07-b4213c019aa4" />

<img width="629" alt="e7a2d76d5ce8f71e6e7bbc54095c00f0" src="https://github.com/user-attachments/assets/024606af-a6ac-46f3-b0cd-b646e2bcc994" />

### 2.主观下线和客观下线
<img width="636" alt="2fe599cf0620eee877e6854b3303db0e" src="https://github.com/user-attachments/assets/ae47daef-70e4-4907-9c0b-6db93d29c830" />

<img width="602" alt="a69428790ce743c14bea3feaca59065f" src="https://github.com/user-attachments/assets/1426bb91-f0f4-4e1f-9d75-70a83b79a412" />

### 3.哨兵中的leader

<img width="431" alt="1908896426d8160f4e0a819a2f9d6a71" src="https://github.com/user-attachments/assets/2f555af2-d5fb-4742-a76d-55f990788837" />

### 4.如何选举哨兵中的leader
通过哨兵之间的raft协议
<img width="605" alt="58813b73b3e7c6050be724e71e47f903" src="https://github.com/user-attachments/assets/4b20223f-e787-4b78-9749-bac29f942dd5" />

### 5.如何选出新的master
<img width="424" alt="9c081145fb8a92879ef8dd4fddc7d11a" src="https://github.com/user-attachments/assets/ab536c6c-2434-4d20-8dca-d58a04cc2e2c" />

<img width="632" alt="0f186925fb968d3a9b5d0faf1914a580" src="https://github.com/user-attachments/assets/4082c4d5-6df1-41b5-b76c-523d1d982ed1" />

### 6.哨兵的使用建议
<img width="565" alt="a4b0c70878a2225597f31a282651aa3b" src="https://github.com/user-attachments/assets/16d1467c-5bbf-4f78-98b3-3df294aeac60" />
Q：哨兵为什么是必要的

### 7.主从复制+哨兵策略的缺陷
在哨兵发现master宕机，（主客观下线）在哨兵中选举一个leader，由leader选择一个slave上位，并且让其他slave与新master建立连接这段时间，数据仍然是无法写入的，这是缺点，由此引入了redis集群
