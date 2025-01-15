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
