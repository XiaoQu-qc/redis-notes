### 1.为什么要redis集群
1）上一节最后提过，有段时间整个redis无法写入数据
2）由于数据量过大，单个Master复制集难以承担，因此需要对多个复制集进行集群，形成水平扩展，每个复制集只负责存储整个数据集的一部分，这就是redis集群，
其作用是提供多个redis节点间共享数据的程序集

### 2.redis集群能干什么
<img width="602" alt="115ccb4e0407bab827b36c3d51f35f98" src="https://github.com/user-attachments/assets/021c60b5-82e7-4b68-94df-5dca6bea8458" />

<img width="627" alt="f602f314f26171d37115517eb6c42ca3" src="https://github.com/user-attachments/assets/06cd3086-2750-42df-bd80-f03e65d083a9" />

