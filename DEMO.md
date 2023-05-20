分布式demokv 实现todo:

- [ ]  使用rocksdb，lmdb等存储引擎，对其使用drive封装一层适配接口，可参考ledis 实现
- [ ]  采用raft来保证kv存储引擎节点的分布式高可用和一致性，写强一致，读一致性分3种模式可选：low(本地一致), mid(最多一致，弱一致 默认实现), high(强一致，leader节点读)
    1. 采用简单上手的 [github.com/hashicorp/raft](http://github.com/hashicorp/raft) 了解raft小论文即可
    2. 实现raft logStore 接口， 可以采用badger, pebble 作为log存储引擎
- [ ]  实现一个简单的raft-demokv 分布式kv服务，采用tcp/grpc通信leader选举和复制日志，提供http/grpc/thrift raft集群节点管理，以及简单的 kv get/set/iter/delete raw操作
- [ ]  采用docker进行部署
- [ ]  使用k8s集群管理编排
- [ ]  使用operator来部署
- [ ]  增强版实现
    - [ ]  实现强一致读， 可参考[rqlite](https://github.com/rqlite/rqlite) 实现
    - [ ]  实现multi group raft, 可以直接引用三方库 https://github.com/lni/dragonboat-example ，或者使用etcd https://github.com/etcd-io/raft 实现multi group raft
    - [ ]  支持redis协议操作， 本地可参考ledis，远程可参考https://github.com/yongman/tidis ；更多操作可参考 https://github.com/tidwall/summitdb
    - [ ]  支持sql 协议解析操作，可参考 [rqlite](https://github.com/rqlite/rqlite) pgsql sqlparser实现
    - [ ]  支持 分布式事务操作，比较难，可参考论文spanner, tidb实现
    - [ ]  底层kv存储引擎支持冷热数据分离，热数据放入内存中，温数据落地只保留2层，L0和L1; 冷数据放入远程分布式对象存储中，通过DAL进行对接 ，满足大数据分析场景(share nothing and disk)
    - [ ]  数据import工具 redis-import, mysql-import (农夫山泉)
    - [ ]  数据export工具 cdc sink 对接三方数据存储服务,进行流式处理,满足大数据实时场景

优化项：

1. 服务可以组合成一个进程部署(接口库集成)，或者架构分层(rpc集成)，多个服务进行部署，根据运维成本等因素而定
2. raft log 已经通过wal保证数据安全一致，状态机数据存放可以不用开启wal机制，减少io
3. 统计读写操作监控数据，flush阈值, compaction阈值优化(关注kv引擎层场景->优化,自适应？)

上层应用使用demokv实例/库来进行业务场景交互，just YY:

1. 文件系统中，元数据存放，比如组织树，
2. 租户系统中， 组织关系的存放，比如组织树，
3. 上层应用协同数据的本地实例存放，比如crdt数据 like: https://github.com/ipfs/go-ds-crdt
