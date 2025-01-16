### 1.为什么要redis集群
1）上一节最后提过，有段时间整个redis无法写入数据
2）由于数据量过大，单个Master复制集难以承担，因此需要对多个复制集进行集群，形成水平扩展，每个复制集只负责存储整个数据集的一部分，这就是redis集群，
其作用是提供多个redis节点间共享数据的程序集

### 2.redis集群能干什么
<img width="602" alt="115ccb4e0407bab827b36c3d51f35f98" src="https://github.com/user-attachments/assets/021c60b5-82e7-4b68-94df-5dca6bea8458" />

<img width="627" alt="f602f314f26171d37115517eb6c42ca3" src="https://github.com/user-attachments/assets/06cd3086-2750-42df-bd80-f03e65d083a9" />

### 3.槽位slot和分片
最大槽位为16384个，但是通常情况下不要超过1000个
<img width="744" alt="044469638c90e400533aac0130eb44f0" src="https://github.com/user-attachments/assets/945298df-3879-49e2-bd03-219dbcc63342" />

<img width="643" alt="9210a0c217b5ee43dd3d9d3e5ebcbbba" src="https://github.com/user-attachments/assets/aae5defa-444b-49a5-89c8-1140c0cdb8eb" />

<img width="541" alt="04dcceeaba59122b8941d3b0a7ef2140" src="https://github.com/user-attachments/assets/f2d1df8a-7b75-40c5-a840-00e3b6355a01" />
1）redis集群中不支持mset(mget) k1 v1 k2 v2操作，因为keys request dont hash in same slot，要用mset k1{x} v1 k2{x} v2通配符操作，这样做不会调用CRChash映射操作
