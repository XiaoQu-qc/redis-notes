### 1.redis事务是什么
本质是一组命令的集合，一个事务中的所有命令都会被序列化，按顺序串行执行而不会被其他命令插入，禁止加塞
事务中的命令执行时，不允许其他命令执行，但如果这些指令还在队列中，还没由EXEC，此时其他指令可以执行
### 2.redis事务和数据库事务的对比
<img width="729" alt="71bc3cc818c9f1c923a22da04bef38af" src="https://github.com/user-attachments/assets/a7977436-efde-4d7f-8a4e-77900f399cd1" />
### 3.redis事务的一些特点
1)全体连坐：当执行队列中的命令有编译错误时，整个事务无法EXEC（nil
2)源头寨主：当出现运行时错误时，只有引起错误的那条指令不会被执行，其他指令都会被正常执行，这就是为什么redis并没有数据库那样的原子性，即redis不提供回滚策略
3）redis采用乐观锁保证高性能和高并发，主要通过watch key命令实现，如果在EXEC之前修改了被watch的键，那么整个事务会被取消，以确保数据的同步，注意这时事务中的命令还在队列中，没有EXEC其他命令没有被阻塞可以执行
<img width="687" alt="827e04b72d2647e335f061a3c8e5abaf" src="https://github.com/user-attachments/assets/60fecb8e-bbc5-4276-be87-f1142dc412f4" />


