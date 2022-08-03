# readConcern

## readConcern作用

**MongoDB** 可以利用`readConcern`来灵活的定制读策略，决定读数据时，能读到什么样的数据。包含两个选项：

- local 能读取任意数据，默认设置
- Majority 只能读取到成功写入到大多数节点的数据

`readConcern`的初衷在于解决 **脏读** 的问题，比如用户从MongoDB的primary上读取了某一条数据，但这条数据并没有同步到大多数节点，然后primary就故障了，重新恢复后这个primary节点会将未同步到大多数节点的数据回滚掉，导致用户读到了 **脏数据**。

当指定 `readConcern `级别为 majority 时，能保证用户读到的数据已经写入到大多数节点，而这样的数据肯定不会发生回滚，避免了脏读的问题。

有用户误以为，`readConcern`指定为 majority 时，客户端会从大多数的节点读取数据，然后返回最新的数据；实际上并不是这样，无论何种级别的`readConcern`，客户端都只会从 某一个确定的节点读取数据（具体是哪个节点由`readPreference`决定），该节点根据自己看到的同步状态视图，指挥返回已经同步到大多数节点的数据。



## readConcern原理

MongoDB 要支持 majority 的 readConcern级别，必须设置 `replication.enableMajorityReadConcern` 参数，加上这个参数后，mongoDB 会起一个单独的snapshot线程，会周期性的对当前的数据集进行snapshot，并记录snapshot时最新的oplog的时间戳，得到一个映射表。

| 最近 oplog 时间戳 | snapshot  | 状态       |
| ----------------- | --------- | ---------- |
| t0                | snapshot0 | commited   |
| t1                | snapshot1 | uncommited |
| t2                | snapshot2 | uncommited |
| t3                | snapshot3 | uncommited |

只有确保 oplog 已经同步到大多数节点时，对应的 snapshot 才会标记为commited，用户读取时，从最新的commited状态的snapshot读取数据，就能保证读到的数据一定已经同步到了大多数节点。







## readConcern须知

## readPreference



# writeConcern

## writeConcern选项

## {w:"majority"}解析



