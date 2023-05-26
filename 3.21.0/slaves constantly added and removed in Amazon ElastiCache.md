### redis engine

  both  `6.2.6` and  `7.0.7` has this problem

### reddison config

```yaml
spring:
  redis:
    database: 0
    password:  PWD
    timeout: 3000
    mode:  cluster
    pool:
      minimumIdleSize: 2
      connectTimeout: 3000
      idleConnectionTimeout: 3000
      size: 10
    cluster:
      nodes: rediss://REDIS_HOST
      scanInterval: 1000
      read-mode: SLAVE
      slaveConnectionPoolSize: 64
      slaveConnectionMinimumIdleSize: 32
      masterConnectionPoolSize: 64
      masterConnectionMinimumIdleSize: 32
      retryAttempts: 3
      failedAttempts: 3
      retryInterval: 1500
```

### trace log

after enable trace log,  The problem reappears at 09:02:08.880,

```shell
2023-05-26 09:00:54.764 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x84160c2f, L:/10.110.144.84:52794 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.764 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0x52637df4, L:/10.110.144.84:52860 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.764 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0x1855534a, L:/10.110.144.84:52876 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.764 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xab19d647, L:/10.110.144.84:52810 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.764 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x473a3b68, L:/10.110.144.84:52796 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.764 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0x326dadc1, L:/10.110.144.84:52868 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.764 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x8c1d1d08, L:/10.110.144.84:52846 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.764 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x79b442af, L:/10.110.144.84:52834 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.764 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xb424d7c0, L:/10.110.144.84:52822 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.764 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x754f25dd, L:/10.110.144.84:52884 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.765 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x84160c2f, L:/10.110.144.84:52794 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@62b05739[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.765 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8c1d1d08, L:/10.110.144.84:52846 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4ff1e620[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.765 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x754f25dd, L:/10.110.144.84:52884 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7360b09d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.765 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x52637df4, L:/10.110.144.84:52860 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2bb77e84[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.765 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1855534a, L:/10.110.144.84:52876 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6067c637[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.765 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xab19d647, L:/10.110.144.84:52810 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7d355680[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.765 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x79b442af, L:/10.110.144.84:52834 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@459df60c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.765 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb424d7c0, L:/10.110.144.84:52822 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6fa56f55[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.765 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0x473a3b68, L:/10.110.144.84:52796 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@11edfc10[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.765 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x326dadc1, L:/10.110.144.84:52868 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@367a1ef1[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.864 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0xae1fe143, L:/10.110.144.84:52890 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.864 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0x7ed2fc63, L:/10.110.144.84:52946 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.864 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0xa71b78cc, L:/10.110.144.84:53048 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.864 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0xae3e7c1c, L:/10.110.144.84:52926 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.864 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x20a56afe, L:/10.110.144.84:53020 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.864 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0x6f191eba, L:/10.110.144.84:52936 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.865 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0xf9c27ef8, L:/10.110.144.84:53024 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.865 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xc1cd3ec0, L:/10.110.144.84:52984 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.864 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0xbbace342, L:/10.110.144.84:52900 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.865 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0xef0f174d, L:/10.110.144.84:53012 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING
2023-05-26 09:00:54.865 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0x680d9bfe, L:/10.110.144.84:53044 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:00:54.864 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x993c18f9, L:/10.110.144.84:52912 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:00:54.865 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x20a56afe, L:/10.110.144.84:53020 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2e2a994[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.864 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x3f3beb36, L:/10.110.144.84:52974 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:00:54.865 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xae3e7c1c, L:/10.110.144.84:52926 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1058a062[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.865 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa71b78cc, L:/10.110.144.84:53048 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@37d6db4f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.865 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0x33a028d2, L:/10.110.144.84:53036 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:00:54.865 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3f3beb36, L:/10.110.144.84:52974 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@13cf344[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.865 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x680d9bfe, L:/10.110.144.84:53044 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@58b71df2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.865 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x993c18f9, L:/10.110.144.84:52912 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5af8caa[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.865 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6f191eba, L:/10.110.144.84:52936 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@42338396[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.865 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbbace342, L:/10.110.144.84:52900 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1ccc118c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.865 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc1cd3ec0, L:/10.110.144.84:52984 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2a684fbf[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.865 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7ed2fc63, L:/10.110.144.84:52946 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@724afc2f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.865 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xef0f174d, L:/10.110.144.84:53012 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@21260983[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.865 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf9c27ef8, L:/10.110.144.84:53024 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5efd9330[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.866 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xae1fe143, L:/10.110.144.84:52890 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@21cc6893[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.866 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xb97ba58c, L:/10.110.144.84:52998 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:00:54.866 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x33a028d2, L:/10.110.144.84:53036 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6f9b801e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.866 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x20089fa0, L:/10.110.144.84:52958 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:00:54.866 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb97ba58c, L:/10.110.144.84:52998 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@30c8e0ce[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.866 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x20089fa0, L:/10.110.144.84:52958 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6eaca943[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.964 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0xdd865026, L:/10.110.144.84:53062 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:00:54.965 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x9cf931d9, L:/10.110.144.84:53074 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:00:54.965 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xa793ea30, L:/10.110.144.84:53094 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:00:54.965 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc5c90da, L:/10.110.144.84:53064 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:00:54.965 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x776d0d72, L:/10.110.144.84:53086 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:00:54.965 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0x7536079f, L:/10.110.144.84:53104 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:00:54.965 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x08223bc3, L:/10.110.144.84:53114 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:00:54.965 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xcc5c90da, L:/10.110.144.84:53064 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@414210c7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.965 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa793ea30, L:/10.110.144.84:53094 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1e1e8580[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.965 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7536079f, L:/10.110.144.84:53104 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@521988f2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.965 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x776d0d72, L:/10.110.144.84:53086 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@75b1cbbf[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.965 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9cf931d9, L:/10.110.144.84:53074 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@385003a4[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.965 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xdd865026, L:/10.110.144.84:53062 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@773ea86d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:54.966 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x08223bc3, L:/10.110.144.84:53114 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6ec378a5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.137 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:00:55.137 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062852000 6 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062854000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062852304 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062850287 5 connected 0-5461
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062851000 4 connected 10923-16383
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062853000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062853000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062851000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062854321 4 connected

, channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6d15aa50[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:00:55.138 DEBUG 1 --- [sson-netty-3-15] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.156.54/10.110.156.54:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062852000 6 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062854000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062852304 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062850287 5 connected 0-5461
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062851000 4 connected 10923-16383
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062853000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062853000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062851000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062854321 4 connected

2023-05-26 09:00:55.165 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0xd866eba9, L:/10.110.144.84:33490 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.165 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0xdcf17e87, L:/10.110.144.84:33518 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.165 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x836e5eb7, L:/10.110.144.84:33508 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.165 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0xf7333ec8, L:/10.110.144.84:33492 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.165 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xa79c2a70, L:/10.110.144.84:33564 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.165 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xee749cfc, L:/10.110.144.84:33510 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.166 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xdcf17e87, L:/10.110.144.84:33518 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@16155054[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.166 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0xf7333ec8, L:/10.110.144.84:33492 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@d840e5f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.166 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xee749cfc, L:/10.110.144.84:33510 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4a16ef29[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.166 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x836e5eb7, L:/10.110.144.84:33508 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6ba75e84[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.166 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x47df7172, L:/10.110.144.84:33548 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.166 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa79c2a70, L:/10.110.144.84:33564 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6ced3196[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.166 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0x4c364542, L:/10.110.144.84:33578 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.166 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd866eba9, L:/10.110.144.84:33490 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@719f260[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.165 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0xbf9413ee, L:/10.110.144.84:33514 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.166 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x67ece0fa, L:/10.110.144.84:33534 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.165 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0x411cd3c8, L:/10.110.144.84:33532 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.167 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x47df7172, L:/10.110.144.84:33548 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@55855668[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.166 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x62eed904, L:/10.110.144.84:33600 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.166 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0xae79d629, L:/10.110.144.84:33586 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.167 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbf9413ee, L:/10.110.144.84:33514 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3f776e7a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.167 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x67ece0fa, L:/10.110.144.84:33534 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1b728227[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.167 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x411cd3c8, L:/10.110.144.84:33532 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@252efb07[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.167 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x4c364542, L:/10.110.144.84:33578 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@53ebf067[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.168 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x62eed904, L:/10.110.144.84:33600 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2310153a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.168 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xae79d629, L:/10.110.144.84:33586 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3a38b2c6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.288 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x2c342c4e, L:/10.110.144.84:33642 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.288 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0x0b9d797f, L:/10.110.144.84:33650 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.288 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xf9c20448, L:/10.110.144.84:33614 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.288 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x3a0f05aa, L:/10.110.144.84:33622 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.288 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x31f2bd4c, L:/10.110.144.84:33630 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.288 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0x3ee3cfdf, L:/10.110.144.84:33668 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.288 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0xac8a284b, L:/10.110.144.84:33664 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.288 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xa3107227, L:/10.110.144.84:33712 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.288 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0x0130460e, L:/10.110.144.84:33724 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.288 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0x1117a381, L:/10.110.144.84:33678 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.289 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x31f2bd4c, L:/10.110.144.84:33630 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@619d1489[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.289 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3ee3cfdf, L:/10.110.144.84:33668 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@53844a63[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.290 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0130460e, L:/10.110.144.84:33724 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7665d5b1[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.290 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf9c20448, L:/10.110.144.84:33614 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@47bd6126[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.290 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xac8a284b, L:/10.110.144.84:33664 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1c15cd64[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.289 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2c342c4e, L:/10.110.144.84:33642 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4e2408a5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.290 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1117a381, L:/10.110.144.84:33678 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@37c7b5a7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.290 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0b9d797f, L:/10.110.144.84:33650 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@202e3cfe[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.290 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x8ec81a61, L:/10.110.144.84:33672 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.290 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x1ae96261, L:/10.110.144.84:33686 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.290 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0x482a4a0b, L:/10.110.144.84:33682 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.289 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x6ee392be, L:/10.110.144.84:33698 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.291 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x482a4a0b, L:/10.110.144.84:33682 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@29a0198a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.291 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa3107227, L:/10.110.144.84:33712 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@10eac9d6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.291 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3a0f05aa, L:/10.110.144.84:33622 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2c241151[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.291 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1ae96261, L:/10.110.144.84:33686 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@62c1873f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.291 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8ec81a61, L:/10.110.144.84:33672 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2f3044bc[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.291 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6ee392be, L:/10.110.144.84:33698 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@bb70a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.364 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x7712ad85, L:/10.110.144.84:33728 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.365 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x3d448dc2, L:/10.110.144.84:33780 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.364 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x637bc211, L:/10.110.144.84:33740 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.364 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xe03909da, L:/10.110.144.84:33770 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.365 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xa3f22cac, L:/10.110.144.84:33754 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.365 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x4be50e97, L:/10.110.144.84:33788 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:55.365 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3d448dc2, L:/10.110.144.84:33780 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7f2aafe3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.366 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe03909da, L:/10.110.144.84:33770 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6107ec1a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.366 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x4be50e97, L:/10.110.144.84:33788 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@ea427a7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.366 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x637bc211, L:/10.110.144.84:33740 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@79dae60a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.366 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7712ad85, L:/10.110.144.84:33728 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@31d5f273[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:55.366 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa3f22cac, L:/10.110.144.84:33754 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@36be600d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:56.145 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:00:56.146 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062855757 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062854000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062855000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062854745 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062852000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062854000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062853000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062852000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062853000 6 connected

, channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5ced0caf[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:00:56.146 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379:
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062855757 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062854000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062855000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062854745 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062852000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062854000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062853000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062852000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062853000 6 connected

2023-05-26 09:00:56.665 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:00:56.665 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@668d8a34[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:00:57.153 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:00:57.154 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: $1894
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062854474 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062855482 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062853464 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062855000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062854000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062854000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062855989 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062856491 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062852000 6 connected

, channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5225a245[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:00:57.154 DEBUG 1 --- [isson-netty-3-6] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.129.61/10.110.129.61:6379:
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062854474 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062855482 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062853464 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062855000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062854000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062854000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062855989 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062856491 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062852000 6 connected

2023-05-26 09:00:57.575  INFO 1 --- [g-avatar-writer] c.x.a.n.config.NotificationConfig        : notification setting display sort: [ALL_NOTIFICATIONS, COMMENTS, NEW_FOLLOWERS]
2023-05-26 09:00:58.164 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:00:58.165 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062856342 6 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062856000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062854000 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062855333 5 connected 0-5461
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062854000 4 connected 10923-16383
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062853000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062857352 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062855000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062854321 4 connected

, channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@53c088b1[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:00:58.165 DEBUG 1 --- [sson-netty-3-15] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.156.54/10.110.156.54:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062856342 6 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062856000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062854000 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062855333 5 connected 0-5461
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062854000 4 connected 10923-16383
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062853000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062857352 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062855000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062854321 4 connected

2023-05-26 09:00:59.171 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:00:59.171 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062854000 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062853000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062854000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062856000 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062857858 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062855838 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062858865 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062857000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062856847 5 connected

, channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7a67a792[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:00:59.172 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.142.16/10.110.142.16:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062854000 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062853000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062854000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062856000 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062857858 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062855838 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062858865 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062857000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062856847 5 connected

2023-05-26 09:00:59.552  INFO 1 --- [io-63000-exec-3] c.x.a.r.c.IndexWriterController          : IndexWriterController ping
2023-05-26 09:00:59.864 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:00:59.865 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@70ac798d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:00.178 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:00.179 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: $1894
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062857502 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062858000 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062857000 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062856000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062858511 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062859519 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062858000 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062856491 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062857000 6 connected

, channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@becf3f[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:00.179 DEBUG 1 --- [isson-netty-3-6] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.129.61/10.110.129.61:6379:
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062857502 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062858000 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062857000 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062856000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062858511 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062859519 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062858000 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062856491 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062857000 6 connected

2023-05-26 09:01:01.190 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:01.192 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062859893 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062859000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062859000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062858000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062856000 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062860909 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062858000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062856000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062858000 6 connected 5462-10922

, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1249f588[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:01.192 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.229/10.110.154.229:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062859893 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062859000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062859000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062858000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062856000 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062860909 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062858000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062856000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062858000 6 connected 5462-10922

2023-05-26 09:01:02.200 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:02.201 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062859893 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062860000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062859000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062858000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062861000 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062860909 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062858000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062861927 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062858000 6 connected 5462-10922

, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1d5d6f04[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:02.201 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.229/10.110.154.229:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062859893 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062860000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062859000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062858000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062861000 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062860909 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062858000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062861927 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062858000 6 connected 5462-10922

2023-05-26 09:01:03.208 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:03.208 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: $1894
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062862542 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062858000 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062860528 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062861535 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062862000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062859519 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062861000 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062859000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062859000 6 connected

, channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3d6d8bb3[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:03.209 DEBUG 1 --- [isson-netty-3-6] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.129.61/10.110.129.61:6379:
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062862542 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062858000 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062860528 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062861535 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062862000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062859519 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062861000 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062859000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062859000 6 connected

2023-05-26 09:01:04.215 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:04.216 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062861825 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062862000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062859000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062862000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062861623 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062861000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062861000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062862837 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062863845 6 connected

, channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@373e9b5a[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:04.217 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379:
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062861825 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062862000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062859000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062862000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062861623 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062861000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062861000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062862837 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062863845 6 connected

2023-05-26 09:01:05.224 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:05.225 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062863000 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062862000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062863000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062862000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062864851 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062863000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062861000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062862837 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062863845 6 connected

, channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@63518e80[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:05.225 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379:
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062863000 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062862000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062863000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062862000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062864851 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062863000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062861000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062862837 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062863845 6 connected

2023-05-26 09:01:06.241 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:06.242 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062863000 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062862000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062863000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062865000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062864851 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062863000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062865867 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062862837 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062863845 6 connected

, channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@737c4074[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:06.242 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379:
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062863000 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062862000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062863000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062865000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062864851 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062863000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062865867 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062862837 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062863845 6 connected

2023-05-26 09:01:06.964 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xacf35917, L:/10.110.144.84:52652 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:06.964 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:06.964 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x092211ef, L:/10.110.144.84:52700 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:06.965 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0xf4fa2716, L:/10.110.144.84:52690 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:06.965 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x29287aa4, L:/10.110.144.84:52674 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:06.965 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf4fa2716, L:/10.110.144.84:52690 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@33154e97[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:06.965 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0xacf35917, L:/10.110.144.84:52652 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2947d9e6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:06.965 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x340eb3de, L:/10.110.144.84:52654 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:06.965 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x70380bd3, L:/10.110.144.84:52666 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:06.965 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x092211ef, L:/10.110.144.84:52700 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2d8e5b4[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:06.965 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x29287aa4, L:/10.110.144.84:52674 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@624aa6de[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:06.965 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1b16fb5d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:06.965 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x340eb3de, L:/10.110.144.84:52654 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3b6f3cf9[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:06.966 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x70380bd3, L:/10.110.144.84:52666 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@70ea6698[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.064 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x9af51b9b, L:/10.110.144.84:52714 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.065 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x523b6e77, L:/10.110.144.84:52768 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.065 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x0580830a, L:/10.110.144.84:52772 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.065 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0xf2f7a384, L:/10.110.144.84:52798 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.065 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0x5d9d8a2f, L:/10.110.144.84:52748 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.065 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0xb7d08619, L:/10.110.144.84:52758 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.065 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x6843b4fb, L:/10.110.144.84:52808 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.065 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0xd9718309, L:/10.110.144.84:52824 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.065 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf2f7a384, L:/10.110.144.84:52798 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@25fccf69[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.065 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9af51b9b, L:/10.110.144.84:52714 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5634a413[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.065 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb7d08619, L:/10.110.144.84:52758 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@bca541c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.066 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6843b4fb, L:/10.110.144.84:52808 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@21fa5e43[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.066 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0xd60af23b, L:/10.110.144.84:52718 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.066 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd9718309, L:/10.110.144.84:52824 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@67dda237[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.066 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd60af23b, L:/10.110.144.84:52718 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3c7081f9[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.064 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0xef8d5a6b, L:/10.110.144.84:52762 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.066 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0x9b21c02e, L:/10.110.144.84:52734 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.069 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x523b6e77, L:/10.110.144.84:52768 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6ffeba05[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.069 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0xb71e8021, L:/10.110.144.84:52812 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.069 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9b21c02e, L:/10.110.144.84:52734 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7bd905b6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.069 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0580830a, L:/10.110.144.84:52772 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5499597a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.069 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xef8d5a6b, L:/10.110.144.84:52762 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@12ce386d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.069 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5d9d8a2f, L:/10.110.144.84:52748 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@49127fd[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.069 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x0aec2d61, L:/10.110.144.84:52792 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.069 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb71e8021, L:/10.110.144.84:52812 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@21abb4d2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.070 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x36af954f, L:/10.110.144.84:52716 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.070 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xd56d05e3, L:/10.110.144.84:52784 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.070 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0aec2d61, L:/10.110.144.84:52792 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@e252321[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.070 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd56d05e3, L:/10.110.144.84:52784 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@305bf10a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.071 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x36af954f, L:/10.110.144.84:52716 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6d458274[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.165 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x7dd7e63c, L:/10.110.144.84:52892 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.165 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0xe1e6bd8f, L:/10.110.144.84:52924 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.165 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x3380aecd, L:/10.110.144.84:52826 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.165 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0x6009cc6c, L:/10.110.144.84:52838 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.165 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0x564f0265, L:/10.110.144.84:52872 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.165 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xa6ccd892, L:/10.110.144.84:52828 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.165 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x60abf31c, L:/10.110.144.84:52922 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.165 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0xbf65c213, L:/10.110.144.84:52854 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.165 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x7d159085, L:/10.110.144.84:52886 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.165 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x29144e0e, L:/10.110.144.84:52906 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.165 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0x28e06be0, L:/10.110.144.84:52860 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.165 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0xf931d36e, L:/10.110.144.84:52832 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:07.166 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x564f0265, L:/10.110.144.84:52872 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7781eb9e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.166 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7dd7e63c, L:/10.110.144.84:52892 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@66c6927f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.166 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7d159085, L:/10.110.144.84:52886 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@f7bee7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.166 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6009cc6c, L:/10.110.144.84:52838 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6dc9109f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.166 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3380aecd, L:/10.110.144.84:52826 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5f24c5e4[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.166 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x28e06be0, L:/10.110.144.84:52860 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3c0680cd[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.166 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x60abf31c, L:/10.110.144.84:52922 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@57966c28[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.166 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa6ccd892, L:/10.110.144.84:52828 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@52bd22a1[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.166 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf931d36e, L:/10.110.144.84:52832 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@68c78dfd[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.166 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x29144e0e, L:/10.110.144.84:52906 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3c0ac2ce[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.166 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe1e6bd8f, L:/10.110.144.84:52924 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@55a2c4c8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.166 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbf65c213, L:/10.110.144.84:52854 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7c52459b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:07.247 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:07.248 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: $1894
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062864668 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062863000 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062864000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062865678 4 connected 10923-16383
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062861643 5 connected 0-5461
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062863000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062866687 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062862000 5 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062863657 6 connected

, channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5eeff086[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:07.249 DEBUG 1 --- [sson-netty-3-22] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.136.174/10.110.136.174:6379:
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062864668 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062863000 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062864000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062865678 4 connected 10923-16383
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062861643 5 connected 0-5461
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062863000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062866687 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062862000 5 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062863657 6 connected

2023-05-26 09:01:08.254 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:08.254 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062867985 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062866975 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062866000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062862000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062866000 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062864000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062865565 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062864959 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062867000 6 connected 5462-10922

, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5bc738cb[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:08.255 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.229/10.110.154.229:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062867985 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062866975 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062866000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062862000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062866000 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062864000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062865565 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062864959 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062867000 6 connected 5462-10922

2023-05-26 09:01:09.259 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:09.261 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: $1894
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062867000 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062868598 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062868096 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062866000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062867000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062866000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062867589 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062865571 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062863000 6 connected

, channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@42f86618[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:09.261 DEBUG 1 --- [isson-netty-3-6] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.129.61/10.110.129.61:6379:
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062867000 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062868598 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062868096 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062866000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062867000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062866000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062867589 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062865571 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062863000 6 connected

2023-05-26 09:01:09.551  INFO 1 --- [io-63000-exec-5] c.x.a.r.c.IndexWriterController          : IndexWriterController ping
2023-05-26 09:01:10.268 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:10.273 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062867567 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062865548 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062867000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062864000 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062866000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062868576 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062869586 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062867000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062866557 6 connected

, channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2ee7cefb[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:10.273 DEBUG 1 --- [sson-netty-3-14] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.141.243/10.110.141.243:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062867567 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062865548 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062867000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062864000 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062866000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062868576 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062869586 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062867000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062866557 6 connected

2023-05-26 09:01:11.281 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:11.282 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062867985 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062867000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062868000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062867000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062871011 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062868997 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062870004 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062868000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062869000 6 connected 5462-10922

, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@36b0964f[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:11.282 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.229/10.110.154.229:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062867985 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062867000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062868000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062867000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062871011 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062868997 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062870004 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062868000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062869000 6 connected 5462-10922

2023-05-26 09:01:12.288 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:12.289 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062867567 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062868000 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062867000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062870605 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062866000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062868576 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062869586 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062869000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062871614 6 connected

, channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@122598bd[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:12.289 DEBUG 1 --- [sson-netty-3-14] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.141.243/10.110.141.243:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062867567 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062868000 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062867000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062870605 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062866000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062868576 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062869586 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062869000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062871614 6 connected

2023-05-26 09:01:13.295 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:13.295 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062869000 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062872027 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062868000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062868000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062871011 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062870000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062873029 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062870000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062869000 6 connected 5462-10922

, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2f30e3[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:13.296 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.229/10.110.154.229:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062869000 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062872027 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062868000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062868000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062871011 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062870000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062873029 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062870000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062869000 6 connected 5462-10922

2023-05-26 09:01:14.302 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:14.305 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062872000 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062866000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062873999 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062869000 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062872000 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062873000 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062869000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062872991 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062871000 5 connected

, channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@221df103[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:14.305 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.142.16/10.110.142.16:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062872000 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062866000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062873999 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062869000 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062872000 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062873000 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062869000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062872991 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062871000 5 connected

2023-05-26 09:01:15.315 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:15.316 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062872000 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062872939 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062869000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062874000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062873947 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062873000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062872000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062874957 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062873000 6 connected

, channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7c71baf9[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:15.316 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379:
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062872000 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062872939 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062869000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062874000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062873947 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062873000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062872000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062874957 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062873000 6 connected

2023-05-26 09:01:16.323 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:16.324 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: $1894
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062874000 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062875666 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062873000 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062872635 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062874555 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062874655 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062873646 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062870000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062869000 6 connected

, channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6a0ee50b[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:16.324 DEBUG 1 --- [isson-netty-3-6] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.129.61/10.110.129.61:6379:
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062874000 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062875666 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062873000 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062872635 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062874555 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062874655 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062873646 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062870000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062869000 6 connected

2023-05-26 09:01:17.334 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:17.335 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062876973 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062874000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062874000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062874000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062873947 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062873000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062875963 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062876000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062873000 6 connected

, channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@707db21f[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:17.335 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379:
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062876973 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062874000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062874000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062874000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062873947 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062873000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062875963 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062876000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062873000 6 connected

2023-05-26 09:01:17.364 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0x49034abd, L:/10.110.144.84:42756 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.364 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x8b328e3d, L:/10.110.144.84:42768 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.364 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x9ec09ec4, L:/10.110.144.84:42766 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.364 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x638588a3, L:/10.110.144.84:42686 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.364 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xe3825aed, L:/10.110.144.84:42734 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.365 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x6bc7d52b, L:/10.110.144.84:42706 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.365 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0x00d8ac77, L:/10.110.144.84:42752 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.365 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0x1230d5b1, L:/10.110.144.84:42720 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.365 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x718982ca, L:/10.110.144.84:42744 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.365 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x49034abd, L:/10.110.144.84:42756 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3857874c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.365 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8b328e3d, L:/10.110.144.84:42768 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@17f79bd1[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.365 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x00d8ac77, L:/10.110.144.84:42752 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7fba22f9[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.364 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x5d451a83, L:/10.110.144.84:42684 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.365 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6bc7d52b, L:/10.110.144.84:42706 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7875dd6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.366 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe3825aed, L:/10.110.144.84:42734 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@f20145b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.366 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9ec09ec4, L:/10.110.144.84:42766 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2b67ff2e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.366 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1230d5b1, L:/10.110.144.84:42720 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6fe2d32a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.366 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5d451a83, L:/10.110.144.84:42684 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5085abbc[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.369 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x718982ca, L:/10.110.144.84:42744 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1d5094e7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.369 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0x638588a3, L:/10.110.144.84:42686 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1f2e431c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.464 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xc17e083d, L:/10.110.144.84:42780 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.464 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0xbf6a03b6, L:/10.110.144.84:42792 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.464 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x6676572f, L:/10.110.144.84:42798 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.465 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x9e0249f6, L:/10.110.144.84:42814 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.465 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xb3fdef01, L:/10.110.144.84:42826 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.465 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x45762bf3, L:/10.110.144.84:48152 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.465 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc17e083d, L:/10.110.144.84:42780 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@484466e2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.465 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6676572f, L:/10.110.144.84:42798 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7b5c3ee4[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.466 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x45762bf3, L:/10.110.144.84:48152 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4827641f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.468 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb3fdef01, L:/10.110.144.84:42826 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@44b2f41b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.469 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x5f96959c, L:/10.110.144.84:42832 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.469 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9e0249f6, L:/10.110.144.84:42814 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@379fda75[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.469 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0xfe71ad77, L:/10.110.144.84:42862 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.469 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbf6a03b6, L:/10.110.144.84:42792 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3942f11e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.469 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0x95188a3c, L:/10.110.144.84:48150 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.469 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xe8cffa89, L:/10.110.144.84:42876 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.469 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfe71ad77, L:/10.110.144.84:42862 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6ac9cb5a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.469 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5f96959c, L:/10.110.144.84:42832 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5eee6a12[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.469 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x198f5dc0, L:/10.110.144.84:42892 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.470 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x849154fc, L:/10.110.144.84:42854 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.470 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0x95188a3c, L:/10.110.144.84:48150 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1ddcd2a8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.468 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x65ce0e77, L:/10.110.144.84:42844 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.470 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0x2d461361, L:/10.110.144.84:42866 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.470 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe8cffa89, L:/10.110.144.84:42876 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@473849b7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.470 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x198f5dc0, L:/10.110.144.84:42892 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3e18a403[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.470 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x849154fc, L:/10.110.144.84:42854 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@71c7adf1[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.470 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x65ce0e77, L:/10.110.144.84:42844 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@785444ac[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.470 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2d461361, L:/10.110.144.84:42866 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@46730888[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.565 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0x9379b00d, L:/10.110.144.84:48176 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.565 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0xbdfab9a9, L:/10.110.144.84:48210 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.565 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0x6deb51e6, L:/10.110.144.84:48192 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.565 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0xa3d1fa19, L:/10.110.144.84:48194 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.565 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0xab48a4fb, L:/10.110.144.84:42950 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.565 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0x94aee659, L:/10.110.144.84:42954 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.565 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9379b00d, L:/10.110.144.84:48176 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7233ba3f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.565 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6deb51e6, L:/10.110.144.84:48192 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@552b7006[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.565 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0xdd2a6659, L:/10.110.144.84:42934 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.565 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbdfab9a9, L:/10.110.144.84:48210 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@421dc4e5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.564 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0xbbe1edf4, L:/10.110.144.84:42908 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.566 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x206b6d8a, L:/10.110.144.84:42910 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.566 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xd386ccc3, L:/10.110.144.84:42924 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.566 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0xf749d129, L:/10.110.144.84:42932 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.566 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0xba9912e9, L:/10.110.144.84:48172 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.566 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x8b1681e6, L:/10.110.144.84:48224 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.566 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xab48a4fb, L:/10.110.144.84:42950 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@12d5537c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.564 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0x365ab65c, L:/10.110.144.84:42904 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.565 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x3b9829b5, L:/10.110.144.84:48234 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.566 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x94aee659, L:/10.110.144.84:42954 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2fe3963b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.565 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x3cd8b701, L:/10.110.144.84:48216 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.566 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x206b6d8a, L:/10.110.144.84:42910 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@46808028[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.566 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8b1681e6, L:/10.110.144.84:48224 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3da5d0fa[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.566 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf749d129, L:/10.110.144.84:42932 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@53c15aa2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.567 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa3d1fa19, L:/10.110.144.84:48194 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2fe28904[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.567 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3b9829b5, L:/10.110.144.84:48234 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7d95e117[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.567 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xdd2a6659, L:/10.110.144.84:42934 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@71c4f00e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.565 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x387347f0, L:/10.110.144.84:48242 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.567 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd386ccc3, L:/10.110.144.84:42924 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@55171468[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.565 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0xa6da8ad5, L:/10.110.144.84:42974 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.565 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0xfaebdc54, L:/10.110.144.84:48240 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.565 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x48fe8a1d, L:/10.110.144.84:42920 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.566 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x5b2d9724, L:/10.110.144.84:42962 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:17.567 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x387347f0, L:/10.110.144.84:48242 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6cd51efc[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.567 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3cd8b701, L:/10.110.144.84:48216 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5ae59c90[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.568 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfaebdc54, L:/10.110.144.84:48240 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@b8db507[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.568 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xba9912e9, L:/10.110.144.84:48172 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@10cd33b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.568 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbbe1edf4, L:/10.110.144.84:42908 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1ed722e8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.568 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x365ab65c, L:/10.110.144.84:42904 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@727c58f1[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.568 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa6da8ad5, L:/10.110.144.84:42974 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@9a47014[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.568 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x48fe8a1d, L:/10.110.144.84:42920 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@298e5c51[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.568 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5b2d9724, L:/10.110.144.84:42962 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@949b71d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.665 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x1821dec4, L:/10.110.144.84:48266 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.665 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x14fca1d2, L:/10.110.144.84:48372 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.665 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0xeffc9c7e, L:/10.110.144.84:48322 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.665 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0xdb123917, L:/10.110.144.84:48258 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.666 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0xe0cb5c04, L:/10.110.144.84:48340 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.665 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0x374cbfef, L:/10.110.144.84:48310 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.665 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xf2b1e2d3, L:/10.110.144.84:48290 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.666 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x03756278, L:/10.110.144.84:48360 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.666 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x3600290d, L:/10.110.144.84:48278 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.665 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x7641bb4d, L:/10.110.144.84:48296 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.665 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0xa0241a4c, L:/10.110.144.84:48338 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.666 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x4b20306c, L:/10.110.144.84:48356 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.666 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0xfc3c2d92, L:/10.110.144.84:48346 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.666 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe0cb5c04, L:/10.110.144.84:48340 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2d8eac26[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.666 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x03756278, L:/10.110.144.84:48360 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5ee82d72[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.666 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3600290d, L:/10.110.144.84:48278 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3e42643a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.666 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1821dec4, L:/10.110.144.84:48266 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4be1d781[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.666 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x374cbfef, L:/10.110.144.84:48310 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5707e251[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.667 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa0241a4c, L:/10.110.144.84:48338 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@16703fb[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.667 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x4b20306c, L:/10.110.144.84:48356 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2f8a13fd[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.668 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7641bb4d, L:/10.110.144.84:48296 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7a1791ba[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.668 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf2b1e2d3, L:/10.110.144.84:48290 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@590040c6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.668 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfc3c2d92, L:/10.110.144.84:48346 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@125f0a99[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.668 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xeffc9c7e, L:/10.110.144.84:48322 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@733fbe40[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.669 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x14fca1d2, L:/10.110.144.84:48372 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4c7213c5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.669 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xdb123917, L:/10.110.144.84:48258 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@69a2bab6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.764 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x2665b389, L:/10.110.144.84:48422 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.764 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xf677ce8a, L:/10.110.144.84:48416 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.764 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x517c3175, L:/10.110.144.84:48378 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.764 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x47c5d6c9, L:/10.110.144.84:48384 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.764 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x0e3613c2, L:/10.110.144.84:48402 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.764 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x6163387d, L:/10.110.144.84:48388 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.764 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0xf497b622, L:/10.110.144.84:48414 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.765 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6163387d, L:/10.110.144.84:48388 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@a060a10[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.765 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf677ce8a, L:/10.110.144.84:48416 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@443e3613[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.765 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf497b622, L:/10.110.144.84:48414 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6e1b21ef[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.765 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x5e54b467, L:/10.110.144.84:48394 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:17.765 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x47c5d6c9, L:/10.110.144.84:48384 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4cb02e0d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.766 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0e3613c2, L:/10.110.144.84:48402 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@deba04d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.766 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5e54b467, L:/10.110.144.84:48394 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@14ade4ff[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.766 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2665b389, L:/10.110.144.84:48422 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7ab3efbc[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.766 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x517c3175, L:/10.110.144.84:48378 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@499481ba[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:17.838  INFO 1 --- [g-avatar-writer] c.x.a.task.config.PromptAuditConfig      : initDeviceAppVersionMap:{IOS=AppVersion(major=1, minor=0, patch=0, isApp=false), WEB=AppVersion(major=1, minor=0, patch=0, isApp=false)}
2023-05-26 09:01:17.838  INFO 1 --- [g-avatar-writer] c.x.a.task.config.PromptAuditConfig      : device:ANDROID, initPhrasePattern size : 25
2023-05-26 09:01:17.838  INFO 1 --- [g-avatar-writer] c.x.a.task.config.PromptAuditConfig      : device:IOS, initPhrasePattern size : 25
2023-05-26 09:01:17.964  WARN 1 --- [g-avatar-writer] c.x.b.m.r.c.ReliabilityMessageConfig     : ReliabilityMessageConfig:ReliabilityMessageConfig(expired=PT24H, maxRetries=10, retryTime=PT5M, excludedTopic=[dvc.staging.push.register, dvc.staging.push, dvc.staging.push.ack], initRetryTime=PT10S, maxRetryTime=PT10M, retryMultiplier=5)
2023-05-26 09:01:17.994  INFO 1 --- [g-avatar-writer] c.x.a.task.config.TagComplementConfig    : Load tag-complement.yaml, content: TagComplementConfig(enabled=true, maxWordCount=15, tokenizerType=MODEL, symbolRegexp=[+_(){}], adjectiveSearchRule=AdjectiveSearchRule(front=3, back=3, crossSplitter=false, splitters=[,, ;, ., ，, 。, ；, 、], matchWordTypes=[JJ, JJR, JJS]), rules=[TagCompleteRule(type=eyes, enabled=true, match=[eye, pupil, sclera, eyewear, eyeshadow], matchRule=NOUN_ADJECTIVE, tags=[TagCompleteWeight(tag=brown eyes, weight=1), TagCompleteWeight(tag=blue eyes, weight=1), TagCompleteWeight(tag=purple eyes, weight=1), TagCompleteWeight(tag=red eyes, weight=1), TagCompleteWeight(tag=black eyes, weight=1)], selectorType=RANDOM_WEIGHT, selector=null, devices=[ANDROID, WEB, IOS]), TagCompleteRule(type=hair, enabled=true, match=[bang, ponytail, twintails, twintail, hair, braid, bun, haircut, cut], matchRule=NOUN_ADJECTIVE, tags=[TagCompleteWeight(tag=bangs pinned back, weight=1), TagCompleteWeight(tag=asymmetrical bangs, weight=1), TagCompleteWeight(tag=blonde hair, weight=1), TagCompleteWeight(tag=long hair, weight=1), TagCompleteWeight(tag=medium hair, weight=1), TagCompleteWeight(tag=short hair, weight=1), TagCompleteWeight(tag=braid, weight=1), TagCompleteWeight(tag=short ponytail, weight=1), TagCompleteWeight(tag=blunt bangs, weight=1), TagCompleteWeight(tag=swept bangs, weight=1), TagCompleteWeight(tag=twin braids, weight=1), TagCompleteWeight(tag=double bun, weight=1), TagCompleteWeight(tag=wavy hair, weight=1), TagCompleteWeight(tag=silver hair, weight=1)], selectorType=RANDOM_WEIGHT, selector=null, devices=[ANDROID, WEB, IOS]), TagCompleteRule(type=breasts, enabled=false, match=[chest, breast, tits, tit, cleavage, boob], matchRule=NOUN_ADJECTIVE, tags=[TagCompleteWeight(tag=biggest breasts, weight=1), TagCompleteWeight(tag=huge breasts, weight=2), TagCompleteWeight(tag=big breasts, weight=2), TagCompleteWeight(tag=medium breasts, weight=1), TagCompleteWeight(tag=small breasts, weight=1), TagCompleteWeight(tag=tiny breasts, weight=1), TagCompleteWeight(tag=flat chests, weight=1), TagCompleteWeight(tag=mole on breast, weight=1)], selectorType=RANDOM_WEIGHT, selector=null, devices=[WEB]), TagCompleteRule(type=face, enabled=null, match=[mouth, tooth, lipstick, face, smile, grin, freckle, mole, mask, tongue], matchRule=NOUN, tags=[TagCompleteWeight(tag=closed_mouth, weight=1), TagCompleteWeight(tag=opened mouth, weight=1), TagCompleteWeight(tag=mole above mouth, weight=1), TagCompleteWeight(tag=mouth mask, weight=1), TagCompleteWeight(tag=smile, weight=1), TagCompleteWeight(tag=grin, weight=1), TagCompleteWeight(tag=smirk, weight=1)], selectorType=RANDOM_WEIGHT, selector=null, devices=[]), TagCompleteRule(type=hand, enabled=true, match=[naked, nude, topless, hand, finger, arm, pose, armpit, hold, gloves, elbow, sleeve, handcuff, mitten, cloth, lolita], matchRule=NOUN, tags=[TagCompleteWeight(tag=arms behind head, weight=1), TagCompleteWeight(tag=arms behind back, weight=1), TagCompleteWeight(tag=hands on hips, weight=1), TagCompleteWeight(tag=own hands together, weight=1), TagCompleteWeight(tag=gloves, weight=1), TagCompleteWeight(tag=lace-trimmed gloves, weight=1), TagCompleteWeight(tag=elbow_gloves, weight=1), TagCompleteWeight(tag=hand to own mouth, weight=1), TagCompleteWeight(tag=hand on own face, weight=1), TagCompleteWeight(tag=arms crossed, weight=1), TagCompleteWeight(tag=hand in own hair, weight=1), TagCompleteWeight(tag=shushing, weight=1)], selectorType=RANDOM_WEIGHT, selector=null, devices=[ANDROID, WEB, IOS]), TagCompleteRule(type=bottomBody, enabled=true, match=[pee, bikini, porn, nsfw, masturbation, sex, nude, naked, vagina, bottomless, ass, pussy, pubic, penis, dick, boobs, fuck, uncensored, thigh, leg, skirt, dress, apron, miniskirt, pettiskirt, lace, dirndl, cloth, microskirt, lolita, jean, short, pant, underpants, trouser, bloomer, pajamas, panties, thong, knee], matchRule=NOUN, tags=[TagCompleteWeight(tag=white skirt, weight=1), TagCompleteWeight(tag=waist apron, weight=1), TagCompleteWeight(tag=plaid skirt, weight=1), TagCompleteWeight(tag=skirt, weight=1), TagCompleteWeight(tag=summer dress, weight=1), TagCompleteWeight(tag=long skirt, weight=1), TagCompleteWeight(tag=strapless dress, weight=1), TagCompleteWeight(tag=night dress, weight=1), TagCompleteWeight(tag=trousers with suspenders, weight=1), TagCompleteWeight(tag=shorts, weight=1), TagCompleteWeight(tag=leggings, weight=1), TagCompleteWeight(tag=jeans, weight=1), TagCompleteWeight(tag=leggings, weight=1), TagCompleteWeight(tag=high-waist pants, weight=1)], selectorType=RANDOM_WEIGHT, selector=null, devices=[ANDROID, WEB, IOS]), TagCompleteRule(type=foot, enabled=true, match=[nude, naked, bottomless, thighs, leg, foot, feet, sock, tabi, pantyhose, paint, trouser, stock], matchRule=NOUN, tags=[TagCompleteWeight(tag=socks, weight=1), TagCompleteWeight(tag=white stocking, weight=1), TagCompleteWeight(tag=black stocking, weight=1), TagCompleteWeight(tag=kneehighs, weight=1), TagCompleteWeight(tag=kneehighs, weight=1), TagCompleteWeight(tag=high heels, weight=1), TagCompleteWeight(tag=boots, weight=1), TagCompleteWeight(tag=ankle boots, weight=1), TagCompleteWeight(tag=slippers, weight=1), TagCompleteWeight(tag=foot shackles, weight=1), TagCompleteWeight(tag=High heeled evening shoe, weight=1)], selectorType=RANDOM_WEIGHT, selector=null, devices=[ANDROID, WEB, IOS]), TagCompleteRule(type=sfw, enabled=true, match=[nsfw, naked, masturbation, sex, vagina, pubic, fuck, dick, pee, porn, penis, nipples, areolae, topless, bottomless], matchRule=NOUN, tags=[TagCompleteWeight(tag=pink bra:1.5, weight=1), TagCompleteWeight(tag=lace bra:1.5, weight=1), TagCompleteWeight(tag=skirt:1.5, weight=1), TagCompleteWeight(tag=white bra:1.5, weight=1), TagCompleteWeight(tag=bikini:1.5, weight=1), TagCompleteWeight(tag=long dress:1.5, weight=1)], selectorType=RANDOM_WEIGHT, selector=null, devices=[IOS])])
2023-05-26 09:01:17.994  INFO 1 --- [g-avatar-writer] c.x.avatar.task.utils.TagCompleteHelper  : Weight selector configed, type: RANDOM_WEIGHT, rule.getTags(): [TagCompleteWeight(tag=brown eyes, weight=1), TagCompleteWeight(tag=blue eyes, weight=1), TagCompleteWeight(tag=purple eyes, weight=1), TagCompleteWeight(tag=red eyes, weight=1), TagCompleteWeight(tag=black eyes, weight=1)]
2023-05-26 09:01:17.994  INFO 1 --- [g-avatar-writer] c.x.avatar.task.utils.TagCompleteHelper  : Weight selector configed, type: RANDOM_WEIGHT, rule.getTags(): [TagCompleteWeight(tag=bangs pinned back, weight=1), TagCompleteWeight(tag=asymmetrical bangs, weight=1), TagCompleteWeight(tag=blonde hair, weight=1), TagCompleteWeight(tag=long hair, weight=1), TagCompleteWeight(tag=medium hair, weight=1), TagCompleteWeight(tag=short hair, weight=1), TagCompleteWeight(tag=braid, weight=1), TagCompleteWeight(tag=short ponytail, weight=1), TagCompleteWeight(tag=blunt bangs, weight=1), TagCompleteWeight(tag=swept bangs, weight=1), TagCompleteWeight(tag=twin braids, weight=1), TagCompleteWeight(tag=double bun, weight=1), TagCompleteWeight(tag=wavy hair, weight=1), TagCompleteWeight(tag=silver hair, weight=1)]
2023-05-26 09:01:17.994  INFO 1 --- [g-avatar-writer] c.x.avatar.task.utils.TagCompleteHelper  : Weight selector configed, type: RANDOM_WEIGHT, rule.getTags(): [TagCompleteWeight(tag=biggest breasts, weight=1), TagCompleteWeight(tag=huge breasts, weight=2), TagCompleteWeight(tag=big breasts, weight=2), TagCompleteWeight(tag=medium breasts, weight=1), TagCompleteWeight(tag=small breasts, weight=1), TagCompleteWeight(tag=tiny breasts, weight=1), TagCompleteWeight(tag=flat chests, weight=1), TagCompleteWeight(tag=mole on breast, weight=1)]
2023-05-26 09:01:17.994  INFO 1 --- [g-avatar-writer] c.x.avatar.task.utils.TagCompleteHelper  : Weight selector configed, type: RANDOM_WEIGHT, rule.getTags(): [TagCompleteWeight(tag=closed_mouth, weight=1), TagCompleteWeight(tag=opened mouth, weight=1), TagCompleteWeight(tag=mole above mouth, weight=1), TagCompleteWeight(tag=mouth mask, weight=1), TagCompleteWeight(tag=smile, weight=1), TagCompleteWeight(tag=grin, weight=1), TagCompleteWeight(tag=smirk, weight=1)]
2023-05-26 09:01:17.994  INFO 1 --- [g-avatar-writer] c.x.avatar.task.utils.TagCompleteHelper  : Weight selector configed, type: RANDOM_WEIGHT, rule.getTags(): [TagCompleteWeight(tag=arms behind head, weight=1), TagCompleteWeight(tag=arms behind back, weight=1), TagCompleteWeight(tag=hands on hips, weight=1), TagCompleteWeight(tag=own hands together, weight=1), TagCompleteWeight(tag=gloves, weight=1), TagCompleteWeight(tag=lace-trimmed gloves, weight=1), TagCompleteWeight(tag=elbow_gloves, weight=1), TagCompleteWeight(tag=hand to own mouth, weight=1), TagCompleteWeight(tag=hand on own face, weight=1), TagCompleteWeight(tag=arms crossed, weight=1), TagCompleteWeight(tag=hand in own hair, weight=1), TagCompleteWeight(tag=shushing, weight=1)]
2023-05-26 09:01:17.994  INFO 1 --- [g-avatar-writer] c.x.avatar.task.utils.TagCompleteHelper  : Weight selector configed, type: RANDOM_WEIGHT, rule.getTags(): [TagCompleteWeight(tag=white skirt, weight=1), TagCompleteWeight(tag=waist apron, weight=1), TagCompleteWeight(tag=plaid skirt, weight=1), TagCompleteWeight(tag=skirt, weight=1), TagCompleteWeight(tag=summer dress, weight=1), TagCompleteWeight(tag=long skirt, weight=1), TagCompleteWeight(tag=strapless dress, weight=1), TagCompleteWeight(tag=night dress, weight=1), TagCompleteWeight(tag=trousers with suspenders, weight=1), TagCompleteWeight(tag=shorts, weight=1), TagCompleteWeight(tag=leggings, weight=1), TagCompleteWeight(tag=jeans, weight=1), TagCompleteWeight(tag=leggings, weight=1), TagCompleteWeight(tag=high-waist pants, weight=1)]
2023-05-26 09:01:17.994  INFO 1 --- [g-avatar-writer] c.x.avatar.task.utils.TagCompleteHelper  : Weight selector configed, type: RANDOM_WEIGHT, rule.getTags(): [TagCompleteWeight(tag=socks, weight=1), TagCompleteWeight(tag=white stocking, weight=1), TagCompleteWeight(tag=black stocking, weight=1), TagCompleteWeight(tag=kneehighs, weight=1), TagCompleteWeight(tag=kneehighs, weight=1), TagCompleteWeight(tag=high heels, weight=1), TagCompleteWeight(tag=boots, weight=1), TagCompleteWeight(tag=ankle boots, weight=1), TagCompleteWeight(tag=slippers, weight=1), TagCompleteWeight(tag=foot shackles, weight=1), TagCompleteWeight(tag=High heeled evening shoe, weight=1)]
2023-05-26 09:01:17.994  INFO 1 --- [g-avatar-writer] c.x.avatar.task.utils.TagCompleteHelper  : Weight selector configed, type: RANDOM_WEIGHT, rule.getTags(): [TagCompleteWeight(tag=pink bra:1.5, weight=1), TagCompleteWeight(tag=lace bra:1.5, weight=1), TagCompleteWeight(tag=skirt:1.5, weight=1), TagCompleteWeight(tag=white bra:1.5, weight=1), TagCompleteWeight(tag=bikini:1.5, weight=1), TagCompleteWeight(tag=long dress:1.5, weight=1)]
2023-05-26 09:01:18.357 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:18.357 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062878291 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062873000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062877281 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062875262 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062875000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062876000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062876271 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062874000 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062876000 5 connected

, channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3e26021[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:18.358 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.144.247/10.110.144.247:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062878291 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062873000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062877281 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062875262 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062875000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062876000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062876271 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062874000 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062876000 5 connected

2023-05-26 09:01:18.413  INFO 1 --- [g-avatar-writer] c.x.b.oss.config.AwsS3CloudFrontConfig   : AwsS3CloudFrontConfig init, keys: [ap-east-1]
2023-05-26 09:01:18.565 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:18.565 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1e73f1c2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:18.864 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:18.864 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:18.864 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:18.865 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@725c7e0e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:18.865 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7016ebde[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:18.865 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@50c5ace1[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:18.926  INFO 1 --- [g-avatar-writer] u.j.c.RefreshScopeRefreshedEventListener : Refreshing cached encryptable property sources
2023-05-26 09:01:18.927  INFO 1 --- [g-avatar-writer] c.u.j.EncryptablePropertySourceConverter : Converting PropertySource server.ports [org.springframework.core.env.MapPropertySource] to EncryptableMapPropertySourceWrapper
2023-05-26 09:01:18.927  INFO 1 --- [g-avatar-writer] c.u.j.EncryptablePropertySourceConverter : Converting PropertySource springCloudDefaultProperties [org.springframework.cloud.bootstrap.BootstrapApplicationListener$ExtendedDefaultPropertySource] to EncryptableSystemEnvironmentPropertySourceWrapper
2023-05-26 09:01:18.928  INFO 1 --- [g-avatar-writer] u.j.c.RefreshScopeRefreshedEventListener : Refreshing cached encryptable property sources
2023-05-26 09:01:18.929  INFO 1 --- [g-avatar-writer] u.j.c.RefreshScopeRefreshedEventListener : Refreshing cached encryptable property sources
2023-05-26 09:01:18.929  INFO 1 --- [g-avatar-writer] o.s.c.e.event.RefreshEventListener       : Refresh keys changed: [logging.level.org.redisson]
2023-05-26 09:01:18.929  INFO 1 --- [g-avatar-writer] c.a.nacos.client.config.impl.CacheData   : [fixed-nacos-headless.avatar-staging.svc.cluster.local_8848-staging-avatar-writer] [notify-ok] dataId=application.yaml, group=DEFAULT_GROUP, md5=4ecb783c4033d729f184d36a52b459c8, listener=com.alibaba.cloud.nacos.refresh.NacosContextRefresher$1@3a0eddaa 
2023-05-26 09:01:18.929  INFO 1 --- [g-avatar-writer] c.a.nacos.client.config.impl.CacheData   : [fixed-nacos-headless.avatar-staging.svc.cluster.local_8848-staging-avatar-writer] [notify-listener] time cost=26117ms in ClientWorker, dataId=application.yaml, group=DEFAULT_GROUP, md5=4ecb783c4033d729f184d36a52b459c8, listener=com.alibaba.cloud.nacos.refresh.NacosContextRefresher$1@3a0eddaa 
2023-05-26 09:01:19.064 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x44f83714, L:/10.110.144.84:33032 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:19.064 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x2faa9b7f, L:/10.110.144.84:35588 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:19.064 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0x20fee0ee, L:/10.110.144.84:35604 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:19.065 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2faa9b7f, L:/10.110.144.84:35588 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@485bada7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.065 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0x20fee0ee, L:/10.110.144.84:35604 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@69dff696[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.065 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x44f83714, L:/10.110.144.84:33032 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@24d38e4e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.165 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x6c1866f4, L:/10.110.144.84:39166 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:19.164 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x5d211705, L:/10.110.144.84:39152 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:19.164 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x5350dfc0, L:/10.110.144.84:39162 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:19.165 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x0c5aa2cc, L:/10.110.144.84:33042 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:19.165 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x1fa475cc, L:/10.110.144.84:33052 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:19.165 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0x9f09d9d3, L:/10.110.144.84:35608 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:19.165 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5350dfc0, L:/10.110.144.84:39162 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@296a8ef3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.165 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6c1866f4, L:/10.110.144.84:39166 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5085e8c2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.165 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0x5d211705, L:/10.110.144.84:39152 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3b4e58b6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.166 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9f09d9d3, L:/10.110.144.84:35608 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7d09b206[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.166 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0x0c5aa2cc, L:/10.110.144.84:33042 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@122f344[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.166 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1fa475cc, L:/10.110.144.84:33052 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7b93f652[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.265 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x5efeef3a, L:/10.110.144.84:39178 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:19.265 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x50af68d4, L:/10.110.144.84:33060 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:19.265 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5efeef3a, L:/10.110.144.84:39178 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@778d7d64[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.265 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x50af68d4, L:/10.110.144.84:33060 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@e43b56c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.366 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:19.367 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: $1894
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062875000 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062876000 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062877680 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062876000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062876000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062878000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062878689 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062876671 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062876000 6 connected

, channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1764fbf7[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:19.367 DEBUG 1 --- [isson-netty-3-6] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.129.61/10.110.129.61:6379:
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062875000 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062876000 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062877680 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062876000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062876000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062878000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062878689 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062876671 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062876000 6 connected

2023-05-26 09:01:19.373 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xfc8e6f66, L:/10.110.144.84:35610 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:19.373 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0x3d424622, L:/10.110.144.84:33064 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:19.373 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x49f89c18, L:/10.110.144.84:39194 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:19.373 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x49f89c18, L:/10.110.144.84:39194 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@36ca3e27[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.374 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3d424622, L:/10.110.144.84:33064 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2ea78f2f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.374 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfc8e6f66, L:/10.110.144.84:35610 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@64f0b365[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.464 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0x4d2f27be, L:/10.110.144.84:39208 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:19.465 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x4d2f27be, L:/10.110.144.84:39208 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@42b6a643[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.551  INFO 1 --- [io-63000-exec-4] c.x.a.r.c.IndexWriterController          : IndexWriterController ping
2023-05-26 09:01:19.564 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0xe9b5ecaa, L:/10.110.144.84:39216 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:19.564 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0x5a5b9307, L:/10.110.144.84:35618 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:19.564 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x317d7e53, L:/10.110.144.84:33068 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:19.564 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x2f4e473f, L:/10.110.144.84:35634 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:19.564 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x1eec75c6, L:/10.110.144.84:33076 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:19.565 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2f4e473f, L:/10.110.144.84:35634 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5bdfef10[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.565 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5a5b9307, L:/10.110.144.84:35618 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4017095b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.565 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe9b5ecaa, L:/10.110.144.84:39216 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@19ab6023[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.565 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x317d7e53, L:/10.110.144.84:33068 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6a658e79[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.565 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1eec75c6, L:/10.110.144.84:33076 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@68c9ced9[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.664 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xd18c14e9, L:/10.110.144.84:39222 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:19.664 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0xdb9c7f7d, L:/10.110.144.84:35638 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:19.665 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xdb9c7f7d, L:/10.110.144.84:35638 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3219a4cc[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.665 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd18c14e9, L:/10.110.144.84:39222 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@103277d3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.764 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x3a35f9d3, L:/10.110.144.84:39230 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:19.764 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x0df23ba1, L:/10.110.144.84:33088 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:19.764 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x2f9ba3aa, L:/10.110.144.84:35646 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:19.765 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3a35f9d3, L:/10.110.144.84:39230 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2f15c184[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.765 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2f9ba3aa, L:/10.110.144.84:35646 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@29f97251[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.765 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0df23ba1, L:/10.110.144.84:33088 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@794b97c9[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.865 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0xe54f5a82, L:/10.110.144.84:33112 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:19.865 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0x5d9b6fbc, L:/10.110.144.84:33116 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:19.865 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xa5b70b5f, L:/10.110.144.84:39242 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:19.865 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x5ea4d9a0, L:/10.110.144.84:35648 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:19.865 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x1928f81a, L:/10.110.144.84:33096 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:19.865 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5ea4d9a0, L:/10.110.144.84:35648 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6906d369[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.865 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa5b70b5f, L:/10.110.144.84:39242 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@551ec212[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.865 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe54f5a82, L:/10.110.144.84:33112 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@53e1f94d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.865 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5d9b6fbc, L:/10.110.144.84:33116 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@25892020[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.866 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1928f81a, L:/10.110.144.84:33096 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7cf8537e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.965 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0xe5202825, L:/10.110.144.84:39250 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:19.965 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0x8226bc27, L:/10.110.144.84:33132 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:19.965 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0x91b09ee6, L:/10.110.144.84:35656 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:19.965 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x91b09ee6, L:/10.110.144.84:35656 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@10313a0a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.965 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe5202825, L:/10.110.144.84:39250 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@37ddcd99[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:19.966 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8226bc27, L:/10.110.144.84:33132 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4e32fa1f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.064 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xe6da5b3d, L:/10.110.144.84:35684 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.064 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x5d7ee767, L:/10.110.144.84:35672 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.064 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x9cd44164, L:/10.110.144.84:39264 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.064 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x0914946e, L:/10.110.144.84:39260 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.064 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0xad344030, L:/10.110.144.84:33142 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.064 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x9ba4091d, L:/10.110.144.84:33152 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.065 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0914946e, L:/10.110.144.84:39260 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4a7209b9[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.065 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9cd44164, L:/10.110.144.84:39264 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1f08206a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.065 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xad344030, L:/10.110.144.84:33142 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7db5449b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.065 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9ba4091d, L:/10.110.144.84:33152 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@60d666c1[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.066 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe6da5b3d, L:/10.110.144.84:35684 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4c82a22b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.066 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5d7ee767, L:/10.110.144.84:35672 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@77492262[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.164 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x75b3a5e2, L:/10.110.144.84:39266 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.164 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x60261659, L:/10.110.144.84:33174 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.164 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0xd2c461b0, L:/10.110.144.84:35698 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.164 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x39bcc445, L:/10.110.144.84:33164 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.164 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x0f7d5094, L:/10.110.144.84:39270 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.164 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0xe2163854, L:/10.110.144.84:35694 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.165 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x75b3a5e2, L:/10.110.144.84:39266 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3960cebf[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.165 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0f7d5094, L:/10.110.144.84:39270 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@43926878[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.165 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x60261659, L:/10.110.144.84:33174 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6025e80c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.165 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe2163854, L:/10.110.144.84:35694 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@42ce41d9[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.165 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x39bcc445, L:/10.110.144.84:33164 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@659b6432[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.165 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd2c461b0, L:/10.110.144.84:35698 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@444819c7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.264 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x9e8db101, L:/10.110.144.84:39288 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.264 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0xc614c9e1, L:/10.110.144.84:39272 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.264 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x5e6938b9, L:/10.110.144.84:33194 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.264 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0xd62e28a1, L:/10.110.144.84:35712 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.265 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0x071a4ddc, L:/10.110.144.84:35722 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.264 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0x82bc0c72, L:/10.110.144.84:33186 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.264 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0x16b80e64, L:/10.110.144.84:35700 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.265 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x071a4ddc, L:/10.110.144.84:35722 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@31931df5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.265 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd62e28a1, L:/10.110.144.84:35712 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@473b20b2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.265 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x16b80e64, L:/10.110.144.84:35700 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@260bbf11[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.265 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc614c9e1, L:/10.110.144.84:39272 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2b4a476f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.265 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9e8db101, L:/10.110.144.84:39288 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6896e81f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.265 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x82bc0c72, L:/10.110.144.84:33186 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@17acaf8a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.265 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5e6938b9, L:/10.110.144.84:33194 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@823c28d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.365 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0xb5304c0b, L:/10.110.144.84:35738 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.365 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x609c717c, L:/10.110.144.84:33222 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.365 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x7ebee1e9, L:/10.110.144.84:39306 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.365 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xb9b1ae85, L:/10.110.144.84:35756 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.365 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc24f08f, L:/10.110.144.84:33220 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.365 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0x6edf1e25, L:/10.110.144.84:35746 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.365 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0xfaafd2b4, L:/10.110.144.84:33210 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.365 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x112d9a77, L:/10.110.144.84:39296 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.365 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x2ed0c7f3, L:/10.110.144.84:39318 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.365 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6edf1e25, L:/10.110.144.84:35746 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5d324aa0[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.365 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb9b1ae85, L:/10.110.144.84:35756 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@62637582[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.365 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7ebee1e9, L:/10.110.144.84:39306 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@628fa638[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.365 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2ed0c7f3, L:/10.110.144.84:39318 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@736b4cf8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.365 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x112d9a77, L:/10.110.144.84:39296 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@28b747d3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.365 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x609c717c, L:/10.110.144.84:33222 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@41d33cf[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.365 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xcc24f08f, L:/10.110.144.84:33220 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@69d9e816[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.366 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfaafd2b4, L:/10.110.144.84:33210 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@da2a230[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.366 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb5304c0b, L:/10.110.144.84:35738 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5205b5c0[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.379 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:20.379 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062879000 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062880310 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062879000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062878000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062877000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062877000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062877000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062879299 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062879000 5 connected

, channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@63411e6d[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:20.380 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.144.247/10.110.144.247:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062879000 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062880310 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062879000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062878000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062877000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062877000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062877000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062879299 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062879000 5 connected

2023-05-26 09:01:20.468 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0x7678bdca, L:/10.110.144.84:35762 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.469 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7678bdca, L:/10.110.144.84:35762 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4ef6c4eb[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.564 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x9948b531, L:/10.110.144.84:33228 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.565 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x7088f732, L:/10.110.144.84:35776 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.564 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0xe3ab2d80, L:/10.110.144.84:35764 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.564 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0xdbce868f, L:/10.110.144.84:39334 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.566 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9948b531, L:/10.110.144.84:33228 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@c8e065f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.566 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe3ab2d80, L:/10.110.144.84:35764 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@16058063[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.566 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7088f732, L:/10.110.144.84:35776 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@75c3c86c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.566 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xdbce868f, L:/10.110.144.84:39334 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@78a11d02[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.569 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x82d0aa81, L:/10.110.144.84:33234 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.570 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x82d0aa81, L:/10.110.144.84:33234 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@c2ae320[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.665 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x43ebc634, L:/10.110.144.84:33238 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.665 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0xb42331de, L:/10.110.144.84:39348 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.665 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0xc6190f33, L:/10.110.144.84:33266 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.665 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x4edd0935, L:/10.110.144.84:35790 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.665 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0xb72196e7, L:/10.110.144.84:33240 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.665 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x47d47e68, L:/10.110.144.84:35798 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.665 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0xca900a49, L:/10.110.144.84:35800 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.665 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0x20e3fa9d, L:/10.110.144.84:35808 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.665 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0xb3821264, L:/10.110.144.84:33254 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.665 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x47d47e68, L:/10.110.144.84:35798 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2acd5d5b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.665 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x20e3fa9d, L:/10.110.144.84:35808 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@def231f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.665 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x4edd0935, L:/10.110.144.84:35790 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@29c5e8e6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.666 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x43ebc634, L:/10.110.144.84:33238 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4d7eb798[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.666 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb42331de, L:/10.110.144.84:39348 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5cdc6b60[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.666 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb72196e7, L:/10.110.144.84:33240 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6289582[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.665 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xca900a49, L:/10.110.144.84:35800 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@62e180ec[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.666 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc6190f33, L:/10.110.144.84:33266 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6f1350c3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.666 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb3821264, L:/10.110.144.84:33254 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4b7e006d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.765 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0x61ded287, L:/10.110.144.84:33274 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.765 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0x777278fa, L:/10.110.144.84:33276 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.765 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xfdf2b385, L:/10.110.144.84:35826 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.765 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x0a434e8d, L:/10.110.144.84:33280 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.765 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x7c01048b, L:/10.110.144.84:39360 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.765 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0xceaa12b2, L:/10.110.144.84:39350 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.765 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0xa3ac92f2, L:/10.110.144.84:35822 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.765 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfdf2b385, L:/10.110.144.84:35826 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@45eef77f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.765 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7c01048b, L:/10.110.144.84:39360 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5b6cefa2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.766 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa3ac92f2, L:/10.110.144.84:35822 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@797df8ed[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.766 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x61ded287, L:/10.110.144.84:33274 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@8480bfe[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.766 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x777278fa, L:/10.110.144.84:33276 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@66bec7ab[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.771 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0a434e8d, L:/10.110.144.84:33280 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@51401eab[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.771 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xceaa12b2, L:/10.110.144.84:39350 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6fb7c6ff[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.864 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x021bf5fb, L:/10.110.144.84:33296 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.864 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x92aa7e20, L:/10.110.144.84:39382 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.864 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0xbf095d83, L:/10.110.144.84:33308 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.864 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0xe4e96074, L:/10.110.144.84:35834 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.864 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x1c131125, L:/10.110.144.84:39374 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.864 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xf69d70d6, L:/10.110.144.84:39370 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.864 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0xc6502ddc, L:/10.110.144.84:35856 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.864 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x4f39f6a3, L:/10.110.144.84:35846 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.865 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x5f05c767, L:/10.110.144.84:33310 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:20.865 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc6502ddc, L:/10.110.144.84:35856 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@74543a8b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.865 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x8b1e8d4c, L:/10.110.144.84:35870 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:20.865 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x4f39f6a3, L:/10.110.144.84:35846 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@514818fd[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.865 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbf095d83, L:/10.110.144.84:33308 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3c4459dd[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.865 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x021bf5fb, L:/10.110.144.84:33296 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4264c99[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.865 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe4e96074, L:/10.110.144.84:35834 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@560516d6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.865 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x92aa7e20, L:/10.110.144.84:39382 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@e64d033[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.865 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1c131125, L:/10.110.144.84:39374 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3e6c53c0[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.865 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8b1e8d4c, L:/10.110.144.84:35870 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@259138d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.865 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5f05c767, L:/10.110.144.84:33310 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@14d0c99e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.865 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf69d70d6, L:/10.110.144.84:39370 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@544e9ae3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.964 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0xfce210a1, L:/10.110.144.84:39384 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.964 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x12375623, L:/10.110.144.84:39396 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:20.965 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfce210a1, L:/10.110.144.84:39384 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7fbb300a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:20.965 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x12375623, L:/10.110.144.84:39396 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4167a9f7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:21.064 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x6f224b76, L:/10.110.144.84:39416 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:21.064 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x5bc4a8da, L:/10.110.144.84:39402 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:21.064 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0xc32c3509, L:/10.110.144.84:39406 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:21.065 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5bc4a8da, L:/10.110.144.84:39402 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7e4214ef[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:21.065 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc32c3509, L:/10.110.144.84:39406 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@23e09531[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:21.065 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6f224b76, L:/10.110.144.84:39416 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3d7fffe1[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:21.165 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x8259c1ae, L:/10.110.144.84:39428 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:21.166 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8259c1ae, L:/10.110.144.84:39428 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@46532c0[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:21.387 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:21.388 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062879689 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062880696 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062878681 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062877670 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062876000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062877000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062880000 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062877000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062878000 6 connected

, channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@517653e4[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:21.388 DEBUG 1 --- [sson-netty-3-14] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.141.243/10.110.141.243:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062879689 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062880696 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062878681 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062877670 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062876000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062877000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062880000 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062877000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062878000 6 connected

2023-05-26 09:01:22.393 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:22.394 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062879689 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062880696 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062878681 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062877670 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062879000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062881706 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062880000 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062880000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062878000 6 connected

, channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5574ee2c[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:22.395 DEBUG 1 --- [sson-netty-3-14] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.141.243/10.110.141.243:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062879689 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062880696 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062878681 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062877670 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062879000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062881706 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062880000 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062880000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062878000 6 connected

2023-05-26 09:01:23.401 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:23.402 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062878000 6 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062881576 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062879000 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062879557 5 connected 0-5461
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062880000 4 connected 10923-16383
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062880000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062880000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062880567 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062882587 4 connected

, channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@444942a9[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:23.402 DEBUG 1 --- [sson-netty-3-15] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.156.54/10.110.156.54:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062878000 6 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062881576 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062879000 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062879557 5 connected 0-5461
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062880000 4 connected 10923-16383
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062880000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062880000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062880567 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062882587 4 connected

2023-05-26 09:01:23.565 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x0db36da8, L:/10.110.144.84:35774 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.565 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0x284d5b96, L:/10.110.144.84:35796 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.565 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0x8c2ea06a, L:/10.110.144.84:35804 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.565 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xf92c01fe, L:/10.110.144.84:35786 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.565 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0xf71f7ab7, L:/10.110.144.84:35790 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.565 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x4805720c, L:/10.110.144.84:35748 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.565 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0xa24502b7, L:/10.110.144.84:35746 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.565 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x0dea50d8, L:/10.110.144.84:45776 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:23.565 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x284d5b96, L:/10.110.144.84:35796 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6f63b51c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.566 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8c2ea06a, L:/10.110.144.84:35804 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@50a41a5e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.566 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf92c01fe, L:/10.110.144.84:35786 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@69155709[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.566 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0dea50d8, L:/10.110.144.84:45776 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5a474497[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.566 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0x4805720c, L:/10.110.144.84:35748 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@27cc00dd[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.566 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa24502b7, L:/10.110.144.84:35746 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5157095a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.566 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0db36da8, L:/10.110.144.84:35774 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@526be54f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.566 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf71f7ab7, L:/10.110.144.84:35790 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5e6b390d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.664 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0xb240c4b0, L:/10.110.144.84:35812 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.664 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0x7f0f4086, L:/10.110.144.84:35868 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.664 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xca067ab9, L:/10.110.144.84:35832 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.664 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0xf49776af, L:/10.110.144.84:35860 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.664 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x3c540846, L:/10.110.144.84:35878 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.664 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x6e4fed1f, L:/10.110.144.84:35882 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.664 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0xd13e7b1a, L:/10.110.144.84:35856 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.664 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x5eb61016, L:/10.110.144.84:35816 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.664 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0x8571b081, L:/10.110.144.84:35906 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.664 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0xc983ece0, L:/10.110.144.84:35848 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.664 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0xe0e620cc, L:/10.110.144.84:35904 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.665 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xb00ac60f, L:/10.110.144.84:35918 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.665 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3c540846, L:/10.110.144.84:35878 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2a8ca7e7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.665 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7f0f4086, L:/10.110.144.84:35868 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@32db0c78[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.665 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd13e7b1a, L:/10.110.144.84:35856 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@da8395e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.665 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe0e620cc, L:/10.110.144.84:35904 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1c41bb93[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.665 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb240c4b0, L:/10.110.144.84:35812 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@40221236[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.665 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0xcba3a34d, L:/10.110.144.84:35888 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.665 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8571b081, L:/10.110.144.84:35906 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@40b1d78[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.665 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc983ece0, L:/10.110.144.84:35848 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@37d55b6a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.665 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf49776af, L:/10.110.144.84:35860 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5903ce5c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.665 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5eb61016, L:/10.110.144.84:35816 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@172d9e64[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.665 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb00ac60f, L:/10.110.144.84:35918 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@78088bb2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.665 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xca067ab9, L:/10.110.144.84:35832 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@432f0fa4[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.666 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xcba3a34d, L:/10.110.144.84:35888 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5bc62fe4[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.665 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6e4fed1f, L:/10.110.144.84:35882 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@92e13b8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.764 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0xef134f04, L:/10.110.144.84:35924 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.764 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0x0cc3914c, L:/10.110.144.84:35956 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.764 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x3a921395, L:/10.110.144.84:35922 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.765 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x37175fd6, L:/10.110.144.84:35982 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.764 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0xfbdec62b, L:/10.110.144.84:35926 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.765 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x13bb21f2, L:/10.110.144.84:36004 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.764 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xcbb73c76, L:/10.110.144.84:35990 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.765 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0xe485a439, L:/10.110.144.84:35968 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.764 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0xcdce0c35, L:/10.110.144.84:35996 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.764 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0xf1dc725c, L:/10.110.144.84:35928 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.764 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x57c3f14e, L:/10.110.144.84:35940 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.765 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x6e7a6e1c, L:/10.110.144.84:35992 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.764 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x55d70ed4, L:/10.110.144.84:35976 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:23.765 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3a921395, L:/10.110.144.84:35922 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2b8bef4b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.765 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xef134f04, L:/10.110.144.84:35924 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@54567d49[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.765 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xcdce0c35, L:/10.110.144.84:35996 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@23a0e659[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.766 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x37175fd6, L:/10.110.144.84:35982 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2becbdfb[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.766 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfbdec62b, L:/10.110.144.84:35926 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1bc2b82[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.765 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xcbb73c76, L:/10.110.144.84:35990 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@58e55db0[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.766 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x57c3f14e, L:/10.110.144.84:35940 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@51fdccbe[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.766 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6e7a6e1c, L:/10.110.144.84:35992 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2d139f60[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.766 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x55d70ed4, L:/10.110.144.84:35976 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5b3aec65[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.766 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x13bb21f2, L:/10.110.144.84:36004 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4467fcc2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.766 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0cc3914c, L:/10.110.144.84:35956 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@98d2549[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.765 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe485a439, L:/10.110.144.84:35968 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@29f5d392[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:23.766 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf1dc725c, L:/10.110.144.84:35928 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3ce25893[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.410 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:24.411 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062884037 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062881007 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062879000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062881000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062883000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062882017 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062883027 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062881000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062880000 6 connected

, channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@e8b806f[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:24.411 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379:
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062884037 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062881007 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062879000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062881000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062883000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062882017 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062883027 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062881000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062880000 6 connected

2023-05-26 09:01:24.664 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:24.665 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@43980341[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.864 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x84160c2f, L:/10.110.144.84:52794 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.864 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x754f25dd, L:/10.110.144.84:52884 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.865 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0x1855534a, L:/10.110.144.84:52876 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.864 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xab19d647, L:/10.110.144.84:52810 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.864 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x473a3b68, L:/10.110.144.84:52796 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.864 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x79b442af, L:/10.110.144.84:52834 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.864 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0x326dadc1, L:/10.110.144.84:52868 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.864 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0x52637df4, L:/10.110.144.84:52860 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.865 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x84160c2f, L:/10.110.144.84:52794 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3893e937[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.865 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0x473a3b68, L:/10.110.144.84:52796 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@785a0fed[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.865 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x754f25dd, L:/10.110.144.84:52884 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@39854f9d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.864 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xb424d7c0, L:/10.110.144.84:52822 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.865 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x8c1d1d08, L:/10.110.144.84:52846 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.865 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xab19d647, L:/10.110.144.84:52810 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@71b09fec[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.865 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1855534a, L:/10.110.144.84:52876 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@c0bb877[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.865 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x52637df4, L:/10.110.144.84:52860 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@536995f1[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.865 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x79b442af, L:/10.110.144.84:52834 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@bfb431c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.866 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x326dadc1, L:/10.110.144.84:52868 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5e1879c7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.866 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb424d7c0, L:/10.110.144.84:52822 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@635f38e5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.866 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8c1d1d08, L:/10.110.144.84:52846 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3346ed3c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.965 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0xbbace342, L:/10.110.144.84:52900 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.965 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0xae3e7c1c, L:/10.110.144.84:52926 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.965 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x3f3beb36, L:/10.110.144.84:52974 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.965 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0x680d9bfe, L:/10.110.144.84:53044 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.965 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0xef0f174d, L:/10.110.144.84:53012 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.965 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0xae1fe143, L:/10.110.144.84:52890 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.965 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x993c18f9, L:/10.110.144.84:52912 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.965 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x20a56afe, L:/10.110.144.84:53020 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.965 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0xa71b78cc, L:/10.110.144.84:53048 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.965 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0x6f191eba, L:/10.110.144.84:52936 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.965 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0xf9c27ef8, L:/10.110.144.84:53024 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.965 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xb97ba58c, L:/10.110.144.84:52998 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.965 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xc1cd3ec0, L:/10.110.144.84:52984 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.965 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xef0f174d, L:/10.110.144.84:53012 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7265797f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.965 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x20a56afe, L:/10.110.144.84:53020 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5a323fd7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.966 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x20089fa0, L:/10.110.144.84:52958 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.965 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa71b78cc, L:/10.110.144.84:53048 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6fae760d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.965 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbbace342, L:/10.110.144.84:52900 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@18c4a0d5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.965 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0x33a028d2, L:/10.110.144.84:53036 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.965 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xae3e7c1c, L:/10.110.144.84:52926 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@37298965[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.966 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf9c27ef8, L:/10.110.144.84:53024 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3b67fd17[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.966 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x680d9bfe, L:/10.110.144.84:53044 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@79560784[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.966 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6f191eba, L:/10.110.144.84:52936 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@22d71769[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.966 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb97ba58c, L:/10.110.144.84:52998 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2ca308f6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.966 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xae1fe143, L:/10.110.144.84:52890 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4b7dcfe3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.966 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x993c18f9, L:/10.110.144.84:52912 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@64ee89e8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.966 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x20089fa0, L:/10.110.144.84:52958 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@743d55b2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.966 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0x7ed2fc63, L:/10.110.144.84:52946 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:24.966 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3f3beb36, L:/10.110.144.84:52974 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@39f7fe8a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.966 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x33a028d2, L:/10.110.144.84:53036 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@79f63628[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.966 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc1cd3ec0, L:/10.110.144.84:52984 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@63edd9ef[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:24.966 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7ed2fc63, L:/10.110.144.84:52946 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@66c52d89[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.065 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0xdd865026, L:/10.110.144.84:53062 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:25.065 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x08223bc3, L:/10.110.144.84:53114 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:25.065 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0x7536079f, L:/10.110.144.84:53104 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:25.065 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x9cf931d9, L:/10.110.144.84:53074 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:25.065 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc5c90da, L:/10.110.144.84:53064 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:25.065 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xa793ea30, L:/10.110.144.84:53094 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:25.065 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x776d0d72, L:/10.110.144.84:53086 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:25.065 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7536079f, L:/10.110.144.84:53104 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7b562430[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.066 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xcc5c90da, L:/10.110.144.84:53064 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@725c87b7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.066 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x776d0d72, L:/10.110.144.84:53086 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4c8cff5a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.065 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xdd865026, L:/10.110.144.84:53062 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@39c448c5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.066 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9cf931d9, L:/10.110.144.84:53074 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@340d94e1[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.066 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x08223bc3, L:/10.110.144.84:53114 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@78e8c694[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.066 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa793ea30, L:/10.110.144.84:53094 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@193e7eb8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.264 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0xd866eba9, L:/10.110.144.84:33490 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.264 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xa79c2a70, L:/10.110.144.84:33564 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.265 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0xbf9413ee, L:/10.110.144.84:33514 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.265 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0x4c364542, L:/10.110.144.84:33578 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.265 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x62eed904, L:/10.110.144.84:33600 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.264 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0x411cd3c8, L:/10.110.144.84:33532 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.264 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0xf7333ec8, L:/10.110.144.84:33492 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.264 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x836e5eb7, L:/10.110.144.84:33508 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.264 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x67ece0fa, L:/10.110.144.84:33534 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.264 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0xdcf17e87, L:/10.110.144.84:33518 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.264 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0xae79d629, L:/10.110.144.84:33586 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.265 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xee749cfc, L:/10.110.144.84:33510 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.265 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x62eed904, L:/10.110.144.84:33600 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@24d3af51[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.265 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x47df7172, L:/10.110.144.84:33548 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.265 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x4c364542, L:/10.110.144.84:33578 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7cb8118b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.265 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbf9413ee, L:/10.110.144.84:33514 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@680a99a4[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.266 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd866eba9, L:/10.110.144.84:33490 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@30e1927a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.265 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa79c2a70, L:/10.110.144.84:33564 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7979b7bb[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.266 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xae79d629, L:/10.110.144.84:33586 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6f01713[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.266 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x411cd3c8, L:/10.110.144.84:33532 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2da1548[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.266 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0xf7333ec8, L:/10.110.144.84:33492 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@49440228[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.266 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x67ece0fa, L:/10.110.144.84:33534 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1a057433[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.266 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x836e5eb7, L:/10.110.144.84:33508 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@39534268[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.266 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xee749cfc, L:/10.110.144.84:33510 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3a38bab8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.266 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xdcf17e87, L:/10.110.144.84:33518 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@ab5277[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.266 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x47df7172, L:/10.110.144.84:33548 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@732b4249[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.364 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x31f2bd4c, L:/10.110.144.84:33630 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.365 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x6ee392be, L:/10.110.144.84:33698 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.364 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xf9c20448, L:/10.110.144.84:33614 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.365 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xa3107227, L:/10.110.144.84:33712 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.365 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0xac8a284b, L:/10.110.144.84:33664 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.365 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x1ae96261, L:/10.110.144.84:33686 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.365 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0x3ee3cfdf, L:/10.110.144.84:33668 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.365 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0x482a4a0b, L:/10.110.144.84:33682 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.364 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x3a0f05aa, L:/10.110.144.84:33622 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.365 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x2c342c4e, L:/10.110.144.84:33642 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.365 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0x0b9d797f, L:/10.110.144.84:33650 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.365 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0x1117a381, L:/10.110.144.84:33678 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.365 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3ee3cfdf, L:/10.110.144.84:33668 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6d1e356[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.365 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x8ec81a61, L:/10.110.144.84:33672 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.365 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0x0130460e, L:/10.110.144.84:33724 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.366 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1ae96261, L:/10.110.144.84:33686 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@76b45c0b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.366 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x482a4a0b, L:/10.110.144.84:33682 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@62dadeaa[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.366 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0b9d797f, L:/10.110.144.84:33650 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@323e6e63[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.366 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3a0f05aa, L:/10.110.144.84:33622 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1d7a6a9d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.365 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa3107227, L:/10.110.144.84:33712 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@110b9cb2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.366 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1117a381, L:/10.110.144.84:33678 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6770cb1e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.365 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xac8a284b, L:/10.110.144.84:33664 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@30124dab[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.366 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8ec81a61, L:/10.110.144.84:33672 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1c8fc259[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.365 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x31f2bd4c, L:/10.110.144.84:33630 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@baf0758[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.365 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6ee392be, L:/10.110.144.84:33698 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@111bd99c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.366 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2c342c4e, L:/10.110.144.84:33642 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4fb0d21a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.366 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf9c20448, L:/10.110.144.84:33614 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@9bfb126[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.366 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0130460e, L:/10.110.144.84:33724 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2023ba60[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.417 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:25.418 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062885134 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062882111 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062881000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062881000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062883119 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062884129 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062883000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062881099 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062882000 6 connected 5462-10922

, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@63faca54[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:25.418 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.229/10.110.154.229:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062885134 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062882111 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062881000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062881000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062883119 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062884129 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062883000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062881099 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062882000 6 connected 5462-10922

2023-05-26 09:01:25.465 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x637bc211, L:/10.110.144.84:33740 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.465 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x3d448dc2, L:/10.110.144.84:33780 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.465 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x4be50e97, L:/10.110.144.84:33788 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.465 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xa3f22cac, L:/10.110.144.84:33754 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.465 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x7712ad85, L:/10.110.144.84:33728 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.465 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xe03909da, L:/10.110.144.84:33770 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:25.466 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3d448dc2, L:/10.110.144.84:33780 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7eabef16[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.466 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x637bc211, L:/10.110.144.84:33740 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2d289e5b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.466 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe03909da, L:/10.110.144.84:33770 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4796b52[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.466 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x4be50e97, L:/10.110.144.84:33788 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@65557873[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.466 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa3f22cac, L:/10.110.144.84:33754 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3d04896[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.466 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7712ad85, L:/10.110.144.84:33728 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@210d9cab[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:25.734 DEBUG 1 --- [sson-netty-3-26] o.r.cluster.ClusterConnectionManager     : slot 10130 for 388
2023-05-26 09:01:25.734 DEBUG 1 --- [sson-netty-3-26] org.redisson.command.RedisExecutor       : acquired connection for command (EVAL) and params [if redis.call('setnx', KEYS[6], ARGV[4]) == 0 then return -1;end;redis.call('expire', KEYS[6], ARGV[3]); local expiredKeys1 = redis.call('zrangebyscore', KEYS[2], 0, ARGV[1], 'limit', 0, ARGV[2]); for i, key in ipairs(expiredKeys1) do local v = redis.call('hget', KEYS[1], key); if v ~= false then local t, val = struct.unpack('dLc0', v); local msg = struct.pack('Lc0Lc0', string.len(key), key, string.len(val), val); local listeners = redis.call('publish', KEYS[4], msg); if (listeners == 0) then break;end; end;end;for i=1, #expiredKeys1, 5000 do redis.call('zrem', KEYS[5], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); redis.call('zrem', KEYS[3], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); redis.call('zrem', KEYS[2], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); redis.call('hdel', KEYS[1], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); end; local expiredKeys2 = redis.call('zrangebyscore', KEYS[..., 6, redis-avatar-files:{388}, redisson__timeout__set:redis-avatar-files:{388}, redisson__idle__set:redis-avatar-files:{388}, redisson_map_cache_expired:redis-avatar-files:{388}, redisson__map_cache__last_access__set:redis-avatar-files:{388}, redisson__execute_task_once_latch:redis-avatar-files:{388}, 1685062885734, 100, ...] from slot NodeSource [slot=10130, addr=null, redisClient=null, redirect=null, entry=null] using node 10.110.144.247/10.110.144.247:6379... RedisConnection@266702834 [redisClient=[addr=rediss://10.110.144.247:6379], channel=[id: 0xc614c9e1, L:/10.110.144.84:39272 - R:10.110.144.247/10.110.144.247:6379], currentCommand=null, usage=1]
2023-05-26 09:01:25.735 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0xc614c9e1, L:/10.110.144.84:39272 - R:10.110.144.247/10.110.144.247:6379] message: *13
$4
EVAL
$1824
if redis.call('setnx', KEYS[6], ARGV[4]) == 0 then return -1;end;redis.call('expire', KEYS[6], ARGV[3]); local expiredKeys1 = redis.call('zrangebyscore', KEYS[2], 0, ARGV[1], 'limit', 0, ARGV[2]); for i, key in ipairs(expiredKeys1) do local v = redis.call('hget', KEYS[1], key); if v ~= false then local t, val = struct.unpack('dLc0', v); local msg = struct.pack('Lc0Lc0', string.len(key), key, string.len(val), val); local listeners = redis.call('publish', KEYS[4], msg); if (listeners == 0) then break;end; end;end;for i=1, #expiredKeys1, 5000 do redis.call('zrem', KEYS[5], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); redis.call('zrem', KEYS[3], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); redis.call('zrem', KEYS[2], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); redis.call('hdel', KEYS[1], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); end; local expiredKeys2 = redis.call('zrangebyscore', KEYS[3], 0, ARGV[1], 'limit', 0, ARGV[2]); for i, key in ipairs(expiredKeys2) do local v = redis.call('hget', KEYS[1], key); if v ~= false then local t, val = struct.unpack('dLc0', v); local msg = struct.pack('Lc0Lc0', string.len(key), key, string.len(val), val); local listeners = redis.call('publish', KEYS[4], msg); if (listeners == 0) then break;end; end;end;for i=1, #expiredKeys2, 5000 do redis.call('zrem', KEYS[5], unpack(expiredKeys2, i, math.min(i+4999, table.getn(expiredKeys2)))); redis.call('zrem', KEYS[3], unpack(expiredKeys2, i, math.min(i+4999, table.getn(expiredKeys2)))); redis.call('zrem', KEYS[2], unpack(expiredKeys2, i, math.min(i+4999, table.getn(expiredKeys2)))); redis.call('hdel', KEYS[1], unpack(expiredKeys2, i, math.min(i+4999, table.getn(expiredKeys2)))); end; return #expiredKeys1 + #expiredKeys2;
$1
6
$24
redis-avatar-files:{388}
$47
redisson__timeout__set:redis-avatar-files:{388}
$44
redisson__idle__set:redis-avatar-files:{388}
$51
redisson_map_cache_expired:redis-avatar-files:{388}
$62
redisson__map_cache__last_access__set:redis-avatar-files:{388}
$58
redisson__execute_task_once_latch:redis-avatar-files:{388}
$13
1685062885734
$3
100
$2
30
$1
1

2023-05-26 09:01:25.736 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: :0
, channel: [id: 0xc614c9e1, L:/10.110.144.84:39272 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5c78acef[Not completed, 1 dependents], command=(EVAL), params=[if redis.call('setnx', KEYS[6], ARGV[4]) == 0 then return -1;end;redis.call('expire', KEYS[6], ARGV[3]); local expiredKeys1 = redis.call('zrangebyscore', KEYS[2], 0, ARGV[1], 'limit', 0, ARGV[2]); for i, key in ipairs(expiredKeys1) do local v = redis.call('hget', KEYS[1], key); if v ~= false then local t, val = struct.unpack('dLc0', v); local msg = struct.pack('Lc0Lc0', string.len(key), key, string.len(val), val); local listeners = redis.call('publish', KEYS[4], msg); if (listeners == 0) then break;end; end;end;for i=1, #expiredKeys1, 5000 do redis.call('zrem', KEYS[5], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); redis.call('zrem', KEYS[3], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); redis.call('zrem', KEYS[2], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); redis.call('hdel', KEYS[1], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); end; local expiredKeys2 = redis.call('zrangebyscore', KEYS[..., 6, redis-avatar-files:{388}, redisson__timeout__set:redis-avatar-files:{388}, redisson__idle__set:redis-avatar-files:{388}, redisson_map_cache_expired:redis-avatar-files:{388}, redisson__map_cache__last_access__set:redis-avatar-files:{388}, redisson__execute_task_once_latch:redis-avatar-files:{388}, 1685062885734, 100, ...], codec=org.redisson.client.codec.LongCodec]
2023-05-26 09:01:25.736 DEBUG 1 --- [sson-netty-3-27] org.redisson.command.RedisExecutor       : connection released for command (EVAL) and params [if redis.call('setnx', KEYS[6], ARGV[4]) == 0 then return -1;end;redis.call('expire', KEYS[6], ARGV[3]); local expiredKeys1 = redis.call('zrangebyscore', KEYS[2], 0, ARGV[1], 'limit', 0, ARGV[2]); for i, key in ipairs(expiredKeys1) do local v = redis.call('hget', KEYS[1], key); if v ~= false then local t, val = struct.unpack('dLc0', v); local msg = struct.pack('Lc0Lc0', string.len(key), key, string.len(val), val); local listeners = redis.call('publish', KEYS[4], msg); if (listeners == 0) then break;end; end;end;for i=1, #expiredKeys1, 5000 do redis.call('zrem', KEYS[5], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); redis.call('zrem', KEYS[3], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); redis.call('zrem', KEYS[2], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); redis.call('hdel', KEYS[1], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); end; local expiredKeys2 = redis.call('zrangebyscore', KEYS[..., 6, redis-avatar-files:{388}, redisson__timeout__set:redis-avatar-files:{388}, redisson__idle__set:redis-avatar-files:{388}, redisson_map_cache_expired:redis-avatar-files:{388}, redisson__map_cache__last_access__set:redis-avatar-files:{388}, redisson__execute_task_once_latch:redis-avatar-files:{388}, 1685062885734, 100, ...] from slot NodeSource [slot=10130, addr=null, redisClient=null, redirect=null, entry=null] using connection RedisConnection@266702834 [redisClient=[addr=rediss://10.110.144.247:6379], channel=[id: 0xc614c9e1, L:/10.110.144.84:39272 - R:10.110.144.247/10.110.144.247:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@5c78acef[Completed normally], command=(EVAL), params=[if redis.call('setnx', KEYS[6], ARGV[4]) == 0 then return -1;end;redis.call('expire', KEYS[6], ARGV[3]); local expiredKeys1 = redis.call('zrangebyscore', KEYS[2], 0, ARGV[1], 'limit', 0, ARGV[2]); for i, key in ipairs(expiredKeys1) do local v = redis.call('hget', KEYS[1], key); if v ~= false then local t, val = struct.unpack('dLc0', v); local msg = struct.pack('Lc0Lc0', string.len(key), key, string.len(val), val); local listeners = redis.call('publish', KEYS[4], msg); if (listeners == 0) then break;end; end;end;for i=1, #expiredKeys1, 5000 do redis.call('zrem', KEYS[5], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); redis.call('zrem', KEYS[3], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); redis.call('zrem', KEYS[2], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); redis.call('hdel', KEYS[1], unpack(expiredKeys1, i, math.min(i+4999, table.getn(expiredKeys1)))); end; local expiredKeys2 = redis.call('zrangebyscore', KEYS[..., 6, redis-avatar-files:{388}, redisson__timeout__set:redis-avatar-files:{388}, redisson__idle__set:redis-avatar-files:{388}, redisson_map_cache_expired:redis-avatar-files:{388}, redisson__map_cache__last_access__set:redis-avatar-files:{388}, redisson__execute_task_once_latch:redis-avatar-files:{388}, 1685062885734, 100, ...], codec=org.redisson.client.codec.LongCodec], usage=0]
2023-05-26 09:01:25.737 DEBUG 1 --- [sson-netty-3-27] o.r.eviction.MapCacheEvictionTask        : 0 elements evicted. Object name: redis-avatar-files:{388}
2023-05-26 09:01:26.424 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:26.426 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062883341 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062883000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062886367 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062883000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062884350 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062880000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062885000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062885358 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062882331 5 connected

, channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@322b68ea[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:26.426 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.144.247/10.110.144.247:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062883341 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062883000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062886367 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062883000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062884350 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062880000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062885000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062885358 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062882331 5 connected

2023-05-26 09:01:26.764 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:26.765 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@126edbf4[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:27.431 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:27.432 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062883000 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062884000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062886107 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062886000 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062885098 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062887114 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062885000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062883000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062884000 5 connected

, channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4ecb3332[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:27.432 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.142.16/10.110.142.16:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062883000 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062884000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062886107 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062886000 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062885098 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062887114 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062885000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062883000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062884000 5 connected

2023-05-26 09:01:28.439 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:28.439 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062886000 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062887155 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062886145 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062884000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062884000 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062887000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062885000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062888159 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062882000 6 connected 5462-10922

, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@78a4c059[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:28.440 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.229/10.110.154.229:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062886000 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062887155 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062886145 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062884000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062884000 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062887000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062885000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062888159 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062882000 6 connected 5462-10922

2023-05-26 09:01:29.445 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:29.446 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: $1894
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062888884 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062885857 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062882000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062886000 4 connected 10923-16383
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062883000 5 connected 0-5461
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062887000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062887000 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062887875 5 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062886000 6 connected

, channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@f848412[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:29.446 DEBUG 1 --- [sson-netty-3-22] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.136.174/10.110.136.174:6379:
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062888884 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062885857 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062882000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062886000 4 connected 10923-16383
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062883000 5 connected 0-5461
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062887000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062887000 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062887875 5 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062886000 6 connected

2023-05-26 09:01:29.551  INFO 1 --- [io-63000-exec-6] c.x.a.r.c.IndexWriterController          : IndexWriterController ping
2023-05-26 09:01:29.965 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:29.966 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1c114a7c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:30.453 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:30.457 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062888000 6 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062887000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062887630 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062889648 5 connected 0-5461
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062888000 4 connected 10923-16383
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062888638 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062886000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062885614 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062886622 4 connected

, channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5c56ce13[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:30.457 DEBUG 1 --- [sson-netty-3-15] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.156.54/10.110.156.54:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062888000 6 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062887000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062887630 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062889648 5 connected 0-5461
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062888000 4 connected 10923-16383
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062888638 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062886000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062885614 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062886622 4 connected

2023-05-26 09:01:31.462 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:31.465 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062888000 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062887155 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062889000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062889000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062889167 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062890177 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062891187 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062890000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062889573 6 connected 5462-10922

, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@22681e7f[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:31.465 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.229/10.110.154.229:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062888000 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062887155 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062889000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062889000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062889167 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062890177 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062891187 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062890000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062889573 6 connected 5462-10922

2023-05-26 09:01:32.472 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:32.472 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062888000 6 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062889000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062888000 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062890000 5 connected 0-5461
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062888000 4 connected 10923-16383
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062890000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062890662 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062891670 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062890000 4 connected

, channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1e94a28f[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:32.473 DEBUG 1 --- [sson-netty-3-15] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.156.54/10.110.156.54:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062888000 6 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062889000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062888000 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062890000 5 connected 0-5461
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062888000 4 connected 10923-16383
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062890000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062890662 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062891670 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062890000 4 connected

2023-05-26 09:01:33.479 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x0dea50d8, L:/10.110.144.84:45776 - R:10.110.154.77/10.110.154.77:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:33.480 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: $1894
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062891000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062887000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062892955 5 connected 0-5461
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062890937 6 connected 5462-10922
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062888000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062889000 4 connected 10923-16383
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062890000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062891000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062891946 6 connected

, channel: [id: 0x0dea50d8, L:/10.110.144.84:45776 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@f625f40[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:33.480 DEBUG 1 --- [sson-netty-3-28] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.77/10.110.154.77:6379:
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062891000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062887000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062892955 5 connected 0-5461
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062890937 6 connected 5462-10922
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062888000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062889000 4 connected 10923-16383
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062890000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062891000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062891946 6 connected

2023-05-26 09:01:34.487 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:34.488 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062892000 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062891000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062888000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062892000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062890092 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062888000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062893119 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062894125 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062892108 6 connected

, channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@742decdb[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:34.489 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379:
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062892000 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062891000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062888000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062892000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062890092 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062888000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062893119 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062894125 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062892108 6 connected

2023-05-26 09:01:35.496 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:35.496 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062892000 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062892421 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062893000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062893430 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062892000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062891000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062891410 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062895451 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062894441 5 connected

, channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1595f9cc[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:35.497 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.144.247/10.110.144.247:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062892000 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062892421 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062893000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062893430 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062892000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062891000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062891410 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062895451 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062894441 5 connected

2023-05-26 09:01:36.503 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:36.503 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: $1894
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062892000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062894000 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062882000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062892918 4 connected 10923-16383
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062893000 5 connected 0-5461
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062892000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062895951 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062895000 5 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062894000 6 connected

, channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2f289855[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:36.504 DEBUG 1 --- [sson-netty-3-22] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.136.174/10.110.136.174:6379:
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062892000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062894000 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062882000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062892918 4 connected 10923-16383
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062893000 5 connected 0-5461
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062892000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062895951 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062895000 5 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062894000 6 connected

2023-05-26 09:01:37.064 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.064 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0xf4fa2716, L:/10.110.144.84:52690 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.064 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x29287aa4, L:/10.110.144.84:52674 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.064 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x092211ef, L:/10.110.144.84:52700 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.064 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x340eb3de, L:/10.110.144.84:52654 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.064 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xacf35917, L:/10.110.144.84:52652 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.064 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x70380bd3, L:/10.110.144.84:52666 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.065 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf4fa2716, L:/10.110.144.84:52690 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@79ef2dfd[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.065 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x29287aa4, L:/10.110.144.84:52674 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@54461040[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.065 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4e5535eb[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.065 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x092211ef, L:/10.110.144.84:52700 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@36131a3c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.065 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x340eb3de, L:/10.110.144.84:52654 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@544639da[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.065 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0xacf35917, L:/10.110.144.84:52652 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@701c154f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.065 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x70380bd3, L:/10.110.144.84:52666 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@634b4083[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.164 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x9af51b9b, L:/10.110.144.84:52714 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.164 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0x5d9d8a2f, L:/10.110.144.84:52748 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.164 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0x9b21c02e, L:/10.110.144.84:52734 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.164 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0xf2f7a384, L:/10.110.144.84:52798 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.164 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x523b6e77, L:/10.110.144.84:52768 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.165 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x6843b4fb, L:/10.110.144.84:52808 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.165 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0xef8d5a6b, L:/10.110.144.84:52762 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.165 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0xd9718309, L:/10.110.144.84:52824 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.165 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0xb7d08619, L:/10.110.144.84:52758 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.165 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0xb71e8021, L:/10.110.144.84:52812 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.165 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xef8d5a6b, L:/10.110.144.84:52762 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@758a8297[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.165 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x0aec2d61, L:/10.110.144.84:52792 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.165 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5d9d8a2f, L:/10.110.144.84:52748 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@68251a1[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.164 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x36af954f, L:/10.110.144.84:52716 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.165 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9af51b9b, L:/10.110.144.84:52714 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5551c39e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.165 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9b21c02e, L:/10.110.144.84:52734 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@557583dd[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.165 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xd56d05e3, L:/10.110.144.84:52784 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.165 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb7d08619, L:/10.110.144.84:52758 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6b2c1f61[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.164 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0xd60af23b, L:/10.110.144.84:52718 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.165 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6843b4fb, L:/10.110.144.84:52808 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7b7a55a3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.165 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x36af954f, L:/10.110.144.84:52716 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6f6e789f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.164 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x0580830a, L:/10.110.144.84:52772 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.165 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb71e8021, L:/10.110.144.84:52812 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5299c5a3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.165 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0aec2d61, L:/10.110.144.84:52792 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@21b6dd24[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.165 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf2f7a384, L:/10.110.144.84:52798 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@66ae0eee[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.165 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x523b6e77, L:/10.110.144.84:52768 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@619102c0[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.165 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd9718309, L:/10.110.144.84:52824 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@51d05dff[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.166 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0580830a, L:/10.110.144.84:52772 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4d79f08[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.166 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd60af23b, L:/10.110.144.84:52718 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1b182f96[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.166 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd56d05e3, L:/10.110.144.84:52784 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@75bcf774[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.264 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x3380aecd, L:/10.110.144.84:52826 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.265 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0x564f0265, L:/10.110.144.84:52872 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.265 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0xbf65c213, L:/10.110.144.84:52854 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.264 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0xf931d36e, L:/10.110.144.84:52832 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.265 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0xe1e6bd8f, L:/10.110.144.84:52924 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.264 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xa6ccd892, L:/10.110.144.84:52828 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.265 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0x6009cc6c, L:/10.110.144.84:52838 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.265 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x7dd7e63c, L:/10.110.144.84:52892 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.265 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x7d159085, L:/10.110.144.84:52886 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.265 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0x28e06be0, L:/10.110.144.84:52860 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.265 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbf65c213, L:/10.110.144.84:52854 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5dc3e586[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.265 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7d159085, L:/10.110.144.84:52886 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@57b8f299[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.265 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe1e6bd8f, L:/10.110.144.84:52924 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@70aa5e58[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.265 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa6ccd892, L:/10.110.144.84:52828 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6eea9361[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.265 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7dd7e63c, L:/10.110.144.84:52892 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4e35e020[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.265 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x29144e0e, L:/10.110.144.84:52906 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.265 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3380aecd, L:/10.110.144.84:52826 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1f3e75eb[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.265 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x28e06be0, L:/10.110.144.84:52860 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3d9c5522[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.265 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x564f0265, L:/10.110.144.84:52872 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@77bd05b9[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.265 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x60abf31c, L:/10.110.144.84:52922 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:01:37.266 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf931d36e, L:/10.110.144.84:52832 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@550fb727[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.265 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6009cc6c, L:/10.110.144.84:52838 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4343e8f8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.266 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x60abf31c, L:/10.110.144.84:52922 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@206fe266[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.266 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x29144e0e, L:/10.110.144.84:52906 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@54029eeb[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:37.512 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:37.513 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062895000 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062895000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062896229 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062895000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062895223 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062896000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062892000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062897243 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062894213 6 connected 5462-10922

, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1b029b94[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:37.513 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.229/10.110.154.229:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062895000 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062895000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062896229 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062895000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062895223 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062896000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062892000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062897243 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062894213 6 connected 5462-10922

2023-05-26 09:01:38.604 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:38.609 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062897153 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062895000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062896000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062898162 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062896147 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062895137 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062897000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062895000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062896000 6 connected

, channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3ba7bcf[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:38.609 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379:
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062897153 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062895000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062896000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062898162 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062896147 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062895137 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062897000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062895000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062896000 6 connected

2023-05-26 09:01:39.552  INFO 1 --- [io-63000-exec-7] c.x.a.r.c.IndexWriterController          : IndexWriterController ping
2023-05-26 09:01:39.615 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:39.615 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062897153 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062899171 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062898000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062898162 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062896147 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062897000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062897000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062895000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062896000 6 connected

, channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@11af2b9b[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:39.615 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379:
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062897153 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062899171 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062898000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062898162 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062896147 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062897000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062897000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062895000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062896000 6 connected

2023-05-26 09:01:40.621 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:40.622 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062896461 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062897470 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062895000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062899490 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062899000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062897000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062898000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062900499 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062898481 5 connected

, channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@60a93aee[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:40.622 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.144.247/10.110.144.247:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062896461 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062897470 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062895000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062899490 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062899000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062897000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062898000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062900499 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062898481 5 connected

2023-05-26 09:01:41.629 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:41.629 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062899259 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062898251 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062898000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062899000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062898000 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062901000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062901273 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062897243 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062897000 6 connected 5462-10922

, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4766e3fa[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:41.630 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.229/10.110.154.229:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062899259 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062898251 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062898000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062899000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062898000 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062901000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062901273 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062897243 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062897000 6 connected 5462-10922

2023-05-26 09:01:42.638 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:42.639 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062899000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062898000 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062900885 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062900000 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062898000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062900000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062901895 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062897000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062901000 6 connected

, channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@13f893c7[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:42.639 DEBUG 1 --- [sson-netty-3-14] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.141.243/10.110.141.243:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062899000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062898000 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062900885 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062900000 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062898000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062900000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062901895 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062897000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062901000 6 connected

2023-05-26 09:01:43.645 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:43.647 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062903559 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062901000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062900231 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062900000 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062903254 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062903000 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062897605 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062902247 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062900000 5 connected

, channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5917e936[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:43.647 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.142.16/10.110.142.16:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062903559 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062901000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062900231 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062900000 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062903254 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062903000 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062897605 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062902247 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062900000 5 connected

2023-05-26 09:01:44.658 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:44.659 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062903559 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062901000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062900231 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062902000 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062903254 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062903000 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062897605 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062902247 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062904263 5 connected

, channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6686429c[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:44.660 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.142.16/10.110.142.16:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062903559 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062901000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062900231 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062902000 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062903254 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062903000 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062897605 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062902247 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062904263 5 connected

2023-05-26 09:01:45.667 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:45.668 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062904000 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062903530 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062901508 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062904538 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062901000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062903000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062903000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062905547 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062904000 5 connected

, channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@430690eb[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:45.668 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.144.247/10.110.144.247:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062904000 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062903530 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062901508 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062904538 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062901000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062903000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062903000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062905547 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062904000 5 connected

2023-05-26 09:01:46.674 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x0dea50d8, L:/10.110.144.84:45776 - R:10.110.154.77/10.110.154.77:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:46.675 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: $1894
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062904000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062903000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062902031 5 connected 0-5461
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062903041 6 connected 5462-10922
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062905000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062905057 4 connected 10923-16383
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062901025 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062902000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062906066 6 connected

, channel: [id: 0x0dea50d8, L:/10.110.144.84:45776 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@44552735[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:46.675 DEBUG 1 --- [sson-netty-3-28] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.77/10.110.154.77:6379:
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062904000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062903000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062902031 5 connected 0-5461
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062903041 6 connected 5462-10922
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062905000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062905057 4 connected 10923-16383
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062901025 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062902000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062906066 6 connected

2023-05-26 09:01:47.464 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xe3825aed, L:/10.110.144.84:42734 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.464 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0x49034abd, L:/10.110.144.84:42756 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.464 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0x1230d5b1, L:/10.110.144.84:42720 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.464 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x5d451a83, L:/10.110.144.84:42684 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.465 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0x00d8ac77, L:/10.110.144.84:42752 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.464 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x6bc7d52b, L:/10.110.144.84:42706 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.465 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x9ec09ec4, L:/10.110.144.84:42766 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.465 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x718982ca, L:/10.110.144.84:42744 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.465 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x8b328e3d, L:/10.110.144.84:42768 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.464 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x638588a3, L:/10.110.144.84:42686 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.465 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9ec09ec4, L:/10.110.144.84:42766 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2cad6a13[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.465 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0x638588a3, L:/10.110.144.84:42686 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3446e21f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.465 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1230d5b1, L:/10.110.144.84:42720 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@35f36584[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.466 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x00d8ac77, L:/10.110.144.84:42752 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1f05ad7e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.466 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8b328e3d, L:/10.110.144.84:42768 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@666a9b84[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.466 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe3825aed, L:/10.110.144.84:42734 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3b71e019[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.466 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6bc7d52b, L:/10.110.144.84:42706 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@230d8155[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.466 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5d451a83, L:/10.110.144.84:42684 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@56f5135b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.466 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x49034abd, L:/10.110.144.84:42756 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1b78164b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.466 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x718982ca, L:/10.110.144.84:42744 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5f966187[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.564 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0xbf6a03b6, L:/10.110.144.84:42792 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.565 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xb3fdef01, L:/10.110.144.84:42826 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.565 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0xfe71ad77, L:/10.110.144.84:42862 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.565 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x9e0249f6, L:/10.110.144.84:42814 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.565 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0x95188a3c, L:/10.110.144.84:48150 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.565 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xe8cffa89, L:/10.110.144.84:42876 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.564 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xc17e083d, L:/10.110.144.84:42780 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.564 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x6676572f, L:/10.110.144.84:42798 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.565 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0x2d461361, L:/10.110.144.84:42866 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.565 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x849154fc, L:/10.110.144.84:42854 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.565 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb3fdef01, L:/10.110.144.84:42826 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@75d392f7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.565 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfe71ad77, L:/10.110.144.84:42862 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3883826b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.565 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x65ce0e77, L:/10.110.144.84:42844 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.566 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbf6a03b6, L:/10.110.144.84:42792 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@d7742d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.565 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0x95188a3c, L:/10.110.144.84:48150 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@755a7e1e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.566 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6676572f, L:/10.110.144.84:42798 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@61abb8d3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.566 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc17e083d, L:/10.110.144.84:42780 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7e798019[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.566 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x849154fc, L:/10.110.144.84:42854 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3f0d7587[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.566 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2d461361, L:/10.110.144.84:42866 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@13957d0a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.565 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x198f5dc0, L:/10.110.144.84:42892 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.565 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x45762bf3, L:/10.110.144.84:48152 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.566 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe8cffa89, L:/10.110.144.84:42876 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@15635341[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.565 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x5f96959c, L:/10.110.144.84:42832 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.565 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9e0249f6, L:/10.110.144.84:42814 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@a77170b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.566 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x65ce0e77, L:/10.110.144.84:42844 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@79decf39[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.567 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x198f5dc0, L:/10.110.144.84:42892 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6611d0ec[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.567 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x45762bf3, L:/10.110.144.84:48152 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1aec7ba1[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.567 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5f96959c, L:/10.110.144.84:42832 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@12d83691[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.665 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x206b6d8a, L:/10.110.144.84:42910 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.665 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x5b2d9724, L:/10.110.144.84:42962 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.665 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0xa3d1fa19, L:/10.110.144.84:48194 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.665 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x387347f0, L:/10.110.144.84:48242 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.665 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0x365ab65c, L:/10.110.144.84:42904 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.665 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0x6deb51e6, L:/10.110.144.84:48192 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.665 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x48fe8a1d, L:/10.110.144.84:42920 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.665 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0xdd2a6659, L:/10.110.144.84:42934 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.665 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0xab48a4fb, L:/10.110.144.84:42950 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.665 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0xa6da8ad5, L:/10.110.144.84:42974 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.665 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0xfaebdc54, L:/10.110.144.84:48240 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.665 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0xbbe1edf4, L:/10.110.144.84:42908 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.666 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0xba9912e9, L:/10.110.144.84:48172 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.666 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5b2d9724, L:/10.110.144.84:42962 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1eaf7e1b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.665 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xd386ccc3, L:/10.110.144.84:42924 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.666 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x387347f0, L:/10.110.144.84:48242 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1d386e79[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.666 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xdd2a6659, L:/10.110.144.84:42934 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1bc47ee6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.665 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0xf749d129, L:/10.110.144.84:42932 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.665 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x3b9829b5, L:/10.110.144.84:48234 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.665 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0x94aee659, L:/10.110.144.84:42954 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:47.665 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0x9379b00d, L:/10.110.144.84:48176 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.666 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6deb51e6, L:/10.110.144.84:48192 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@21b9d03c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.666 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xba9912e9, L:/10.110.144.84:48172 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6afbdcb2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.666 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3b9829b5, L:/10.110.144.84:48234 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6782b534[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.666 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa6da8ad5, L:/10.110.144.84:42974 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@63e67277[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.665 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0xbdfab9a9, L:/10.110.144.84:48210 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.665 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x8b1681e6, L:/10.110.144.84:48224 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.665 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x3cd8b701, L:/10.110.144.84:48216 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.667 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbdfab9a9, L:/10.110.144.84:48210 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@10782c31[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.667 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x94aee659, L:/10.110.144.84:42954 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5f584cb5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.667 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf749d129, L:/10.110.144.84:42932 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1f1425a3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.667 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9379b00d, L:/10.110.144.84:48176 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5db0d432[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.667 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd386ccc3, L:/10.110.144.84:42924 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@796cb4a3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.667 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3cd8b701, L:/10.110.144.84:48216 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@16868ccc[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.667 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbbe1edf4, L:/10.110.144.84:42908 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@74c99793[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.666 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x365ab65c, L:/10.110.144.84:42904 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@38675919[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.667 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8b1681e6, L:/10.110.144.84:48224 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@15f6e56b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.666 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa3d1fa19, L:/10.110.144.84:48194 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1de11686[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.667 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x206b6d8a, L:/10.110.144.84:42910 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5dc178b3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.666 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xab48a4fb, L:/10.110.144.84:42950 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5e0aa445[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.666 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfaebdc54, L:/10.110.144.84:48240 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@18172a67[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.666 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x48fe8a1d, L:/10.110.144.84:42920 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@750f26b8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.680 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:47.681 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062906318 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062905000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062905000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062904000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062905000 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062906000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062903000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062902283 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062907329 6 connected 5462-10922

, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6a652235[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:47.681 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.229/10.110.154.229:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062906318 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062905000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062905000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062904000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062905000 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062906000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062903000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062902283 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062907329 6 connected 5462-10922

2023-05-26 09:01:47.764 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0xdb123917, L:/10.110.144.84:48258 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.764 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x14fca1d2, L:/10.110.144.84:48372 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.764 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0xfc3c2d92, L:/10.110.144.84:48346 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.764 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x3600290d, L:/10.110.144.84:48278 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.765 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0xe0cb5c04, L:/10.110.144.84:48340 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.765 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x03756278, L:/10.110.144.84:48360 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.765 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0x374cbfef, L:/10.110.144.84:48310 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.765 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xf2b1e2d3, L:/10.110.144.84:48290 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.765 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3600290d, L:/10.110.144.84:48278 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@b3b7a9f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.764 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x1821dec4, L:/10.110.144.84:48266 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.765 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfc3c2d92, L:/10.110.144.84:48346 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1d47ca6f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.764 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0xeffc9c7e, L:/10.110.144.84:48322 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.765 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xdb123917, L:/10.110.144.84:48258 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5650c46e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.765 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x7641bb4d, L:/10.110.144.84:48296 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.765 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x374cbfef, L:/10.110.144.84:48310 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6e1d4002[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.765 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x4b20306c, L:/10.110.144.84:48356 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.765 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0xa0241a4c, L:/10.110.144.84:48338 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.765 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x14fca1d2, L:/10.110.144.84:48372 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@433f6aab[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.765 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe0cb5c04, L:/10.110.144.84:48340 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1bee6904[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.766 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf2b1e2d3, L:/10.110.144.84:48290 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7a072e0a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.766 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa0241a4c, L:/10.110.144.84:48338 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@25279390[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.766 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x4b20306c, L:/10.110.144.84:48356 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@14d4bd86[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.765 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x03756278, L:/10.110.144.84:48360 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2475a741[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.766 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1821dec4, L:/10.110.144.84:48266 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@69aa6371[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.766 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7641bb4d, L:/10.110.144.84:48296 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1d93665a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.766 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xeffc9c7e, L:/10.110.144.84:48322 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@39cfedc8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.865 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x0e3613c2, L:/10.110.144.84:48402 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.865 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xf677ce8a, L:/10.110.144.84:48416 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.865 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x6163387d, L:/10.110.144.84:48388 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.865 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x517c3175, L:/10.110.144.84:48378 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.865 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0xf497b622, L:/10.110.144.84:48414 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.865 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x47c5d6c9, L:/10.110.144.84:48384 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.865 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x2665b389, L:/10.110.144.84:48422 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.865 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x5e54b467, L:/10.110.144.84:48394 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:47.865 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf497b622, L:/10.110.144.84:48414 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5c0ab694[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.865 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0e3613c2, L:/10.110.144.84:48402 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@444536a5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.865 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf677ce8a, L:/10.110.144.84:48416 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5e46c73a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.865 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x517c3175, L:/10.110.144.84:48378 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3da520ba[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.865 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6163387d, L:/10.110.144.84:48388 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@62fe5d79[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.866 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x47c5d6c9, L:/10.110.144.84:48384 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@306c7de[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.866 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2665b389, L:/10.110.144.84:48422 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7a448113[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:47.866 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5e54b467, L:/10.110.144.84:48394 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@24a08403[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:48.664 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:48.665 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1350e9f4[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:48.691 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:48.692 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062905000 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062901000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062906279 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062904000 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062908302 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062907290 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062906000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062905271 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062907000 5 connected

, channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@31af8b48[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:48.692 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.142.16/10.110.142.16:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062905000 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062901000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062906279 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062904000 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062908302 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062907290 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062906000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062905271 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062907000 5 connected

2023-05-26 09:01:48.965 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:48.965 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:48.965 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:48.965 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@784b731f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:48.965 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@38cdc89[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:48.966 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@63ff0fcf[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.164 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x2faa9b7f, L:/10.110.144.84:35588 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:49.164 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x44f83714, L:/10.110.144.84:33032 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:49.164 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0x20fee0ee, L:/10.110.144.84:35604 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:49.164 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0x20fee0ee, L:/10.110.144.84:35604 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@57028cc8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.165 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2faa9b7f, L:/10.110.144.84:35588 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@54fd1f52[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.165 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x44f83714, L:/10.110.144.84:33032 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5046bc2e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.264 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x5350dfc0, L:/10.110.144.84:39162 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:49.264 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x0c5aa2cc, L:/10.110.144.84:33042 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:49.264 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x5d211705, L:/10.110.144.84:39152 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:49.264 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x6c1866f4, L:/10.110.144.84:39166 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:49.264 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x1fa475cc, L:/10.110.144.84:33052 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:49.265 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0x9f09d9d3, L:/10.110.144.84:35608 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:49.265 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6c1866f4, L:/10.110.144.84:39166 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2dab7396[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.265 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0x5d211705, L:/10.110.144.84:39152 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@53003c22[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.265 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5350dfc0, L:/10.110.144.84:39162 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@17146c92[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.265 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0x0c5aa2cc, L:/10.110.144.84:33042 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@230db432[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.265 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9f09d9d3, L:/10.110.144.84:35608 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@73dd274d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.265 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1fa475cc, L:/10.110.144.84:33052 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6a2d5514[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.364 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x5efeef3a, L:/10.110.144.84:39178 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:49.364 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x50af68d4, L:/10.110.144.84:33060 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:49.365 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5efeef3a, L:/10.110.144.84:39178 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4b6cbc0a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.365 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x50af68d4, L:/10.110.144.84:33060 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3bff6562[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.464 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xfc8e6f66, L:/10.110.144.84:35610 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:49.464 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x49f89c18, L:/10.110.144.84:39194 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:49.464 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0x3d424622, L:/10.110.144.84:33064 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:49.465 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfc8e6f66, L:/10.110.144.84:35610 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@268f5225[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.465 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3d424622, L:/10.110.144.84:33064 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@32c57111[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.465 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x49f89c18, L:/10.110.144.84:39194 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@40bb2247[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.551  INFO 1 --- [io-63000-exec-8] c.x.a.r.c.IndexWriterController          : IndexWriterController ping
2023-05-26 09:01:49.565 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0x4d2f27be, L:/10.110.144.84:39208 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:49.565 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x4d2f27be, L:/10.110.144.84:39208 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@18ebac5f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.665 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x1eec75c6, L:/10.110.144.84:33076 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:49.665 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0x5a5b9307, L:/10.110.144.84:35618 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:49.665 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x2f4e473f, L:/10.110.144.84:35634 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:49.665 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x317d7e53, L:/10.110.144.84:33068 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:49.665 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0xe9b5ecaa, L:/10.110.144.84:39216 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:49.665 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5a5b9307, L:/10.110.144.84:35618 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7c8116d8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.665 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2f4e473f, L:/10.110.144.84:35634 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@991b3f2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.666 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe9b5ecaa, L:/10.110.144.84:39216 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@41bd666d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.666 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x317d7e53, L:/10.110.144.84:33068 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@57bc3989[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.666 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1eec75c6, L:/10.110.144.84:33076 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@8094cb4[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.703 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:49.704 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062908000 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062907000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062905000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062908257 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062909267 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062907000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062905000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062906000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062907000 6 connected

, channel: [id: 0xaa46b69d, L:/10.110.144.84:42496 - R:clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@544e68fb[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:49.704 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from clustercfg.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com/10.110.144.233:6379:
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062908000 5 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062907000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062905000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062908257 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062909267 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062907000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062905000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062906000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062907000 6 connected

2023-05-26 09:01:49.764 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0xdb9c7f7d, L:/10.110.144.84:35638 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:49.764 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xd18c14e9, L:/10.110.144.84:39222 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:49.764 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd18c14e9, L:/10.110.144.84:39222 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@40c524cf[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.765 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xdb9c7f7d, L:/10.110.144.84:35638 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6f7be6fa[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.864 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x2f9ba3aa, L:/10.110.144.84:35646 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:49.864 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x3a35f9d3, L:/10.110.144.84:39230 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:49.864 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x0df23ba1, L:/10.110.144.84:33088 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:49.865 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2f9ba3aa, L:/10.110.144.84:35646 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7ba3e43e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.865 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3a35f9d3, L:/10.110.144.84:39230 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6b32f7a9[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.865 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0df23ba1, L:/10.110.144.84:33088 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4e6a15ed[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.964 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x5ea4d9a0, L:/10.110.144.84:35648 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:49.964 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x1928f81a, L:/10.110.144.84:33096 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:49.964 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0xe54f5a82, L:/10.110.144.84:33112 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:49.964 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xa5b70b5f, L:/10.110.144.84:39242 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:49.965 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0x5d9b6fbc, L:/10.110.144.84:33116 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:49.965 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5ea4d9a0, L:/10.110.144.84:35648 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@10d345d8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.965 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa5b70b5f, L:/10.110.144.84:39242 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1d0346b2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.965 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1928f81a, L:/10.110.144.84:33096 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7cdfb422[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.965 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe54f5a82, L:/10.110.144.84:33112 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@469c3dbc[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:49.965 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5d9b6fbc, L:/10.110.144.84:33116 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1cdf2fed[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.064 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0x8226bc27, L:/10.110.144.84:33132 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.065 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0x91b09ee6, L:/10.110.144.84:35656 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.064 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0xe5202825, L:/10.110.144.84:39250 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.065 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x91b09ee6, L:/10.110.144.84:35656 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7d5a092f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.065 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe5202825, L:/10.110.144.84:39250 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@720aa9ee[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.065 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8226bc27, L:/10.110.144.84:33132 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7669913c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.165 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x0914946e, L:/10.110.144.84:39260 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.165 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x9cd44164, L:/10.110.144.84:39264 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.165 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xe6da5b3d, L:/10.110.144.84:35684 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.165 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0xad344030, L:/10.110.144.84:33142 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.165 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x5d7ee767, L:/10.110.144.84:35672 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.165 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x9ba4091d, L:/10.110.144.84:33152 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.165 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe6da5b3d, L:/10.110.144.84:35684 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@d7d1254[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.165 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5d7ee767, L:/10.110.144.84:35672 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@58591f55[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.166 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9cd44164, L:/10.110.144.84:39264 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6f0f4a55[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.166 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0914946e, L:/10.110.144.84:39260 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5285780[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.166 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xad344030, L:/10.110.144.84:33142 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@24996408[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.166 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9ba4091d, L:/10.110.144.84:33152 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1d22c534[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.265 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0xd2c461b0, L:/10.110.144.84:35698 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.265 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x60261659, L:/10.110.144.84:33174 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.265 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x0f7d5094, L:/10.110.144.84:39270 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.265 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x39bcc445, L:/10.110.144.84:33164 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.265 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x75b3a5e2, L:/10.110.144.84:39266 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.265 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0xe2163854, L:/10.110.144.84:35694 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.265 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd2c461b0, L:/10.110.144.84:35698 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1964ef40[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.265 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0f7d5094, L:/10.110.144.84:39270 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@180e7065[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.265 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe2163854, L:/10.110.144.84:35694 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@35a71710[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.266 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x75b3a5e2, L:/10.110.144.84:39266 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@11c25502[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.266 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x60261659, L:/10.110.144.84:33174 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3e731d86[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.266 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x39bcc445, L:/10.110.144.84:33164 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2b002c90[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.364 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0x82bc0c72, L:/10.110.144.84:33186 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.364 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x5e6938b9, L:/10.110.144.84:33194 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.364 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0x071a4ddc, L:/10.110.144.84:35722 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.364 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0x16b80e64, L:/10.110.144.84:35700 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.364 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0xd62e28a1, L:/10.110.144.84:35712 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.364 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x9e8db101, L:/10.110.144.84:39288 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.365 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x16b80e64, L:/10.110.144.84:35700 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5a9cff52[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.364 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0xc614c9e1, L:/10.110.144.84:39272 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.365 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5e6938b9, L:/10.110.144.84:33194 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@69d0a155[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.365 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x82bc0c72, L:/10.110.144.84:33186 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@29c0f2d9[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.365 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd62e28a1, L:/10.110.144.84:35712 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@74538f03[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.365 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9e8db101, L:/10.110.144.84:39288 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7aed646[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.365 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x071a4ddc, L:/10.110.144.84:35722 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@56191aba[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.365 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc614c9e1, L:/10.110.144.84:39272 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@71976961[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.464 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0xb5304c0b, L:/10.110.144.84:35738 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.464 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x609c717c, L:/10.110.144.84:33222 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.464 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x2ed0c7f3, L:/10.110.144.84:39318 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.464 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc24f08f, L:/10.110.144.84:33220 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.464 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0xfaafd2b4, L:/10.110.144.84:33210 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.464 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x112d9a77, L:/10.110.144.84:39296 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.464 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xb9b1ae85, L:/10.110.144.84:35756 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.464 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0x6edf1e25, L:/10.110.144.84:35746 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.464 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x7ebee1e9, L:/10.110.144.84:39306 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.465 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb5304c0b, L:/10.110.144.84:35738 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5a02485d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.465 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x112d9a77, L:/10.110.144.84:39296 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@61fdb606[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.465 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2ed0c7f3, L:/10.110.144.84:39318 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@27e1ad4[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.465 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x609c717c, L:/10.110.144.84:33222 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7d038f79[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.465 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7ebee1e9, L:/10.110.144.84:39306 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@320ad721[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.465 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xcc24f08f, L:/10.110.144.84:33220 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3f6027dc[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.465 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfaafd2b4, L:/10.110.144.84:33210 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@91686da[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.465 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6edf1e25, L:/10.110.144.84:35746 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@56d2269c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.465 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb9b1ae85, L:/10.110.144.84:35756 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7e67ab5f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.564 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0x7678bdca, L:/10.110.144.84:35762 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.565 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7678bdca, L:/10.110.144.84:35762 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@77e3bdf6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.665 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x9948b531, L:/10.110.144.84:33228 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.665 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0xdbce868f, L:/10.110.144.84:39334 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.665 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x7088f732, L:/10.110.144.84:35776 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.665 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0xe3ab2d80, L:/10.110.144.84:35764 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.665 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x82d0aa81, L:/10.110.144.84:33234 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.665 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xdbce868f, L:/10.110.144.84:39334 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7ef7c4e5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.665 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7088f732, L:/10.110.144.84:35776 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5d943001[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.665 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9948b531, L:/10.110.144.84:33228 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1f317e55[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.665 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe3ab2d80, L:/10.110.144.84:35764 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@19be97fd[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.666 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x82d0aa81, L:/10.110.144.84:33234 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3b154e6e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.709 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:50.710 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: $1894
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062909986 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062908000 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062906000 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062908971 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062907000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062905943 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062907000 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062906955 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062906000 6 connected

, channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@39929a7e[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:50.711 DEBUG 1 --- [isson-netty-3-6] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.129.61/10.110.129.61:6379:
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062909986 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062908000 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062906000 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062908971 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062907000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062905943 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062907000 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062906955 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062906000 6 connected

2023-05-26 09:01:50.765 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x43ebc634, L:/10.110.144.84:33238 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.765 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0xb3821264, L:/10.110.144.84:33254 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.765 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0xc6190f33, L:/10.110.144.84:33266 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.765 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0x20e3fa9d, L:/10.110.144.84:35808 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.765 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x47d47e68, L:/10.110.144.84:35798 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.765 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x4edd0935, L:/10.110.144.84:35790 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.765 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0xb42331de, L:/10.110.144.84:39348 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.765 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0xca900a49, L:/10.110.144.84:35800 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.765 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0xb72196e7, L:/10.110.144.84:33240 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.766 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x4edd0935, L:/10.110.144.84:35790 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1a8a2ad5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.766 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xca900a49, L:/10.110.144.84:35800 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@b20256f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.766 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x20e3fa9d, L:/10.110.144.84:35808 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3876d515[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.766 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb3821264, L:/10.110.144.84:33254 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5ee62134[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.766 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x47d47e68, L:/10.110.144.84:35798 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@14547b13[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.766 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb42331de, L:/10.110.144.84:39348 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4bcacf33[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.766 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc6190f33, L:/10.110.144.84:33266 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@120ca61d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.766 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb72196e7, L:/10.110.144.84:33240 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@25a28148[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.766 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x43ebc634, L:/10.110.144.84:33238 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6ac8b4ea[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.864 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0xa3ac92f2, L:/10.110.144.84:35822 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.864 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0x61ded287, L:/10.110.144.84:33274 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.864 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xfdf2b385, L:/10.110.144.84:35826 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.864 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0xceaa12b2, L:/10.110.144.84:39350 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.864 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0x777278fa, L:/10.110.144.84:33276 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.864 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x0a434e8d, L:/10.110.144.84:33280 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.864 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x7c01048b, L:/10.110.144.84:39360 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.865 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfdf2b385, L:/10.110.144.84:35826 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@199645ff[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.865 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa3ac92f2, L:/10.110.144.84:35822 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6eb717e2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.865 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xceaa12b2, L:/10.110.144.84:39350 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@64333384[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.865 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7c01048b, L:/10.110.144.84:39360 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7ee74665[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.865 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0a434e8d, L:/10.110.144.84:33280 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@49ad09b3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.865 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x61ded287, L:/10.110.144.84:33274 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@723cb0d3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.865 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x777278fa, L:/10.110.144.84:33276 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5b394a7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.964 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x021bf5fb, L:/10.110.144.84:33296 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.964 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x8b1e8d4c, L:/10.110.144.84:35870 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.964 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x5f05c767, L:/10.110.144.84:33310 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.964 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0xc6502ddc, L:/10.110.144.84:35856 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.964 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x92aa7e20, L:/10.110.144.84:39382 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.964 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0xe4e96074, L:/10.110.144.84:35834 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.964 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xf69d70d6, L:/10.110.144.84:39370 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.964 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x1c131125, L:/10.110.144.84:39374 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:50.964 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0xbf095d83, L:/10.110.144.84:33308 - R:10.110.141.243/10.110.141.243:6379] message: *1
$4
PING

2023-05-26 09:01:50.965 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x4f39f6a3, L:/10.110.144.84:35846 - R:10.110.156.54/10.110.156.54:6379] message: *1
$4
PING

2023-05-26 09:01:50.965 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf69d70d6, L:/10.110.144.84:39370 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4d6610f8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.965 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc6502ddc, L:/10.110.144.84:35856 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5f19f06e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.965 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe4e96074, L:/10.110.144.84:35834 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2af65348[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.965 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x92aa7e20, L:/10.110.144.84:39382 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2aa67966[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.965 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8b1e8d4c, L:/10.110.144.84:35870 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@43658363[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.965 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x021bf5fb, L:/10.110.144.84:33296 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@379a5e1d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.965 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5f05c767, L:/10.110.144.84:33310 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7e7a7782[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.965 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x4f39f6a3, L:/10.110.144.84:35846 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@a8fc109[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.965 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbf095d83, L:/10.110.144.84:33308 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@70a5616a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:50.965 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1c131125, L:/10.110.144.84:39374 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@61c79de0[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:51.064 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x12375623, L:/10.110.144.84:39396 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:51.064 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0xfce210a1, L:/10.110.144.84:39384 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:51.065 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfce210a1, L:/10.110.144.84:39384 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@17f9493e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:51.065 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x12375623, L:/10.110.144.84:39396 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@65382e41[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:51.165 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x6f224b76, L:/10.110.144.84:39416 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:51.165 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x5bc4a8da, L:/10.110.144.84:39402 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:51.165 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0xc32c3509, L:/10.110.144.84:39406 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:51.165 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc32c3509, L:/10.110.144.84:39406 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@154445db[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:51.165 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5bc4a8da, L:/10.110.144.84:39402 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5c2864f1[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:51.165 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6f224b76, L:/10.110.144.84:39416 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2d978c56[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:51.265 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x8259c1ae, L:/10.110.144.84:39428 - R:10.110.144.247/10.110.144.247:6379] message: *1
$4
PING

2023-05-26 09:01:51.265 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8259c1ae, L:/10.110.144.84:39428 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@f0aa319[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:51.716 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:51.716 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062911361 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062910000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062910349 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062907000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062905000 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062907000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062908000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062908339 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062907329 6 connected 5462-10922

, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@28834e32[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:51.717 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.229/10.110.154.229:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062911361 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062910000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062910349 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062907000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062905000 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062907000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062908000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062908339 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062907329 6 connected 5462-10922

2023-05-26 09:01:52.723 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:52.724 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062911602 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062908000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062910000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062911000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062909000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062907000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062908576 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062910592 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062912610 5 connected

, channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@499a641c[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:52.724 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.144.247/10.110.144.247:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062911602 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062908000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062910000 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062911000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062909000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062907000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062908576 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062910592 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062912610 5 connected

2023-05-26 09:01:53.664 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x0dea50d8, L:/10.110.144.84:45776 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:01:53.664 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0xf71f7ab7, L:/10.110.144.84:35790 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.664 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0xa24502b7, L:/10.110.144.84:35746 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.664 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x4805720c, L:/10.110.144.84:35748 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.664 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0x284d5b96, L:/10.110.144.84:35796 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.664 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xf92c01fe, L:/10.110.144.84:35786 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.664 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0x8c2ea06a, L:/10.110.144.84:35804 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.664 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x0db36da8, L:/10.110.144.84:35774 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.665 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0dea50d8, L:/10.110.144.84:45776 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@358a8fbe[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.665 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf71f7ab7, L:/10.110.144.84:35790 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1b95dfa5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.665 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa24502b7, L:/10.110.144.84:35746 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@266e515c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.665 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf92c01fe, L:/10.110.144.84:35786 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6b4202be[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.665 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8c2ea06a, L:/10.110.144.84:35804 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2a169a04[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.665 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0db36da8, L:/10.110.144.84:35774 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6210564f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.665 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0x4805720c, L:/10.110.144.84:35748 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@52107f2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.665 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x284d5b96, L:/10.110.144.84:35796 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@10c56fff[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.730 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:53.731 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062909311 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062909000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062909000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062911000 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062911330 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062913350 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062912000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062912339 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062912000 5 connected

, channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6e266c8e[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:53.731 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.142.16/10.110.142.16:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062909311 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062909000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062909000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062911000 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062911330 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062913350 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062912000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062912339 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062912000 5 connected

2023-05-26 09:01:53.764 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x5eb61016, L:/10.110.144.84:35816 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.764 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0xf49776af, L:/10.110.144.84:35860 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.764 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0xe0e620cc, L:/10.110.144.84:35904 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.765 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0xd13e7b1a, L:/10.110.144.84:35856 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.765 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x3c540846, L:/10.110.144.84:35878 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.765 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x6e4fed1f, L:/10.110.144.84:35882 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.764 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0xb240c4b0, L:/10.110.144.84:35812 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.765 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0x8571b081, L:/10.110.144.84:35906 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.765 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0xc983ece0, L:/10.110.144.84:35848 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.765 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0xcba3a34d, L:/10.110.144.84:35888 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.765 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0x7f0f4086, L:/10.110.144.84:35868 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.764 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xca067ab9, L:/10.110.144.84:35832 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.765 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xb00ac60f, L:/10.110.144.84:35918 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.765 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8571b081, L:/10.110.144.84:35906 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3709af3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.765 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5eb61016, L:/10.110.144.84:35816 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3f45c969[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.765 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc983ece0, L:/10.110.144.84:35848 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5a7dfa31[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.765 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7f0f4086, L:/10.110.144.84:35868 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5307ccab[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.765 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe0e620cc, L:/10.110.144.84:35904 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6c5d61c5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.766 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xca067ab9, L:/10.110.144.84:35832 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7231fee9[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.766 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb00ac60f, L:/10.110.144.84:35918 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7b8c5cf9[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.766 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xcba3a34d, L:/10.110.144.84:35888 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@502fa1c4[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.765 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd13e7b1a, L:/10.110.144.84:35856 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@549c8bff[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.765 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb240c4b0, L:/10.110.144.84:35812 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@770f64b4[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.765 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3c540846, L:/10.110.144.84:35878 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@de1b90f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.765 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf49776af, L:/10.110.144.84:35860 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6f2c2b74[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.765 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6e4fed1f, L:/10.110.144.84:35882 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@39c036c5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.864 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0xef134f04, L:/10.110.144.84:35924 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.865 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0xe485a439, L:/10.110.144.84:35968 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.865 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x37175fd6, L:/10.110.144.84:35982 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.865 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x6e7a6e1c, L:/10.110.144.84:35992 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.865 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0xcdce0c35, L:/10.110.144.84:35996 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.865 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0xfbdec62b, L:/10.110.144.84:35926 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.865 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0xf1dc725c, L:/10.110.144.84:35928 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.864 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x3a921395, L:/10.110.144.84:35922 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.865 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x57c3f14e, L:/10.110.144.84:35940 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.865 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0x0cc3914c, L:/10.110.144.84:35956 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.865 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x13bb21f2, L:/10.110.144.84:36004 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.865 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x55d70ed4, L:/10.110.144.84:35976 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.865 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xcbb73c76, L:/10.110.144.84:35990 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:01:53.865 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xef134f04, L:/10.110.144.84:35924 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@12e8436f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.865 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x37175fd6, L:/10.110.144.84:35982 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3d9feb9f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.866 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xcdce0c35, L:/10.110.144.84:35996 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4599cb8a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.866 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf1dc725c, L:/10.110.144.84:35928 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@60af746c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.866 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6e7a6e1c, L:/10.110.144.84:35992 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@200d83a7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.866 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0cc3914c, L:/10.110.144.84:35956 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@32a2fab3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.866 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3a921395, L:/10.110.144.84:35922 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6c5ebe84[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.866 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfbdec62b, L:/10.110.144.84:35926 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@542723b4[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.866 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe485a439, L:/10.110.144.84:35968 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@628699fd[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.866 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x13bb21f2, L:/10.110.144.84:36004 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@34f8c73f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.866 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x55d70ed4, L:/10.110.144.84:35976 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@213002ce[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.866 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xcbb73c76, L:/10.110.144.84:35990 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@49fa7ec9[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:53.866 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x57c3f14e, L:/10.110.144.84:35940 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@903cf79[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:54.737 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:54.738 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062913000 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062909000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062912000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062914357 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062911330 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062914000 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062912000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062912339 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062912000 5 connected

, channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@13ba5062[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:54.738 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.142.16/10.110.142.16:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062913000 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062909000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062912000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062914357 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062911330 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062914000 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062912000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062912339 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062912000 5 connected

2023-05-26 09:01:54.765 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:01:54.766 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@14108d42[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:54.964 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x473a3b68, L:/10.110.144.84:52796 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:54.964 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0x52637df4, L:/10.110.144.84:52860 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:54.964 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xab19d647, L:/10.110.144.84:52810 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:54.964 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x8c1d1d08, L:/10.110.144.84:52846 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:54.964 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0x326dadc1, L:/10.110.144.84:52868 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:54.964 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x79b442af, L:/10.110.144.84:52834 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:54.965 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xb424d7c0, L:/10.110.144.84:52822 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:54.965 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0x1855534a, L:/10.110.144.84:52876 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:54.965 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x754f25dd, L:/10.110.144.84:52884 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:54.964 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x84160c2f, L:/10.110.144.84:52794 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:54.965 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0x473a3b68, L:/10.110.144.84:52796 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@326705c7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:54.965 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb424d7c0, L:/10.110.144.84:52822 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@58e5de85[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:54.965 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x754f25dd, L:/10.110.144.84:52884 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@413512ea[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:54.965 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x326dadc1, L:/10.110.144.84:52868 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@73380a7a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:54.965 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8c1d1d08, L:/10.110.144.84:52846 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4fe21979[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:54.965 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x52637df4, L:/10.110.144.84:52860 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@48e936ff[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:54.966 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xab19d647, L:/10.110.144.84:52810 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@52dd12d2[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:54.965 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1855534a, L:/10.110.144.84:52876 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@755cf0e0[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:54.965 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x79b442af, L:/10.110.144.84:52834 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4a1e7b3a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:54.965 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x84160c2f, L:/10.110.144.84:52794 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@44f27d0a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.065 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0xae1fe143, L:/10.110.144.84:52890 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.065 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0x680d9bfe, L:/10.110.144.84:53044 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.065 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0xef0f174d, L:/10.110.144.84:53012 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.065 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x20a56afe, L:/10.110.144.84:53020 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.065 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xb97ba58c, L:/10.110.144.84:52998 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.065 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x993c18f9, L:/10.110.144.84:52912 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.065 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0xbbace342, L:/10.110.144.84:52900 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.065 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0xae3e7c1c, L:/10.110.144.84:52926 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.065 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0x7ed2fc63, L:/10.110.144.84:52946 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.066 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x20a56afe, L:/10.110.144.84:53020 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@62eea0c0[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.065 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x3f3beb36, L:/10.110.144.84:52974 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.066 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbbace342, L:/10.110.144.84:52900 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@79195b6e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.066 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xef0f174d, L:/10.110.144.84:53012 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@f9c9189[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.065 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0x33a028d2, L:/10.110.144.84:53036 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.066 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3f3beb36, L:/10.110.144.84:52974 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2bed86e9[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.066 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xae1fe143, L:/10.110.144.84:52890 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3da272f3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.066 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x33a028d2, L:/10.110.144.84:53036 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@44e5f35b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.065 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xc1cd3ec0, L:/10.110.144.84:52984 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.065 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0xf9c27ef8, L:/10.110.144.84:53024 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.065 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0x6f191eba, L:/10.110.144.84:52936 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.065 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x20089fa0, L:/10.110.144.84:52958 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.065 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0xa71b78cc, L:/10.110.144.84:53048 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.066 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xae3e7c1c, L:/10.110.144.84:52926 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2d6da23e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.066 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7ed2fc63, L:/10.110.144.84:52946 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5c17e426[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.065 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x680d9bfe, L:/10.110.144.84:53044 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@41689622[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.066 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb97ba58c, L:/10.110.144.84:52998 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@c09d19e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.066 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x993c18f9, L:/10.110.144.84:52912 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@40bdc7a8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.067 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc1cd3ec0, L:/10.110.144.84:52984 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3f52feb6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.067 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x20089fa0, L:/10.110.144.84:52958 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@17e8ff12[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.067 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf9c27ef8, L:/10.110.144.84:53024 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@f480fb8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.067 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa71b78cc, L:/10.110.144.84:53048 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7575280b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.067 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6f191eba, L:/10.110.144.84:52936 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1930e8a5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.164 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0xdd865026, L:/10.110.144.84:53062 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.164 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xa793ea30, L:/10.110.144.84:53094 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.164 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0x7536079f, L:/10.110.144.84:53104 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.164 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x776d0d72, L:/10.110.144.84:53086 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.164 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc5c90da, L:/10.110.144.84:53064 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.165 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa793ea30, L:/10.110.144.84:53094 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5710562[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.165 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x9cf931d9, L:/10.110.144.84:53074 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.165 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7536079f, L:/10.110.144.84:53104 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1cee0606[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.165 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x08223bc3, L:/10.110.144.84:53114 - R:10.110.144.233/10.110.144.233:6379] message: *1
$4
PING

2023-05-26 09:01:55.165 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x776d0d72, L:/10.110.144.84:53086 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3388f205[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.166 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xcc5c90da, L:/10.110.144.84:53064 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@248eb61f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.167 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9cf931d9, L:/10.110.144.84:53074 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@288597a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.167 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x08223bc3, L:/10.110.144.84:53114 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@271b4d63[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.176 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xdd865026, L:/10.110.144.84:53062 - R:10.110.144.233/10.110.144.233:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@41faac8c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.364 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0xf7333ec8, L:/10.110.144.84:33492 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.364 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0xbf9413ee, L:/10.110.144.84:33514 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.365 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x62eed904, L:/10.110.144.84:33600 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.364 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x47df7172, L:/10.110.144.84:33548 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.364 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0xd866eba9, L:/10.110.144.84:33490 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.365 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xee749cfc, L:/10.110.144.84:33510 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.365 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0xae79d629, L:/10.110.144.84:33586 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.364 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x836e5eb7, L:/10.110.144.84:33508 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.365 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0xdcf17e87, L:/10.110.144.84:33518 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.365 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x67ece0fa, L:/10.110.144.84:33534 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.365 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0x411cd3c8, L:/10.110.144.84:33532 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.365 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0x4c364542, L:/10.110.144.84:33578 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.365 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xa79c2a70, L:/10.110.144.84:33564 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.365 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xee749cfc, L:/10.110.144.84:33510 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3a443b43[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.365 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x67ece0fa, L:/10.110.144.84:33534 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@199f5153[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.365 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x62eed904, L:/10.110.144.84:33600 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@25947f6b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.365 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x411cd3c8, L:/10.110.144.84:33532 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3a56ce30[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.365 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xae79d629, L:/10.110.144.84:33586 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@61c1d3c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.366 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd866eba9, L:/10.110.144.84:33490 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@10dd429d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.366 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0xf7333ec8, L:/10.110.144.84:33492 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@25ee8ca5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.366 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xdcf17e87, L:/10.110.144.84:33518 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7afb89db[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.366 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x4c364542, L:/10.110.144.84:33578 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2977cbd8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.365 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x47df7172, L:/10.110.144.84:33548 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@35f800b0[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.365 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbf9413ee, L:/10.110.144.84:33514 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4028b9f7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.365 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x836e5eb7, L:/10.110.144.84:33508 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@d9024b8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.366 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa79c2a70, L:/10.110.144.84:33564 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@78ca7593[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.465 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xf9c20448, L:/10.110.144.84:33614 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.465 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0x0b9d797f, L:/10.110.144.84:33650 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.465 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xa3107227, L:/10.110.144.84:33712 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.465 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0x482a4a0b, L:/10.110.144.84:33682 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.465 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0xac8a284b, L:/10.110.144.84:33664 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.465 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0x3ee3cfdf, L:/10.110.144.84:33668 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.465 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x2c342c4e, L:/10.110.144.84:33642 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.465 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0x0130460e, L:/10.110.144.84:33724 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.465 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0x1117a381, L:/10.110.144.84:33678 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.465 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x3a0f05aa, L:/10.110.144.84:33622 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.465 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x31f2bd4c, L:/10.110.144.84:33630 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.465 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x6ee392be, L:/10.110.144.84:33698 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.465 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x1ae96261, L:/10.110.144.84:33686 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.465 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x482a4a0b, L:/10.110.144.84:33682 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5781704d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.465 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x8ec81a61, L:/10.110.144.84:33672 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.466 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3ee3cfdf, L:/10.110.144.84:33668 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2336c366[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.466 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0130460e, L:/10.110.144.84:33724 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7f68e67a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.466 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x31f2bd4c, L:/10.110.144.84:33630 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3752f8a1[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.466 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf9c20448, L:/10.110.144.84:33614 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2544c3a3[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.466 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2c342c4e, L:/10.110.144.84:33642 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@197942d7[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.466 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa3107227, L:/10.110.144.84:33712 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5d186f5b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.466 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0b9d797f, L:/10.110.144.84:33650 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@22bea1e5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.466 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1117a381, L:/10.110.144.84:33678 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2a585ed0[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.466 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8ec81a61, L:/10.110.144.84:33672 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@591b85e8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.466 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1ae96261, L:/10.110.144.84:33686 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@37b1454f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.466 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xac8a284b, L:/10.110.144.84:33664 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5128ee28[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.466 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6ee392be, L:/10.110.144.84:33698 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@75c43863[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.466 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3a0f05aa, L:/10.110.144.84:33622 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1c6337c0[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.566 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x637bc211, L:/10.110.144.84:33740 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.566 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x7712ad85, L:/10.110.144.84:33728 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.566 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xa3f22cac, L:/10.110.144.84:33754 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.566 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x3d448dc2, L:/10.110.144.84:33780 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.566 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xe03909da, L:/10.110.144.84:33770 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.567 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7712ad85, L:/10.110.144.84:33728 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@51512ad8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.567 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3d448dc2, L:/10.110.144.84:33780 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3c1cb05a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.567 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x637bc211, L:/10.110.144.84:33740 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6795ab55[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.567 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa3f22cac, L:/10.110.144.84:33754 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@31f4b2dc[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.566 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x4be50e97, L:/10.110.144.84:33788 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:55.567 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe03909da, L:/10.110.144.84:33770 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@43bd3245[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.568 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x4be50e97, L:/10.110.144.84:33788 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@468fb950[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:55.747 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:55.748 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062913000 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062914387 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062911000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062912000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062913000 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062912000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062915397 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062913379 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062914893 6 connected 5462-10922

, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5bd932c9[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:55.748 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.229/10.110.154.229:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062913000 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062914387 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062911000 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062912000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062913000 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062912000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062915397 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062913379 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062914893 6 connected 5462-10922

2023-05-26 09:01:56.760 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x0dea50d8, L:/10.110.144.84:45776 - R:10.110.154.77/10.110.154.77:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:56.760 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: $1894
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062915144 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062914000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062913000 5 connected 0-5461
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062914000 6 connected 5462-10922
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062914000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062916153 4 connected 10923-16383
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062915000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062914135 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062913634 6 connected

, channel: [id: 0x0dea50d8, L:/10.110.144.84:45776 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6232518a[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:56.761 DEBUG 1 --- [sson-netty-3-28] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.77/10.110.154.77:6379:
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062915144 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062914000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062913000 5 connected 0-5461
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062914000 6 connected 5462-10922
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062914000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062916153 4 connected 10923-16383
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062915000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062914135 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062913634 6 connected

2023-05-26 09:01:56.864 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379] message: *1
$4
PING

2023-05-26 09:01:56.865 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@70f74b1a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:01:57.766 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:57.767 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062916905 6 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062915000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062914000 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062914888 5 connected 0-5461
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062915000 4 connected 10923-16383
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062914000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062915898 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062914000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062913879 4 connected

, channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@51a46903[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:57.767 DEBUG 1 --- [sson-netty-3-15] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.156.54/10.110.156.54:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062916905 6 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062915000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062914000 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062914888 5 connected 0-5461
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062915000 4 connected 10923-16383
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062914000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062915898 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062914000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062913879 4 connected

2023-05-26 09:01:58.773 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:58.774 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: $1894
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062916000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062918137 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062917000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062916118 4 connected 10923-16383
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062917000 5 connected 0-5461
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062917000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062916000 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062917000 5 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062917129 6 connected

, channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@51363426[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:58.774 DEBUG 1 --- [sson-netty-3-22] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.136.174/10.110.136.174:6379:
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062916000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062918137 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062917000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062916118 4 connected 10923-16383
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062917000 5 connected 0-5461
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062917000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062916000 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062917000 5 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062917129 6 connected

2023-05-26 09:01:59.551  INFO 1 --- [io-63000-exec-9] c.x.a.r.c.IndexWriterController          : IndexWriterController ping
2023-05-26 09:01:59.779 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:01:59.780 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062916025 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062918045 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062917000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062919052 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062914000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062917036 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062917000 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062914000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062915012 6 connected

, channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@549fab65[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:01:59.780 DEBUG 1 --- [sson-netty-3-14] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.141.243/10.110.141.243:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062916025 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062918045 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062917000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062919052 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062914000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062917036 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062917000 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062914000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062915012 6 connected

2023-05-26 09:02:00.064 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:00.066 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@79d352a0[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:00.787 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:00.788 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062919000 6 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062917000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062916000 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062918000 5 connected 0-5461
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062918000 4 connected 10923-16383
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062919931 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062917000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062919000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062918000 4 connected

, channel: [id: 0xc66575c6, L:/10.110.144.84:35572 - R:10.110.156.54/10.110.156.54:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3ace8549[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:00.788 DEBUG 1 --- [sson-netty-3-15] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.156.54/10.110.156.54:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062919000 6 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062917000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062916000 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062918000 5 connected 0-5461
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062918000 4 connected 10923-16383
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062919931 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062917000 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062919000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062918000 4 connected

2023-05-26 09:02:01.793 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x0dea50d8, L:/10.110.144.84:45776 - R:10.110.154.77/10.110.154.77:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:01.794 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: $1894
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062921219 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062914000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062918175 5 connected 0-5461
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062918000 6 connected 5462-10922
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062920209 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062920000 4 connected 10923-16383
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062919185 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062921723 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062919000 6 connected

, channel: [id: 0x0dea50d8, L:/10.110.144.84:45776 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1448156[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:01.794 DEBUG 1 --- [sson-netty-3-28] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.77/10.110.154.77:6379:
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062921219 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062914000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062918175 5 connected 0-5461
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062918000 6 connected 5462-10922
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062920209 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062920000 4 connected 10923-16383
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062919185 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062921723 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062919000 6 connected

2023-05-26 09:02:02.800 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:02.803 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062916000 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062921000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062921423 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062919405 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062920414 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062922434 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062919000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062918000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062919000 5 connected

, channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@382b34b8[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:02.803 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.142.16/10.110.142.16:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062916000 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062921000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062921423 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062919405 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062920414 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062922434 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062919000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062918000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062919000 5 connected

2023-05-26 09:02:03.809 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:03.810 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062923543 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062921000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062922000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062919405 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062920414 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062922434 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062919000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062918000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062923443 5 connected

, channel: [id: 0xcc8baceb, L:/10.110.144.84:43076 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@262f9330[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:03.811 DEBUG 1 --- [isson-netty-3-3] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.142.16/10.110.142.16:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062923543 4 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062921000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062922000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062919405 6 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062920414 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062922434 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062919000 6 connected 5462-10922
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062918000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062923443 5 connected

2023-05-26 09:02:04.816 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x0dea50d8, L:/10.110.144.84:45776 - R:10.110.154.77/10.110.154.77:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:04.817 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: $1894
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062922000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062919000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062923239 5 connected 0-5461
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062922225 6 connected 5462-10922
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062922000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062923000 4 connected 10923-16383
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062921000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062923000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062924250 6 connected

, channel: [id: 0x0dea50d8, L:/10.110.144.84:45776 - R:10.110.154.77/10.110.154.77:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@12840f58[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:04.817 DEBUG 1 --- [sson-netty-3-28] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.77/10.110.154.77:6379:
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062922000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062919000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062923239 5 connected 0-5461
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062922225 6 connected 5462-10922
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062922000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062923000 4 connected 10923-16383
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062921000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062923000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062924250 6 connected

2023-05-26 09:02:05.823 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:05.824 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062923000 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062922708 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062924727 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062923718 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062925736 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062920000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062924000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062923000 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062925000 5 connected

, channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@135359a9[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:05.825 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.144.247/10.110.144.247:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062923000 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062922708 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062924727 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062923718 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062925736 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062920000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062924000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062923000 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062925000 5 connected

2023-05-26 09:02:06.851 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:06.852 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: $1894
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062926130 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062925122 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062921000 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062924115 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062923000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062922000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062923000 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062924000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062924000 6 connected

, channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3b13ceca[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:06.852 DEBUG 1 --- [isson-netty-3-6] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.129.61/10.110.129.61:6379:
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062926130 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062925122 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062921000 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062924115 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062923000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062922000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062923000 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062924000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062924000 6 connected

2023-05-26 09:02:07.164 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xacf35917, L:/10.110.144.84:52652 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.164 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x092211ef, L:/10.110.144.84:52700 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.164 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x70380bd3, L:/10.110.144.84:52666 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.164 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.164 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x340eb3de, L:/10.110.144.84:52654 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.164 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x29287aa4, L:/10.110.144.84:52674 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.164 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0xf4fa2716, L:/10.110.144.84:52690 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.165 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0xacf35917, L:/10.110.144.84:52652 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@27e869ba[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.165 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@32419d78[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.165 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x092211ef, L:/10.110.144.84:52700 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@25533cfa[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.165 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x29287aa4, L:/10.110.144.84:52674 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@54466e1d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.165 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x340eb3de, L:/10.110.144.84:52654 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@19568a5f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.165 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf4fa2716, L:/10.110.144.84:52690 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6744c0ba[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.165 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x70380bd3, L:/10.110.144.84:52666 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2f9538ac[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x9af51b9b, L:/10.110.144.84:52714 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0xef8d5a6b, L:/10.110.144.84:52762 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.265 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0xf2f7a384, L:/10.110.144.84:52798 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x523b6e77, L:/10.110.144.84:52768 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0xd60af23b, L:/10.110.144.84:52718 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.265 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x6843b4fb, L:/10.110.144.84:52808 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0xb71e8021, L:/10.110.144.84:52812 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x36af954f, L:/10.110.144.84:52716 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.265 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0xd56d05e3, L:/10.110.144.84:52784 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x0580830a, L:/10.110.144.84:52772 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0x9b21c02e, L:/10.110.144.84:52734 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9af51b9b, L:/10.110.144.84:52714 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@47bcc46c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0x5d9d8a2f, L:/10.110.144.84:52748 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xef8d5a6b, L:/10.110.144.84:52762 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6e9968b8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x36af954f, L:/10.110.144.84:52716 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@8f59b5b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0xb7d08619, L:/10.110.144.84:52758 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.265 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6843b4fb, L:/10.110.144.84:52808 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5a3b7dc[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0580830a, L:/10.110.144.84:52772 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@73b122e9[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x523b6e77, L:/10.110.144.84:52768 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2954b7ab[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0xd9718309, L:/10.110.144.84:52824 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5d9d8a2f, L:/10.110.144.84:52748 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@8bed10c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.266 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb7d08619, L:/10.110.144.84:52758 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@377d1f2f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.265 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x0aec2d61, L:/10.110.144.84:52792 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.265 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd56d05e3, L:/10.110.144.84:52784 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@50c75d1f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.266 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9b21c02e, L:/10.110.144.84:52734 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1c9a551[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.266 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf2f7a384, L:/10.110.144.84:52798 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1b183430[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.265 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd60af23b, L:/10.110.144.84:52718 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2a312a03[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.266 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xd9718309, L:/10.110.144.84:52824 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@13569cfd[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.266 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb71e8021, L:/10.110.144.84:52812 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@64a607a5[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.266 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x0aec2d61, L:/10.110.144.84:52792 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2ea4a325[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.365 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xa6ccd892, L:/10.110.144.84:52828 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.365 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x29144e0e, L:/10.110.144.84:52906 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.365 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0x564f0265, L:/10.110.144.84:52872 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.365 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0xf931d36e, L:/10.110.144.84:52832 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.365 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x564f0265, L:/10.110.144.84:52872 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4f932e56[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.367 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0x6009cc6c, L:/10.110.144.84:52838 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.367 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x29144e0e, L:/10.110.144.84:52906 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@879c974[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.367 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa6ccd892, L:/10.110.144.84:52828 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@996f51f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.367 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf931d36e, L:/10.110.144.84:52832 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7a68515a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.367 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x7d159085, L:/10.110.144.84:52886 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.365 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x3380aecd, L:/10.110.144.84:52826 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.365 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0xbf65c213, L:/10.110.144.84:52854 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.365 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0x28e06be0, L:/10.110.144.84:52860 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.365 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x7dd7e63c, L:/10.110.144.84:52892 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.367 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7d159085, L:/10.110.144.84:52886 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2e5482a8[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.367 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x60abf31c, L:/10.110.144.84:52922 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.367 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xbf65c213, L:/10.110.144.84:52854 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@783eac6e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.367 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x28e06be0, L:/10.110.144.84:52860 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@16cbf31e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.365 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0xe1e6bd8f, L:/10.110.144.84:52924 - R:10.110.154.229/10.110.154.229:6379] message: *1
$4
PING

2023-05-26 09:02:07.367 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7dd7e63c, L:/10.110.144.84:52892 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7ad9db0d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.367 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x60abf31c, L:/10.110.144.84:52922 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@aabe224[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.367 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6009cc6c, L:/10.110.144.84:52838 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@227f8523[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.368 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe1e6bd8f, L:/10.110.144.84:52924 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1b58661c[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.367 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3380aecd, L:/10.110.144.84:52826 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@cbe7fb6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:07.857 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:07.858 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: $1894
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062926130 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062925122 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062927141 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062925000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062926000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062923000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062924000 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062924000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062925000 6 connected

, channel: [id: 0xa228ac59, L:/10.110.144.84:36896 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@79a9e115[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:07.858 DEBUG 1 --- [isson-netty-3-6] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.129.61/10.110.129.61:6379:
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062926130 4 connected 10923-16383
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062925122 5 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062927141 6 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062925000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062926000 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062923000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062924000 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062924000 4 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062925000 6 connected

2023-05-26 09:02:08.874 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:08.875 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062928000 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062925000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062928764 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062927754 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062926000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062923000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062926000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062923000 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062926000 5 connected

, channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4deb28f5[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:08.876 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.144.247/10.110.144.247:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062928000 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062925000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062928764 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062927754 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062926000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062923000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062926000 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062923000 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062926000 5 connected

2023-05-26 09:02:08.879 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0xa24502b7, L:/10.110.144.84:35746 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.879 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x0db36da8, L:/10.110.144.84:35774 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0x7f0f4086, L:/10.110.144.84:35868 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0x284d5b96, L:/10.110.144.84:35796 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0xd13e7b1a, L:/10.110.144.84:35856 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0xcba3a34d, L:/10.110.144.84:35888 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xcbb73c76, L:/10.110.144.84:35990 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.879 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xf92c01fe, L:/10.110.144.84:35786 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xb00ac60f, L:/10.110.144.84:35918 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x13bb21f2, L:/10.110.144.84:36004 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880  INFO 1 --- [isson-netty-3-4] o.r.cluster.ClusterConnectionManager     : slave rediss://10.110.142.16:6379 removed for slot ranges: [[5462-10922]]
2023-05-26 09:02:08.880 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x4805720c, L:/10.110.144.84:35748 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0xf71f7ab7, L:/10.110.144.84:35790 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x6e4fed1f, L:/10.110.144.84:35882 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x5eb61016, L:/10.110.144.84:35816 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.881 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xb00ac60f, L:/10.110.144.84:35918 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@422375ea[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.881 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0xcdce0c35, L:/10.110.144.84:35996 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.881 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandPubSubDecoder  : reply: +OK
, channel: [id: 0x4805720c, L:/10.110.144.84:35748 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2d50a270[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.881 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xf92c01fe, L:/10.110.144.84:35786 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@e59fe85[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.880 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0xef134f04, L:/10.110.144.84:35924 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0x8c2ea06a, L:/10.110.144.84:35804 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.881 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x284d5b96, L:/10.110.144.84:35796 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@46e3aed9[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.881 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0xfbdec62b, L:/10.110.144.84:35926 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0xb240c4b0, L:/10.110.144.84:35812 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.881 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x3a921395, L:/10.110.144.84:35922 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.881 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0xf1dc725c, L:/10.110.144.84:35928 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0xc983ece0, L:/10.110.144.84:35848 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.881 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0xe485a439, L:/10.110.144.84:35968 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0x8571b081, L:/10.110.144.84:35906 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xca067ab9, L:/10.110.144.84:35832 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.882 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0x0cc3914c, L:/10.110.144.84:35956 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.882 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x6e4fed1f, L:/10.110.144.84:35882 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4c22ef7[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.882 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x8571b081, L:/10.110.144.84:35906 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6efe6649[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.882 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x8c2ea06a, L:/10.110.144.84:35804 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4f481dd3[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.882 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x7f0f4086, L:/10.110.144.84:35868 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@14ee347c[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.882 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xcdce0c35, L:/10.110.144.84:35996 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@226890f9[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.882 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xc983ece0, L:/10.110.144.84:35848 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4dfe8688[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.882 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xfbdec62b, L:/10.110.144.84:35926 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@52e67780[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.882 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xcbb73c76, L:/10.110.144.84:35990 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@63ba409e[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.882 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xe485a439, L:/10.110.144.84:35968 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@70bcd60[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.882 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xca067ab9, L:/10.110.144.84:35832 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@61a8138e[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.883 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xf1dc725c, L:/10.110.144.84:35928 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6a56c402[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.883 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x0cc3914c, L:/10.110.144.84:35956 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3483d4f1[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.883 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xb240c4b0, L:/10.110.144.84:35812 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@581ae8df[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.880 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0xe0e620cc, L:/10.110.144.84:35904 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x3c540846, L:/10.110.144.84:35878 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0xf49776af, L:/10.110.144.84:35860 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.883 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x6e7a6e1c, L:/10.110.144.84:35992 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.883 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xe0e620cc, L:/10.110.144.84:35904 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4c4a2bb2[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.883 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x37175fd6, L:/10.110.144.84:35982 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.880 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x55d70ed4, L:/10.110.144.84:35976 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.884 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xd13e7b1a, L:/10.110.144.84:35856 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@37e17c77[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.880 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x0db36da8, L:/10.110.144.84:35774 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@13d6a427[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.880 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xa24502b7, L:/10.110.144.84:35746 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2261b538[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.884 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xf49776af, L:/10.110.144.84:35860 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3f78dd6d[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.884 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xcba3a34d, L:/10.110.144.84:35888 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6ab60504[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.884 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x13bb21f2, L:/10.110.144.84:36004 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3ea73094[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.884 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x37175fd6, L:/10.110.144.84:35982 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3731664[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.881 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x57c3f14e, L:/10.110.144.84:35940 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
QUIT

2023-05-26 09:02:08.881 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xf71f7ab7, L:/10.110.144.84:35790 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5ffa72fd[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.884 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x5eb61016, L:/10.110.144.84:35816 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7fef2b00[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.885 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x3a921395, L:/10.110.144.84:35922 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7a0e153d[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.882 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xef134f04, L:/10.110.144.84:35924 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@18c65b49[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.884 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x3c540846, L:/10.110.144.84:35878 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@24b63c66[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.884 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x55d70ed4, L:/10.110.144.84:35976 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@71eae4f2[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.885 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x6e7a6e1c, L:/10.110.144.84:35992 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1f6d3a4[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:08.885 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x57c3f14e, L:/10.110.144.84:35940 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@32f9fbdf[Not completed, 2 dependents], command=(QUIT), params=[], codec=null]
2023-05-26 09:02:09.552  INFO 1 --- [o-63000-exec-10] c.x.a.r.c.IndexWriterController          : IndexWriterController ping
2023-05-26 09:02:09.884 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:09.884 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062928513 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062926000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062927501 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062926000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062926495 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062929521 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062928000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062924000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062928009 6 connected 5462-10922

, channel: [id: 0x693282dd, L:/10.110.144.84:39932 - R:10.110.154.229/10.110.154.229:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@69e04d50[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:09.885 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.154.229/10.110.154.229:6379:
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062928513 6 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062926000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062927501 4 connected 10923-16383
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062926000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062926495 5 connected 0-5461
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062929521 6 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062928000 5 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062924000 4 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062928009 6 connected 5462-10922

2023-05-26 09:02:09.888 DEBUG 1 --- [sson-netty-3-15] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:09.888 DEBUG 1 --- [sson-netty-3-26] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:09.898 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xb003e2be, L:/10.110.144.84:56300 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:09.898 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0xa080e84b, L:/10.110.144.84:56312 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:09.898 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xb003e2be, L:/10.110.144.84:56300 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:09.898 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xb003e2be, L:/10.110.144.84:56300 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.898 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandPubSubDecoder  : reply: +OK
, channel: [id: 0xa080e84b, L:/10.110.144.84:56312 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4cd9daea[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:09.898 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xb003e2be, L:/10.110.144.84:56300 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@48f545ca[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:09.898 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0xa080e84b, L:/10.110.144.84:56312 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:09.899 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xb003e2be, L:/10.110.144.84:56300 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@579e20a9[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:09.899 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb003e2be, L:/10.110.144.84:56300 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3757853d[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:09.899 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0xb003e2be, L:/10.110.144.84:56300 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.899 DEBUG 1 --- [sson-netty-3-16] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@1371153335 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0xb003e2be, L:/10.110.144.84:56300 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@5c457296[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:09.899 DEBUG 1 --- [sson-netty-3-17] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:09.899 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandPubSubDecoder  : reply: +OK
, channel: [id: 0xa080e84b, L:/10.110.144.84:56312 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5024169d[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:09.899 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb003e2be, L:/10.110.144.84:56300 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5c457296[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:09.899 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0xa080e84b, L:/10.110.144.84:56312 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.900 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0xa080e84b, L:/10.110.144.84:56312 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@43230658[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:09.900 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0xa080e84b, L:/10.110.144.84:56312 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.900 DEBUG 1 --- [sson-netty-3-18] o.r.connection.ClientConnectionsEntry    : new pubsub connection created: RedisPubSubConnection@738670746 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0xa080e84b, L:/10.110.144.84:56312 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@fc57e2b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:09.900  INFO 1 --- [sson-netty-3-18] o.r.c.pool.PubSubConnectionPool          : 1 connections initialized for 10.110.142.16/10.110.142.16:6379
2023-05-26 09:02:09.900 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0xa080e84b, L:/10.110.144.84:56312 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@fc57e2b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:09.905 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0xfc94cfdf, L:/10.110.144.84:56324 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:09.906 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0xfc94cfdf, L:/10.110.144.84:56324 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:09.906 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0xfc94cfdf, L:/10.110.144.84:56324 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.906 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xfc94cfdf, L:/10.110.144.84:56324 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6b4caea7[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:09.906 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xfc94cfdf, L:/10.110.144.84:56324 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5fdea84f[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:09.906 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfc94cfdf, L:/10.110.144.84:56324 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2d664806[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:09.906 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0xfc94cfdf, L:/10.110.144.84:56324 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.906 DEBUG 1 --- [sson-netty-3-19] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@1800418817 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0xfc94cfdf, L:/10.110.144.84:56324 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@4b706f20[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:09.907 DEBUG 1 --- [sson-netty-3-27] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:09.907 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xfc94cfdf, L:/10.110.144.84:56324 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4b706f20[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:09.913 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0x9373c0ee, L:/10.110.144.84:56334 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:09.914 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0x9373c0ee, L:/10.110.144.84:56334 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:09.914 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0x9373c0ee, L:/10.110.144.84:56334 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.914 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x9373c0ee, L:/10.110.144.84:56334 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4b4a33b1[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:09.914 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x9373c0ee, L:/10.110.144.84:56334 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@49a51bc3[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:09.914 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9373c0ee, L:/10.110.144.84:56334 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@9c32188[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:09.914 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0x9373c0ee, L:/10.110.144.84:56334 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.914 DEBUG 1 --- [sson-netty-3-28] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@1878231013 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x9373c0ee, L:/10.110.144.84:56334 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@26969f9f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:09.915 DEBUG 1 --- [sson-netty-3-29] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:09.915 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9373c0ee, L:/10.110.144.84:56334 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@26969f9f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:09.921 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0x1c5d13ed, L:/10.110.144.84:56342 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:09.921 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0x1c5d13ed, L:/10.110.144.84:56342 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:09.921 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0x1c5d13ed, L:/10.110.144.84:56342 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.922 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x1c5d13ed, L:/10.110.144.84:56342 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6f94edfb[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:09.922 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x1c5d13ed, L:/10.110.144.84:56342 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@36725979[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:09.922 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1c5d13ed, L:/10.110.144.84:56342 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2ea400dd[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:09.922 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0x1c5d13ed, L:/10.110.144.84:56342 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.922 DEBUG 1 --- [sson-netty-3-30] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@1235242379 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x1c5d13ed, L:/10.110.144.84:56342 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@7f30221b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:09.922 DEBUG 1 --- [sson-netty-3-31] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:09.922 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1c5d13ed, L:/10.110.144.84:56342 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7f30221b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:09.930 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0x28244e32, L:/10.110.144.84:56346 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:09.930 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0x28244e32, L:/10.110.144.84:56346 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:09.930 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0x28244e32, L:/10.110.144.84:56346 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.931 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x28244e32, L:/10.110.144.84:56346 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@40e1281e[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:09.931 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x28244e32, L:/10.110.144.84:56346 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3bb160c[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:09.931 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x28244e32, L:/10.110.144.84:56346 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2df07893[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:09.931 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0x28244e32, L:/10.110.144.84:56346 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.931 DEBUG 1 --- [sson-netty-3-32] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@772508804 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x28244e32, L:/10.110.144.84:56346 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@b5128c6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:09.931 DEBUG 1 --- [sson-netty-3-20] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:09.931 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x28244e32, L:/10.110.144.84:56346 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@b5128c6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:09.939 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0xb83de612, L:/10.110.144.84:56348 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:09.939 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0xb83de612, L:/10.110.144.84:56348 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:09.940 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0xb83de612, L:/10.110.144.84:56348 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.940 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xb83de612, L:/10.110.144.84:56348 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7aed428a[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:09.940 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xb83de612, L:/10.110.144.84:56348 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@93ef892[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:09.940 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb83de612, L:/10.110.144.84:56348 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2503d1f[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:09.940 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0xb83de612, L:/10.110.144.84:56348 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.940 DEBUG 1 --- [sson-netty-3-21] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@805029588 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0xb83de612, L:/10.110.144.84:56348 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@3b578488[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:09.941 DEBUG 1 --- [sson-netty-3-22] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:09.941 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xb83de612, L:/10.110.144.84:56348 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3b578488[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:09.948 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x643b7f6a, L:/10.110.144.84:56362 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:09.948 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x643b7f6a, L:/10.110.144.84:56362 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:09.948 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x643b7f6a, L:/10.110.144.84:56362 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.948 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x643b7f6a, L:/10.110.144.84:56362 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@59f5aaa7[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:09.949 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x643b7f6a, L:/10.110.144.84:56362 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@d7da243[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:09.949 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x643b7f6a, L:/10.110.144.84:56362 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@75a0094a[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:09.949 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x643b7f6a, L:/10.110.144.84:56362 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.949 DEBUG 1 --- [isson-netty-3-1] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@179128214 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x643b7f6a, L:/10.110.144.84:56362 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@5105af9e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:09.949 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x643b7f6a, L:/10.110.144.84:56362 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5105af9e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:09.949 DEBUG 1 --- [sson-netty-3-23] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:09.956 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x64e03b48, L:/10.110.144.84:56368 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:09.956 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x64e03b48, L:/10.110.144.84:56368 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:09.956 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x64e03b48, L:/10.110.144.84:56368 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.956 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x64e03b48, L:/10.110.144.84:56368 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5521d603[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:09.956 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x64e03b48, L:/10.110.144.84:56368 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@660ff3e7[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:09.956 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x64e03b48, L:/10.110.144.84:56368 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@56d404c8[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:09.956 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x64e03b48, L:/10.110.144.84:56368 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.957 DEBUG 1 --- [isson-netty-3-2] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@1946131897 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x64e03b48, L:/10.110.144.84:56368 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@6796294b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:09.957 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x64e03b48, L:/10.110.144.84:56368 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6796294b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:09.957 DEBUG 1 --- [isson-netty-3-3] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:09.964 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x8a0608fa, L:/10.110.144.84:56378 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:09.964 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x8a0608fa, L:/10.110.144.84:56378 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:09.964 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x8a0608fa, L:/10.110.144.84:56378 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.965 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x8a0608fa, L:/10.110.144.84:56378 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@35b1e512[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:09.965 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x8a0608fa, L:/10.110.144.84:56378 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@75e01d58[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:09.965 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8a0608fa, L:/10.110.144.84:56378 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3215906b[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:09.965 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x8a0608fa, L:/10.110.144.84:56378 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.965 DEBUG 1 --- [isson-netty-3-4] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@1129553489 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x8a0608fa, L:/10.110.144.84:56378 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@46cd1283[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:09.965 DEBUG 1 --- [isson-netty-3-5] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:09.965 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8a0608fa, L:/10.110.144.84:56378 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@46cd1283[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:09.973 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x1a260cac, L:/10.110.144.84:56394 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:09.973 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x1a260cac, L:/10.110.144.84:56394 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:09.973 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x1a260cac, L:/10.110.144.84:56394 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.974 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x1a260cac, L:/10.110.144.84:56394 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@53dad23f[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:09.974 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x1a260cac, L:/10.110.144.84:56394 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@195e1a3d[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:09.974 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1a260cac, L:/10.110.144.84:56394 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@278f5d8[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:09.974 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x1a260cac, L:/10.110.144.84:56394 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.974 DEBUG 1 --- [isson-netty-3-6] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@1706549145 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x1a260cac, L:/10.110.144.84:56394 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@53203b73[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:09.974 DEBUG 1 --- [isson-netty-3-7] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:09.974 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1a260cac, L:/10.110.144.84:56394 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@53203b73[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:09.982 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x89698635, L:/10.110.144.84:56410 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:09.982 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x89698635, L:/10.110.144.84:56410 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:09.983 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x89698635, L:/10.110.144.84:56410 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.983 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x89698635, L:/10.110.144.84:56410 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1d013d26[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:09.983 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x89698635, L:/10.110.144.84:56410 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@33f82ecf[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:09.983 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x89698635, L:/10.110.144.84:56410 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@46a487f8[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:09.983 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x89698635, L:/10.110.144.84:56410 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.983 DEBUG 1 --- [isson-netty-3-8] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@1156997155 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x89698635, L:/10.110.144.84:56410 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@51565bdc[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:09.984 DEBUG 1 --- [isson-netty-3-9] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:09.984 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x89698635, L:/10.110.144.84:56410 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@51565bdc[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:09.991 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x7021a4b8, L:/10.110.144.84:56420 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:09.991 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x7021a4b8, L:/10.110.144.84:56420 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:09.991 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x7021a4b8, L:/10.110.144.84:56420 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.992 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x7021a4b8, L:/10.110.144.84:56420 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@10ddc0c3[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:09.992 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x7021a4b8, L:/10.110.144.84:56420 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1e98a8d7[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:09.992 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7021a4b8, L:/10.110.144.84:56420 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3767fb2a[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:09.992 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x7021a4b8, L:/10.110.144.84:56420 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:09.992 DEBUG 1 --- [sson-netty-3-10] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@1172235965 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x7021a4b8, L:/10.110.144.84:56420 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@6a39434b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:09.992 DEBUG 1 --- [sson-netty-3-11] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:09.992 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7021a4b8, L:/10.110.144.84:56420 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6a39434b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.014 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x110cd1c6, L:/10.110.144.84:56436 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.014 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x110cd1c6, L:/10.110.144.84:56436 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.015 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x110cd1c6, L:/10.110.144.84:56436 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.015 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x110cd1c6, L:/10.110.144.84:56436 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@71f8a977[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.015 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x110cd1c6, L:/10.110.144.84:56436 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4e1fe263[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.015 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x110cd1c6, L:/10.110.144.84:56436 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@32be9ecc[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.015 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x110cd1c6, L:/10.110.144.84:56436 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.016 DEBUG 1 --- [sson-netty-3-12] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@1415528841 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x110cd1c6, L:/10.110.144.84:56436 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@2707a014[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.016 DEBUG 1 --- [sson-netty-3-13] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.016 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x110cd1c6, L:/10.110.144.84:56436 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2707a014[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.023 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x530cc975, L:/10.110.144.84:56438 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.023 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x530cc975, L:/10.110.144.84:56438 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.023 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x530cc975, L:/10.110.144.84:56438 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.024 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x530cc975, L:/10.110.144.84:56438 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3d8959c3[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.024 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x530cc975, L:/10.110.144.84:56438 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4bcaca8[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.024 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x530cc975, L:/10.110.144.84:56438 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4f8917d5[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.024 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x530cc975, L:/10.110.144.84:56438 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.024 DEBUG 1 --- [sson-netty-3-24] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@132815102 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x530cc975, L:/10.110.144.84:56438 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@4cb3d38f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.024 DEBUG 1 --- [sson-netty-3-14] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.025 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x530cc975, L:/10.110.144.84:56438 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4cb3d38f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.031 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0xf64f91fc, L:/10.110.144.84:56444 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.031 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0xf64f91fc, L:/10.110.144.84:56444 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.031 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0xf64f91fc, L:/10.110.144.84:56444 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.032 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xf64f91fc, L:/10.110.144.84:56444 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@a735306[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.032 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xf64f91fc, L:/10.110.144.84:56444 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@28566d28[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.032 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf64f91fc, L:/10.110.144.84:56444 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@29a59a81[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.032 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0xf64f91fc, L:/10.110.144.84:56444 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.032 DEBUG 1 --- [sson-netty-3-25] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@268582615 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0xf64f91fc, L:/10.110.144.84:56444 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@49d79518[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.032 DEBUG 1 --- [sson-netty-3-15] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.032 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf64f91fc, L:/10.110.144.84:56444 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@49d79518[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.039 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x547d58e8, L:/10.110.144.84:56456 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.039 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x547d58e8, L:/10.110.144.84:56456 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.040 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x547d58e8, L:/10.110.144.84:56456 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.040 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x547d58e8, L:/10.110.144.84:56456 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5e48f425[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.040 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x547d58e8, L:/10.110.144.84:56456 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@157c9b96[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.040 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x547d58e8, L:/10.110.144.84:56456 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@730eb165[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.040 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x547d58e8, L:/10.110.144.84:56456 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.040 DEBUG 1 --- [sson-netty-3-26] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@683884102 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x547d58e8, L:/10.110.144.84:56456 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@2a4fbf3e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.041 DEBUG 1 --- [sson-netty-3-16] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.041 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x547d58e8, L:/10.110.144.84:56456 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2a4fbf3e[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.047 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x3a656e97, L:/10.110.144.84:56460 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.047 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x3a656e97, L:/10.110.144.84:56460 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.048 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x3a656e97, L:/10.110.144.84:56460 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.048 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x3a656e97, L:/10.110.144.84:56460 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@465c2f8b[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.048 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x3a656e97, L:/10.110.144.84:56460 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@358efd3[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.048 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3a656e97, L:/10.110.144.84:56460 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1b7c8834[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.048 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x3a656e97, L:/10.110.144.84:56460 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.048 DEBUG 1 --- [sson-netty-3-17] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@1467619399 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x3a656e97, L:/10.110.144.84:56460 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@7dcc5e37[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.049 DEBUG 1 --- [sson-netty-3-18] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.049 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3a656e97, L:/10.110.144.84:56460 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7dcc5e37[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.055 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0x719780a1, L:/10.110.144.84:56468 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.055 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0x719780a1, L:/10.110.144.84:56468 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.055 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0x719780a1, L:/10.110.144.84:56468 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.056 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x719780a1, L:/10.110.144.84:56468 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@a01e865[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.056 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x719780a1, L:/10.110.144.84:56468 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4d4aa6f5[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.056 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x719780a1, L:/10.110.144.84:56468 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@e5302c5[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.056 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandEncoder        : channel: [id: 0x719780a1, L:/10.110.144.84:56468 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.056 DEBUG 1 --- [sson-netty-3-19] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@1146701080 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x719780a1, L:/10.110.144.84:56468 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@25627064[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.056 DEBUG 1 --- [sson-netty-3-27] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.056 TRACE 1 --- [sson-netty-3-18] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x719780a1, L:/10.110.144.84:56468 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@25627064[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.063 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0xa69a2290, L:/10.110.144.84:56484 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.063 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0xa69a2290, L:/10.110.144.84:56484 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.063 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0xa69a2290, L:/10.110.144.84:56484 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.064 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xa69a2290, L:/10.110.144.84:56484 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@36a94cf6[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.064 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xa69a2290, L:/10.110.144.84:56484 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@700c29c5[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.064 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa69a2290, L:/10.110.144.84:56484 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@15944ab7[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.064 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandEncoder        : channel: [id: 0xa69a2290, L:/10.110.144.84:56484 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.064 DEBUG 1 --- [sson-netty-3-28] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@2059155867 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0xa69a2290, L:/10.110.144.84:56484 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@756f7a03[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.064 DEBUG 1 --- [sson-netty-3-29] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.065 TRACE 1 --- [sson-netty-3-27] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa69a2290, L:/10.110.144.84:56484 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@756f7a03[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.074 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0xf8e6055a, L:/10.110.144.84:56498 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.074 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0xf8e6055a, L:/10.110.144.84:56498 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.074 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0xf8e6055a, L:/10.110.144.84:56498 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.074 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xf8e6055a, L:/10.110.144.84:56498 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2ab81749[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.074 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xf8e6055a, L:/10.110.144.84:56498 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7e7a0007[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.074 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf8e6055a, L:/10.110.144.84:56498 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3308f1e9[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.074 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandEncoder        : channel: [id: 0xf8e6055a, L:/10.110.144.84:56498 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.075 DEBUG 1 --- [sson-netty-3-30] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@2030154198 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0xf8e6055a, L:/10.110.144.84:56498 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@4db8a2a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.075 TRACE 1 --- [sson-netty-3-29] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xf8e6055a, L:/10.110.144.84:56498 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4db8a2a[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.075 DEBUG 1 --- [sson-netty-3-31] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.082 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0xa6ff3c48, L:/10.110.144.84:56508 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.082 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0xa6ff3c48, L:/10.110.144.84:56508 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.082 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0xa6ff3c48, L:/10.110.144.84:56508 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.083 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xa6ff3c48, L:/10.110.144.84:56508 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1237d317[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.083 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xa6ff3c48, L:/10.110.144.84:56508 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@570ec4fd[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.083 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa6ff3c48, L:/10.110.144.84:56508 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@41de912f[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.083 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandEncoder        : channel: [id: 0xa6ff3c48, L:/10.110.144.84:56508 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.083 DEBUG 1 --- [sson-netty-3-32] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@709131841 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0xa6ff3c48, L:/10.110.144.84:56508 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@ca03a4[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.083 DEBUG 1 --- [sson-netty-3-20] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.083 TRACE 1 --- [sson-netty-3-31] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa6ff3c48, L:/10.110.144.84:56508 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@ca03a4[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.090 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x3b3c017a, L:/10.110.144.84:56516 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.090 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x3b3c017a, L:/10.110.144.84:56516 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.090 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x3b3c017a, L:/10.110.144.84:56516 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.090 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x3b3c017a, L:/10.110.144.84:56516 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7b5ffef0[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.090 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x3b3c017a, L:/10.110.144.84:56516 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@767fee2e[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.090 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3b3c017a, L:/10.110.144.84:56516 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3eba37f8[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.090 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandEncoder        : channel: [id: 0x3b3c017a, L:/10.110.144.84:56516 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.091 DEBUG 1 --- [sson-netty-3-21] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@35950508 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x3b3c017a, L:/10.110.144.84:56516 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@5b1d3245[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.091 DEBUG 1 --- [sson-netty-3-22] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.091 TRACE 1 --- [sson-netty-3-20] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x3b3c017a, L:/10.110.144.84:56516 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5b1d3245[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.098 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x2e24b24b, L:/10.110.144.84:56526 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.098 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x2e24b24b, L:/10.110.144.84:56526 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.098 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x2e24b24b, L:/10.110.144.84:56526 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.099 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x2e24b24b, L:/10.110.144.84:56526 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5362a060[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.099 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x2e24b24b, L:/10.110.144.84:56526 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@427b7cea[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.099 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2e24b24b, L:/10.110.144.84:56526 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@8ebc07d[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.099 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x2e24b24b, L:/10.110.144.84:56526 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.100 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x2e24b24b, L:/10.110.144.84:56526 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4ecc10a0[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.103 DEBUG 1 --- [isson-netty-3-1] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@1832612621 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x2e24b24b, L:/10.110.144.84:56526 - R:10.110.142.16/10.110.142.16:6379], currentCommand=null, usage=0]
2023-05-26 09:02:10.103 DEBUG 1 --- [sson-netty-3-23] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.111 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x5cf413e3, L:/10.110.144.84:56532 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.112 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x5cf413e3, L:/10.110.144.84:56532 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.112 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x5cf413e3, L:/10.110.144.84:56532 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.112 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x5cf413e3, L:/10.110.144.84:56532 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@acf954d[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.112 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x5cf413e3, L:/10.110.144.84:56532 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@33b7d0af[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.112 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5cf413e3, L:/10.110.144.84:56532 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@317b9333[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.112 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandEncoder        : channel: [id: 0x5cf413e3, L:/10.110.144.84:56532 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.113 DEBUG 1 --- [isson-netty-3-2] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@519836513 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x5cf413e3, L:/10.110.144.84:56532 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@527e6ec[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.113 TRACE 1 --- [sson-netty-3-23] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5cf413e3, L:/10.110.144.84:56532 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@527e6ec[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.113 DEBUG 1 --- [isson-netty-3-3] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.120 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x8c119d46, L:/10.110.144.84:56540 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.120 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x8c119d46, L:/10.110.144.84:56540 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.121 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x8c119d46, L:/10.110.144.84:56540 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.121 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x8c119d46, L:/10.110.144.84:56540 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6a57260f[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.121 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x8c119d46, L:/10.110.144.84:56540 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@707de646[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.121 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8c119d46, L:/10.110.144.84:56540 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7a307281[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.122 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandEncoder        : channel: [id: 0x8c119d46, L:/10.110.144.84:56540 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.122 DEBUG 1 --- [isson-netty-3-4] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@593855474 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x8c119d46, L:/10.110.144.84:56540 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@12ea99b0[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.122 DEBUG 1 --- [isson-netty-3-5] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.122 TRACE 1 --- [isson-netty-3-3] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8c119d46, L:/10.110.144.84:56540 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@12ea99b0[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.129 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x37a2b68a, L:/10.110.144.84:56548 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.129 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x37a2b68a, L:/10.110.144.84:56548 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.129 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x37a2b68a, L:/10.110.144.84:56548 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.129 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x37a2b68a, L:/10.110.144.84:56548 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@8d89737[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.129 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x37a2b68a, L:/10.110.144.84:56548 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5eefb4ca[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.129 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x37a2b68a, L:/10.110.144.84:56548 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3accbf35[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.129 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandEncoder        : channel: [id: 0x37a2b68a, L:/10.110.144.84:56548 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.129 DEBUG 1 --- [isson-netty-3-6] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@1180723325 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x37a2b68a, L:/10.110.144.84:56548 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@713cf8e6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.130 TRACE 1 --- [isson-netty-3-5] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x37a2b68a, L:/10.110.144.84:56548 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@713cf8e6[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.130 DEBUG 1 --- [isson-netty-3-7] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.136 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x7d09e2e6, L:/10.110.144.84:56550 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.136 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x7d09e2e6, L:/10.110.144.84:56550 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.137 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x7d09e2e6, L:/10.110.144.84:56550 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.137 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x7d09e2e6, L:/10.110.144.84:56550 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4239dbb1[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.137 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x7d09e2e6, L:/10.110.144.84:56550 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6bd3509e[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.137 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7d09e2e6, L:/10.110.144.84:56550 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6a683e17[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.137 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandEncoder        : channel: [id: 0x7d09e2e6, L:/10.110.144.84:56550 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.137 DEBUG 1 --- [isson-netty-3-8] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@937424471 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x7d09e2e6, L:/10.110.144.84:56550 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@7db5b385[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.138 DEBUG 1 --- [isson-netty-3-9] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.138 TRACE 1 --- [isson-netty-3-7] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7d09e2e6, L:/10.110.144.84:56550 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7db5b385[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.144 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0xa358d691, L:/10.110.144.84:56560 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.144 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0xa358d691, L:/10.110.144.84:56560 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.144 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0xa358d691, L:/10.110.144.84:56560 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.144 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xa358d691, L:/10.110.144.84:56560 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2cbcbcf6[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.145 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xa358d691, L:/10.110.144.84:56560 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@10f9fa9b[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.145 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa358d691, L:/10.110.144.84:56560 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6bef58cc[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.145 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0xa358d691, L:/10.110.144.84:56560 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.145 DEBUG 1 --- [sson-netty-3-10] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@821945645 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0xa358d691, L:/10.110.144.84:56560 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@37594036[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.145 DEBUG 1 --- [sson-netty-3-11] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.145 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xa358d691, L:/10.110.144.84:56560 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@37594036[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.152 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x6f7030e8, L:/10.110.144.84:56566 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.152 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x6f7030e8, L:/10.110.144.84:56566 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.152 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x6f7030e8, L:/10.110.144.84:56566 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.153 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x6f7030e8, L:/10.110.144.84:56566 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5becfc25[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.153 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x6f7030e8, L:/10.110.144.84:56566 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5eb4bfd0[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.153 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6f7030e8, L:/10.110.144.84:56566 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@52de5fe5[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.153 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x6f7030e8, L:/10.110.144.84:56566 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.153 DEBUG 1 --- [sson-netty-3-12] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@973936893 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x6f7030e8, L:/10.110.144.84:56566 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@49548ef[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.153 DEBUG 1 --- [sson-netty-3-13] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.154 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6f7030e8, L:/10.110.144.84:56566 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@49548ef[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.159 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x7a7ec448, L:/10.110.144.84:56580 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.160 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x7a7ec448, L:/10.110.144.84:56580 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.160 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x7a7ec448, L:/10.110.144.84:56580 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.160 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x7a7ec448, L:/10.110.144.84:56580 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5ac7e766[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.160 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x7a7ec448, L:/10.110.144.84:56580 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@62e7a3fb[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.160 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7a7ec448, L:/10.110.144.84:56580 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6ae024ef[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.160 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandEncoder        : channel: [id: 0x7a7ec448, L:/10.110.144.84:56580 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.161 DEBUG 1 --- [sson-netty-3-24] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@1365391486 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x7a7ec448, L:/10.110.144.84:56580 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@9877066[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.161 DEBUG 1 --- [sson-netty-3-14] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.161 TRACE 1 --- [sson-netty-3-13] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x7a7ec448, L:/10.110.144.84:56580 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@9877066[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.168 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0xc6abd0a8, L:/10.110.144.84:56586 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.168 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0xc6abd0a8, L:/10.110.144.84:56586 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.168 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0xc6abd0a8, L:/10.110.144.84:56586 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.168 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xc6abd0a8, L:/10.110.144.84:56586 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@bd09f64[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.169 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0xc6abd0a8, L:/10.110.144.84:56586 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3e5c55e6[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.169 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc6abd0a8, L:/10.110.144.84:56586 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@78fc924b[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.169 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0xc6abd0a8, L:/10.110.144.84:56586 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.169 DEBUG 1 --- [sson-netty-3-25] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@138143601 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0xc6abd0a8, L:/10.110.144.84:56586 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@3b9cd290[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.169 DEBUG 1 --- [sson-netty-3-15] org.redisson.client.RedisConnection      : Connection created [addr=rediss://10.110.142.16:6379]
2023-05-26 09:02:10.169 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xc6abd0a8, L:/10.110.144.84:56586 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@3b9cd290[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.176 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x025aace4, L:/10.110.144.84:56596 - R:10.110.142.16/10.110.142.16:6379] message: *2
$4
AUTH(password masked)
2023-05-26 09:02:10.176 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x025aace4, L:/10.110.144.84:56596 - R:10.110.142.16/10.110.142.16:6379] message: *1
$8
READONLY

2023-05-26 09:02:10.176 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x025aace4, L:/10.110.144.84:56596 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.177 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x025aace4, L:/10.110.144.84:56596 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@91b718c[Not completed, 2 dependents], command=(AUTH), params=[Gewgre325geteqD7wStagingPS], codec=null]
2023-05-26 09:02:10.177 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +OK
, channel: [id: 0x025aace4, L:/10.110.144.84:56596 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6197473b[Not completed, 2 dependents], command=(READONLY), params=[], codec=null]
2023-05-26 09:02:10.177 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x025aace4, L:/10.110.144.84:56596 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@54cb57d7[Not completed, 2 dependents], command=(PING), params=[], codec=null]
2023-05-26 09:02:10.177 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandEncoder        : channel: [id: 0x025aace4, L:/10.110.144.84:56596 - R:10.110.142.16/10.110.142.16:6379] message: *1
$4
PING

2023-05-26 09:02:10.177 DEBUG 1 --- [sson-netty-3-26] o.r.connection.ClientConnectionsEntry    : new connection created: RedisConnection@1513079828 [redisClient=[addr=rediss://10.110.142.16:6379], channel=[id: 0x025aace4, L:/10.110.144.84:56596 - R:10.110.142.16/10.110.142.16:6379], currentCommand=CommandData [promise=java.util.concurrent.CompletableFuture@16518cf[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec], usage=0]
2023-05-26 09:02:10.177 DEBUG 1 --- [sson-netty-3-26] o.r.c.balancer.LoadBalancerManager       : Unfreezed entry: [freeSubscribeConnectionsAmount=1, freeSubscribeConnectionsCounter=value:50:queue:0, freeConnectionsAmount=32, freeConnectionsCounter=value:64:queue:0, freezeReason=null, client=[addr=rediss://10.110.142.16:6379], nodeType=SLAVE, firstFail=0]
2023-05-26 09:02:10.177  INFO 1 --- [sson-netty-3-26] o.r.cluster.ClusterConnectionManager     : slave: rediss://10.110.142.16:6379 added for slot ranges: [[5462-10922]]
2023-05-26 09:02:10.177 TRACE 1 --- [sson-netty-3-15] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x025aace4, L:/10.110.144.84:56596 - R:10.110.142.16/10.110.142.16:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@16518cf[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:10.178  INFO 1 --- [sson-netty-3-26] o.r.connection.pool.SlaveConnectionPool  : 32 connections initialized for 10.110.142.16/10.110.142.16:6379
2023-05-26 09:02:11.181 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:11.182 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062929000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062929159 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062929000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062930570 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062928000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062930000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062931177 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062927000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062930169 6 connected

, channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@5d70c3b[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:11.182 DEBUG 1 --- [sson-netty-3-14] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.141.243/10.110.141.243:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062929000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062929159 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062929000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062930570 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062928000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062930000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062931177 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062927000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062930169 6 connected

2023-05-26 09:02:12.187 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:12.188 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062930000 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062931000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062931789 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062930000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062926000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062927000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062930782 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062930580 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062930000 5 connected

, channel: [id: 0x93d4e779, L:/10.110.144.84:39138 - R:10.110.144.247/10.110.144.247:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@539e3940[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:12.188 DEBUG 1 --- [sson-netty-3-16] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.144.247/10.110.144.247:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062930000 4 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062931000 5 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062931789 5 connected 0-5461
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062930000 6 connected
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062926000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062927000 6 connected 5462-10922
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062930782 4 connected 10923-16383
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062930580 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062930000 5 connected

2023-05-26 09:02:13.194 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:13.195 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: $1906
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062931000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062929159 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062932185 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062930570 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062928000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062930000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062931177 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062927000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 1685062933194 1685062930169 6 connected

, channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@af3885a[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:13.195 DEBUG 1 --- [sson-netty-3-14] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.141.243/10.110.141.243:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062931000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062929159 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062932185 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062930570 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062928000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062930000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062931177 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062927000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 1685062933194 1685062930169 6 connected

2023-05-26 09:02:14.200 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:14.201 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062932000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062931000 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062932185 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062930570 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062931000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062932000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062931177 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062927000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062933195 6 connected

, channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@4aaeb1cd[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:14.202 DEBUG 1 --- [sson-netty-3-14] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.141.243/10.110.141.243:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062932000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062931000 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062932185 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062930570 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062931000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062932000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062931177 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062927000 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062933195 6 connected

2023-05-26 09:02:15.206 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandEncoder        : channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:15.207 TRACE 1 --- [sson-netty-3-14] o.r.client.handler.CommandDecoder        : reply: $1894
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062932000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062934204 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062933000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062930570 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062934000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062932000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062931177 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062934507 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062933195 6 connected

, channel: [id: 0x6dd3b6ae, L:/10.110.144.84:33030 - R:10.110.141.243/10.110.141.243:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7725da77[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:15.207 DEBUG 1 --- [sson-netty-3-14] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.141.243/10.110.141.243:6379:
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062932000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062934204 4 connected 10923-16383
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062933000 6 connected
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062930570 4 connected
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,master - 0 1685062934000 5 connected 0-5461
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062932000 5 connected
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062931177 5 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062934507 6 connected 5462-10922
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062933195 6 connected

2023-05-26 09:02:16.214 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:16.215 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: $1894
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062933000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062932261 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062930000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062932000 4 connected 10923-16383
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062933000 5 connected 0-5461
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062935294 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062933271 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062932000 5 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062934277 6 connected

, channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@2a9ba5b2[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:16.215 DEBUG 1 --- [sson-netty-3-22] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.136.174/10.110.136.174:6379:
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062933000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062932261 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062930000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062932000 4 connected 10923-16383
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062933000 5 connected 0-5461
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062935294 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062933271 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062932000 5 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062934277 6 connected

2023-05-26 09:02:17.221 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandEncoder        : channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379] message: *2
$7
CLUSTER
$5
NODES

2023-05-26 09:02:17.222 TRACE 1 --- [sson-netty-3-22] o.r.client.handler.CommandDecoder        : reply: $1894
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062933000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062932261 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062930000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062936302 4 connected 10923-16383
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062935000 5 connected 0-5461
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062935294 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062933271 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062936000 5 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062934277 6 connected

, channel: [id: 0x1b5a9800, L:/10.110.144.84:54606 - R:10.110.136.174/10.110.136.174:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@7ca560b4[Not completed, 2 dependents], command=(CLUSTER NODES), params=[], codec=null]
2023-05-26 09:02:17.222 DEBUG 1 --- [sson-netty-3-22] o.r.cluster.ClusterConnectionManager     : cluster nodes state got from 10.110.136.174/10.110.136.174:6379:
29934c959860d85fd0f5e8349966bce2f1799921 staging-dvc-redis-cluster-0002-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062933000 6 connected
162df60885b9f61f49eeb70eee1c8751ca2680bc staging-dvc-redis-cluster-0002-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062932261 6 connected 5462-10922
5649ef8eca8e5f1c0610e31599daa1b2382fd33d staging-dvc-redis-cluster-0003-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 myself,slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062930000 4 connected
ef2f642e6a90150e219ab332612c73dff1a38c8c staging-dvc-redis-cluster-0003-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062936302 4 connected 10923-16383
20a437c3dc9a9da0918e4ac540420b7ed3917ef7 staging-dvc-redis-cluster-0001-002.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 master - 0 1685062935000 5 connected 0-5461
7be61feb7376e00252d5e4cb455517d768848112 staging-dvc-redis-cluster-0001-003.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062935294 5 connected
f4671ae661f496f53414cdd2981b05e314f742b7 staging-dvc-redis-cluster-0003-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave ef2f642e6a90150e219ab332612c73dff1a38c8c 0 1685062933271 4 connected
8674a95a5c7021a421b92ae522893fe43dbf307e staging-dvc-redis-cluster-0001-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 20a437c3dc9a9da0918e4ac540420b7ed3917ef7 0 1685062936000 5 connected
21f27763f2e79853977fed2ab18f9c709ef13320 staging-dvc-redis-cluster-0002-001.staging-dvc-redis-cluster.hvkdjz.use1.cache.amazonaws.com:6379@1122 slave 162df60885b9f61f49eeb70eee1c8751ca2680bc 0 1685062934277 6 connected

2023-05-26 09:02:17.564 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x5d451a83, L:/10.110.144.84:42684 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.564 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandEncoder        : channel: [id: 0x00d8ac77, L:/10.110.144.84:42752 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.564 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandEncoder        : channel: [id: 0x6bc7d52b, L:/10.110.144.84:42706 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.564 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandEncoder        : channel: [id: 0x9ec09ec4, L:/10.110.144.84:42766 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.564 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x718982ca, L:/10.110.144.84:42744 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.564 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandEncoder        : channel: [id: 0x638588a3, L:/10.110.144.84:42686 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.564 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandEncoder        : channel: [id: 0x1230d5b1, L:/10.110.144.84:42720 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.564 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandEncoder        : channel: [id: 0x8b328e3d, L:/10.110.144.84:42768 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.564 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandEncoder        : channel: [id: 0x49034abd, L:/10.110.144.84:42756 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.564 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xe3825aed, L:/10.110.144.84:42734 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.565 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x718982ca, L:/10.110.144.84:42744 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@432faf46[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:17.565 TRACE 1 --- [sson-netty-3-28] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x9ec09ec4, L:/10.110.144.84:42766 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@f438939[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:17.565 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x5d451a83, L:/10.110.144.84:42684 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@21fb3f6b[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:17.565 TRACE 1 --- [sson-netty-3-30] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x8b328e3d, L:/10.110.144.84:42768 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1d2b509d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:17.565 TRACE 1 --- [isson-netty-3-9] o.r.client.handler.CommandPubSubDecoder  : reply: +PONG
, channel: [id: 0x638588a3, L:/10.110.144.84:42686 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@6d1e4f27[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:17.565 TRACE 1 --- [sson-netty-3-17] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x00d8ac77, L:/10.110.144.84:42752 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@51d1fa8f[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:17.565 TRACE 1 --- [sson-netty-3-11] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x6bc7d52b, L:/10.110.144.84:42706 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@21a17115[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:17.565 TRACE 1 --- [sson-netty-3-24] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x1230d5b1, L:/10.110.144.84:42720 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@884abab[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:17.565 TRACE 1 --- [sson-netty-3-19] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0x49034abd, L:/10.110.144.84:42756 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@956313d[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:17.566 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandDecoder        : reply: +PONG
, channel: [id: 0xe3825aed, L:/10.110.144.84:42734 - R:10.110.129.61/10.110.129.61:6379], command: CommandData [promise=java.util.concurrent.CompletableFuture@1834fc50[Not completed, 1 dependents], command=(PING), params=[], codec=org.redisson.client.codec.StringCodec]
2023-05-26 09:02:17.664 TRACE 1 --- [isson-netty-3-2] o.r.client.handler.CommandEncoder        : channel: [id: 0x9e0249f6, L:/10.110.144.84:42814 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.664 TRACE 1 --- [sson-netty-3-12] o.r.client.handler.CommandEncoder        : channel: [id: 0xfe71ad77, L:/10.110.144.84:42862 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.664 TRACE 1 --- [sson-netty-3-32] o.r.client.handler.CommandEncoder        : channel: [id: 0xc17e083d, L:/10.110.144.84:42780 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.664 TRACE 1 --- [sson-netty-3-25] o.r.client.handler.CommandEncoder        : channel: [id: 0xe8cffa89, L:/10.110.144.84:42876 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.664 TRACE 1 --- [sson-netty-3-21] o.r.client.handler.CommandEncoder        : channel: [id: 0xbf6a03b6, L:/10.110.144.84:42792 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.664 TRACE 1 --- [isson-netty-3-6] o.r.client.handler.CommandEncoder        : channel: [id: 0x5f96959c, L:/10.110.144.84:42832 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.664 TRACE 1 --- [sson-netty-3-16] o.r.client.handler.CommandEncoder        : channel: [id: 0x45762bf3, L:/10.110.144.84:48152 - R:10.110.154.77/10.110.154.77:6379] message: *1
$4
PING

2023-05-26 09:02:17.664 TRACE 1 --- [isson-netty-3-8] o.r.client.handler.CommandEncoder        : channel: [id: 0x65ce0e77, L:/10.110.144.84:42844 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.664 TRACE 1 --- [isson-netty-3-1] o.r.client.handler.CommandEncoder        : channel: [id: 0x6676572f, L:/10.110.144.84:42798 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.664 TRACE 1 --- [sson-netty-3-10] o.r.client.handler.CommandEncoder        : channel: [id: 0x849154fc, L:/10.110.144.84:42854 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.664 TRACE 1 --- [sson-netty-3-26] o.r.client.handler.CommandEncoder        : channel: [id: 0x198f5dc0, L:/10.110.144.84:42892 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

2023-05-26 09:02:17.664 TRACE 1 --- [isson-netty-3-4] o.r.client.handler.CommandEncoder        : channel: [id: 0xb3fdef01, L:/10.110.144.84:42826 - R:10.110.129.61/10.110.129.61:6379] message: *1
$4
PING

```

