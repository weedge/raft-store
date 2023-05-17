# raft-store

## paper:

[https://raft.github.io/raft.pdf](https://raft.github.io/raft.pdf)

[https://web.stanford.edu/~ouster/cgi-bin/papers/OngaroPhD.pdf](https://web.stanford.edu/~ouster/cgi-bin/papers/OngaroPhD.pdf)

[https://github.com/maemual/raft-zh_cn](https://github.com/maemual/raft-zh_cn)

## learn:

[https://pdos.csail.mit.edu/6.824/](https://pdos.csail.mit.edu/6.824/)

[https://github.com/talent-plan/tinykv](https://github.com/talent-plan/tinykv) (multi-raft)

## implementations need support:

1. **Leader Election (the important first thing core PreVote)**
2. **Log Replication (transport)**
3. **Persistence (meta stable/log storage interface)**
4. **Membership Changes(add/remove nodes)**
5. **Log Compaction (snapshotting compaction <-> FSM)**

## open source code:

1. c-raft: [https://github.com/redislabs/raft](https://github.com/redislabs/raft) [https://github.com/willemt/raft](https://github.com/willemt/raft)

 [https://github.com/redislabs/raft](https://github.com/redislabs/raft)[https://github.com/willemt/raft](https://github.com/willemt/raft) [https://github.com/willemt/ticketd](https://github.com/willemt/ticketd)

[https://github.com/RedisLabs/redisraft/blob/master/deps/raft/README.md](https://github.com/RedisLabs/redisraft/blob/master/deps/raft/README.md) [**https://redis.com/blog/redisraft-new-strong-consistency-deployment-option/**](https://redis.com/blog/redisraft-new-strong-consistency-deployment-option/)

1. c++-raft:[**https://github.com/logcabin/logcabin**](https://github.com/logcabin/logcabin) [https://github.com/baidu/braft](https://github.com/baidu/braft) [https://github.com/PikaLabs/floyd](https://github.com/PikaLabs/floyd)
2. rust-raft: [https://tikv.org/blog/implement-raft-in-rust/](https://tikv.org/blog/implement-raft-in-rust/) [https://github.com/tikv/raft-rs](https://github.com/tikv/raft-rs)
3. go-raft: [https://github.com/hashicorp/raft](https://github.com/hashicorp/raft)([prevote issue](https://github.com/hashicorp/raft/issues/31))   [https://github.com/etcd-io/raft](https://github.com/etcd-io/raft)
4. go-multi-group-raft: [https://github.com/lni/dragonboat](https://github.com/lni/dragonboat)

### hashicorp raft  use case:

1. [https://github.com/ledisdb/redis-failover/blob/3d60fbae159a63e375ab6b11f4a8913f46ce477f/failover/raft.go#L164](https://github.com/ledisdb/redis-failover/blob/3d60fbae159a63e375ab6b11f4a8913f46ce477f/failover/raft.go#L164)
2. [**https://github.com/seaweedfs/seaweedfs/blob/2e351aa96735ab2d1e4c20d0973d0653820b4cd4/weed/server/raft_hashicorp.go#L138**](https://github.com/seaweedfs/seaweedfs/blob/2e351aa96735ab2d1e4c20d0973d0653820b4cd4/weed/server/raft_hashicorp.go#L138)
3. [https://github.com/chengshiwen/influxdb-cluster/blob/529251fda5d776cf47bb0c247cf81075f2980fed/services/meta/raft_state.go](https://github.com/chengshiwen/influxdb-cluster/blob/529251fda5d776cf47bb0c247cf81075f2980fed/services/meta/raft_state.go)
4. [https://github.com/ApsaraDB/PolarDB-ClusterManager/blob/dd1c4312b1202023eb693174e64be660d5c49140/pkg/meta/raft_consensus_service.go](https://github.com/ApsaraDB/PolarDB-ClusterManager/blob/dd1c4312b1202023eb693174e64be660d5c49140/pkg/meta/raft_consensus_service.go)
5. [https://github.com/casbin/hraft-dispatcher/blob/main/store/store.go](https://github.com/casbin/hraft-dispatcher/blob/main/store/store.go)
6. [https://github.com/tidwall/ticketd/blob/master/main.go](https://github.com/tidwall/ticketd/blob/master/main.go) (like c ticketd simple)
7. [**https://github.com/tidwall/uhaha/blob/master/uhaha.go**](https://github.com/tidwall/uhaha/blob/master/uhaha.go)
8. **[https://github.com/rqlite/rqlite/blob/master/store/store.go#L426](https://github.com/rqlite/rqlite/blob/master/store/store.go#L426) (distributed relational database use sqlite)**
9. [https://github.com/hashicorp/consul/blob/v1.15.2/agent/consul/server.go#L1135](https://github.com/hashicorp/consul/blob/v1.15.2/agent/consul/server.go#L1135) (consul)
10. [https://github.com/travisjeffery/jocko/blob/9613083803fc7d0fefd10d6d0cf00223d13ba301/jocko/leader.go#L117](https://github.com/travisjeffery/jocko/blob/9613083803fc7d0fefd10d6d0cf00223d13ba301/jocko/leader.go#L117) (kafka like KRaft)
11. [https://github.com/ipfs-cluster/ipfs-cluster/blob/f092e02850221fb03ebabb7bb24007748a36c804/consensus/raft/raft.go#L100](https://github.com/ipfs-cluster/ipfs-cluster/blob/f092e02850221fb03ebabb7bb24007748a36c804/consensus/raft/raft.go#L100) (ipfs)
12. [https://github.com/dapr/dapr/blob/770d4e51604f1264d8bb25cedf16ea9f77539394/pkg/placement/raft/server.go#L226](https://github.com/dapr/dapr/blob/770d4e51604f1264d8bb25cedf16ea9f77539394/pkg/placement/raft/server.go#L226) (dapr placement data)
13. [https://github.com/hashicorp/vault/blob/6bb1f6a9046a0dc1d301cf2d2a8191bbe81fe4c8/physical/raft/raft.go#L1018](https://github.com/hashicorp/vault/blob/6bb1f6a9046a0dc1d301cf2d2a8191bbe81fe4c8/physical/raft/raft.go#L1018)

### raft storage(log, meta stable):

1. [https://github.com/weedge/raft-pebble](https://github.com/weedge/raft-pebble)
2. [https://github.com/BBVA/raft-badger](https://github.com/BBVA/raft-badger) [https://github.com/vaccovecrana/vephar/blob/main/srv/vp_badger.go](https://github.com/vaccovecrana/vephar/blob/main/srv/vp_badger.go)
3. [https://github.com/hashicorp/raft-boltdb](https://github.com/hashicorp/raft-boltdb) 
4. [https://github.com/tidwall/raft-leveldb](https://github.com/tidwall/raft-leveldb)
5. [https://github.com/hashicorp/raft-mdb](https://github.com/hashicorp/raft-mdb)
6. [https://github.com/hashicorp/raft/blob/main/inmem_store.go](https://github.com/hashicorp/raft/blob/main/inmem_store.go)
7. **[github.com/tidwall/raft-wal](http://github.com/tidwall/raft-wal) ([github.com/tidwall/wal](http://github.com/tidwall/wal))  [https://github.com/tidwall/raft-jss](https://github.com/tidwall/raft-jss) (json) simple raw support** 

# Storage:

## [LSMTree](https://en.wikipedia.org/wiki/Log-structured_merge-tree)

leveldb: [https://github.com/google/leveldb](https://github.com/google/leveldb) [https://github.com/syndtr/goleveldb](https://github.com/syndtr/goleveldb)

rocksdb: [https://github.com/facebook/rocksdb](https://github.com/facebook/rocksdb)

rocksdb extra

1. [https://github.com/bytedance/terarkdb](https://github.com/bytedance/terarkdb)  [https://github.com/topling/toplingdb](https://github.com/topling/toplingdb)
2. *https://github.com/cockroachdb/pebble*
3. *https://github.com/dgraph-io/badger* <u>[bench badger-lmdb-boltdb](https://dgraph.io/blog/post/badger-lmdb-boltdb/)</u>

## [BTree](https://en.wikipedia.org/wiki/B%2B_tree)

[lmdb](https://www.symas.com/lmdb)

[bboltdb](https://github.com/etcd-io/bbolt)

[SQLite3](https://www.sqlite.org/arch.html)


# test:
https://github.com/jepsen-io/jepsen

# reference:

1. [https://raft.github.io/](https://raft.github.io/)
2. [https://github.com/hashicorp/raft/tree/main/docs](https://github.com/hashicorp/raft/tree/main/docs)
3. [https://github.com/hashicorp/raft-wal](https://github.com/hashicorp/raft-wal)
