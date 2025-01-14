### 1.哨兵的作用
1）监控redis运行状态，包括master和slave
2）当master宕机时，根据某一种选举算法，使其中一个slave成为master（master宕机时，无法向redis写入数据，此时系统将会瘫痪，因此必须立刻重新产生以master）
