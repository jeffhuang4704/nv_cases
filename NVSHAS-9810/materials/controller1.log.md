### controller log

###

```
\e[31mThis is red text\e[0m
\e[34mThis is blue text\e[0m

```


```
neuvector-controller-pod-854b7c7d46-fhw25.log (node-#1 - check this first)
====================================================
2025-01-26T04:50:44.156|INFO|CTL|cache.CacheMethod.MatchK8sAdmissionRules: first image summary - Image=registry-push.idst.ibaintern.de:5002/istio-ipdt/proxyv2:1.22.6-distroless digest= imageID=
...
....
2025-02-03T09:24:45.612Z [ERROR] agent.server.rpc: rejecting RPC conn from because rpc_max_conns_per_client exceeded: conn=from=10.42.55.36:36869
2025-02-03T09:24:45.864Z [ERROR] agent: Coordinate update error: error="No cluster leader"

(in the beginning, lots of Receive connect request)
2025-01-26T13:09:02.525|INFO|CTL|cache.AgentAdmissionRequest: Receive connect request - host=q0009381:6596a768-fb27-457f-8c3f-a37b220da290 id=4cafd2b5afb5d9f0c652783ac7c8b5a7e41295b9220d85687a880d9db227e2db
2025-01-26T13:09:02.774|INFO|CTL|cache.AgentAdmissionRequest: Receive connect request - host=q0003320:df3b39de-ca8e-4378-9092-665947d3f873 id=24f3f72d9753c44038a6de5b0a1f9c2a0daca6775e2e4373f04f2759504cb469
2025-01-26T13:09:02.907|INFO|CTL|cache.AgentAdmissionRequest: Receive connect request - host=q0003838:8d69c1bb-9e4f-409a-833f-1e094b83e862 id=6dcbd878342919c72f61f2b40434384198ee273001e5031a2d52c579d3ea44bd
2025-01-26T13:09:04.439|INFO|CTL|cache.AgentAdmissionRequest: Receive connect request - host=q0003322:a38626a4-a970-431f-b66d-465829643591 id=91221f7ce111344774649459e3dacaace11229cb34483091353e72fd020f6bd5
....  (算一下總共有多少個 "cache.AgentAdmissionRequest: Receive connect request", 然後開始 error...

2025-01-26T13:09:13.061Z [ERROR] agent.server.raft: peer has newer term, stopping replication: peer="{Nonvoter e502f51a-8d52-6c56-1869-76bb11b32c51 10.42.55.36:18300}"
2025-01-26T13:09:15.004|INFO|CTL|cluster.StartCluster.func2: Lead elected - lead=10.42.60.190:18300
2025-01-26T13:09:15.771|INFO|CTL|cluster.StartCluster.func1: - newLead=10.42.60.190 oldLead=
2025-01-26T13:09:16.161|INFO|CTL|utils.PerfSnapshot.func1: - at=2025-01-26 13:09:16.157645427 +0000 UTC m=+422425.720579844 label=p memLimit=6442450944 pid=1 prefix=ctl. profileLimit=1 workFolder=/var/nv_debug/snapshot/a47f288af60c8107802c69f24557cbc2b76bb1b9b8ff5c5b8941e175aa17ef0f workingSet=109572132864
2025-01-26T13:09:16.163|INFO|CTL|system.(*SystemTools).CGroupMemoryStatReset: - threshold=4831838208 usage=109572907008
2025-01-26T13:09:20.055Z [ERROR] agent.http: Request error: method=GET url="/v1/kv/lock/policy?consistent=&index=710787498" from=127.0.0.1:40852 error="node is not the leader"
2025-01-26T13:09:19.946|INFO|CTL|cluster.StartCluster.func1: - newLead= oldLead=10.42.60.190
2025-01-26T13:09:24.07 |INFO|CTL|cluster.StartCluster.func2: Lead loss detected
2025-01-26T13:09:24.544|INFO|CTL|cluster.StartCluster.func2: Cannot locate lead - join=neuvector-svc-controller.neuvector
2025-01-26T13:09:24.556|INFO|CTL|cluster.StartCluster.func2: Retry join - JoinAddr=[10.42.57.244 10.42.55.36 10.42.60.190]
2025-01-26T13:09:24.562Z [ERROR] agent.http: Request error: method=PUT url=/v1/agent/join/10.42.57.244 from=127.0.0.1:36218
  error=
  | 1 error occurred:
  | \t* Failed to join 10.42.57.244:18301: dial tcp 10.42.57.244:18301: connect: connection refused
  | 
  
2025-01-26T13:09:24.568|ERRO|CTL|cluster.(*consulMethod).Join: - error=Unexpected response code: 500 (1 error occurred:
    * Failed to join 10.42.57.244:18301: dial tcp 10.42.57.244:18301: connect: connection refused

) ip=10.42.57.244

...
2025-01-26T13:09:39.2  |INFO|CTL|cache.AgentAdmissionRequest: Receive connect request - host=q0010439:1b2cb03a-65e9-4ea3-bcef-bb12683b6a74 id=d4396a287e353c3e6be5e5a327e5ff7ef8fdfc685313faf750dd7da72e90b4a0
2025-01-26T13:09:39.665Z [ERROR] agent.server.raft: peer has newer term, stopping replication: peer="{Voter e502f51a-8d52-6c56-1869-76bb11b32c51 10.42.55.36:18300}"
2025-01-26T13:09:39.783Z [ERROR] agent.server: failed to reconcile member: member="{10.42.62.190 10.42.62.190 18301 map[build:1.20.1:920cc7c6 dc:neuvector id:00df7fd4-4125-8ce9-adaf-e2dbec831063 role:node segment: vsn:2 vsn_max:3 vsn_min:2] left 1 5 2 2 5 4}" partition=default error="leadership lost while committing log"
2025-01-26T13:09:41.126|INFO|CTL|cache.AgentAdmissionRequest: Receive connect request - host=q0002707:4fdbd2de-49d3-4465-9e57-b14c8603a143 id=1b5d126b3a9989b0dada9ed49411063b152ee274ad212978617525223bb5de57

2025-01-26T13:09:43.178|INFO|CTL|cluster.StartCluster.func2: Cannot locate lead - join=neuvector-svc-controller.neuvector
2025-01-26T13:09:43.364|INFO|CTL|cluster.StartCluster.func2: Retry join - JoinAddr=[10.42.55.36 10.42.57.244 10.42.60.190]

2025-01-26T13:09:52.288|INFO|CTL|utils.PerfSnapshot.func1: - package=/var/nv_debug/snapshot/ctl.snapshot.a47f288af60c8107802c69f24557cbc2b76bb1b9b8ff5c5b8941e175aa17ef0f.p.zip  (*這個的snapshot很重要)(因為在40秒後controller process就要exit)
2025-01-26T13:09:52.291|INFO|CTL|utils.PerfSnapshot.func1: done

2025-01-26T13:09:53.215Z [ERROR] agent.http: Request error: method=PUT url=/v1/agent/join/10.42.57.244 from=127.0.0.1:42838
  error=
  | 1 error occurred:
  | \t* Failed to join 10.42.57.244:18301: dial tcp 10.42.57.244:18301: connect: connection refused
  | 
  
2025-01-26T13:10:24.255Z [ERROR] agent.server: yamux: keepalive failed: i/o deadline reached
2025-01-26T13:10:24.364Z [ERROR] agent.server: yamux: Failed to write header: write tcp 10.42.60.190:18300->10.42.67.107:46095: use of closed network connection
2025-01-26T13:10:24.364Z [ERROR] agent.server: yamux: Failed to write header: write tcp 10.42.60.190:18300->10.42.69.231:51591: use of closed network connection

...
2025-01-26T13:10:27.760Z [ERROR] agent.server: yamux: keepalive failed: connection write timeout
2025-01-26T13:10:27.762Z [ERROR] agent: yamux: Failed to write header: write tcp 10.42.60.190:40453->10.42.55.36:18300: use of closed network connection
2025-01-26T13:10:30|MON|Process ctrl exit status -1, pid=19402
```