## NVSHAS-9810 NeuVector controller not responding and UI not accessible

### Case description

The customer reported that NeuVector UI is not loading. This is an installation running for a long time and this customer reported before that controller pods got stuck and it is required to scale down and scale up the controller deployment to recover from failure.

### Materias we have
TODO: list the log files we have

Pods status

```
NAME                                                 READY   STATUS             RESTARTS           AGE
neuvector-controller-pod-854b7c7d46-fhw25            1/1     Running            0                  25d
neuvector-controller-pod-854b7c7d46-nktdw            1/1     Running            0                  25d
neuvector-controller-pod-854b7c7d46-rwcxp            1/1     Running            0                  25d

neuvector-enforcer-pod-24526                         0/1     CrashLoopBackOff   1557 (3m33s ago)   25d
neuvector-enforcer-pod-2qj5k                         1/1     Running            8 (8d ago)         25d
neuvector-enforcer-pod-2rlbg                         0/1     CrashLoopBackOff   1281 (19s ago)     25d
neuvector-enforcer-pod-2tc5s                         1/1     Running            4 (12d ago)        25d
neuvector-enforcer-pod-2z5w4                         1/1     Running            4 (10d ago)        25d
neuvector-enforcer-pod-65dld                         1/1     Running            4 (12d ago)        25d
neuvector-enforcer-pod-6nvsn                         1/1     Running            1 (12d ago)        25d
neuvector-enforcer-pod-7vhk9                         1/1     Running            4 (11d ago)        25d
neuvector-enforcer-pod-7x6gr                         1/1     Running            1413 (7m24s ago)   25d
neuvector-enforcer-pod-8bqt7                         0/1     CrashLoopBackOff   1115 (4m52s ago)   25d
neuvector-enforcer-pod-8cg84                         1/1     Running            6 (10d ago)        25d
neuvector-enforcer-pod-8fbms                         1/1     Running            1 (11d ago)        25d
neuvector-enforcer-pod-8m8r2                         1/1     Running            8 (9d ago)         25d
neuvector-enforcer-pod-9647j                         1/1     Running            1262 (7m40s ago)   25d
neuvector-enforcer-pod-cc9dh                         1/1     Running            1168 (6m41s ago)   25d
neuvector-enforcer-pod-dslcf                         1/1     Running            4 (12d ago)        25d
neuvector-enforcer-pod-dzgv7                         1/1     Running            15 (10d ago)       25d
neuvector-enforcer-pod-fn2bg                         1/1     Running            10 (9d ago)        25d
neuvector-enforcer-pod-fnt77                         1/1     Running            4 (10d ago)        25d
neuvector-enforcer-pod-g47xf                         1/1     Running            4 (14d ago)        25d
neuvector-enforcer-pod-h48j2                         1/1     Running            24 (9d ago)        25d
neuvector-enforcer-pod-hgmb6                         1/1     Running            1156 (7m18s ago)   25d
neuvector-enforcer-pod-hww9k                         0/1     CrashLoopBackOff   1354 (109s ago)    25d
neuvector-enforcer-pod-jpd7s                         1/1     Running            9 (10d ago)        25d
neuvector-enforcer-pod-k8ctb                         1/1     Running            2 (13d ago)        25d
neuvector-enforcer-pod-kkrck                         0/1     CrashLoopBackOff   807 (96s ago)      25d
neuvector-enforcer-pod-ljkns                         0/1     CrashLoopBackOff   209 (4m23s ago)    25d
neuvector-enforcer-pod-m5s9n                         1/1     Running            7 (11d ago)        25d
neuvector-enforcer-pod-n94c6                         1/1     Running            1295 (8m12s ago)   25d
neuvector-enforcer-pod-nmtzb                         1/1     Running            13 (9d ago)        25d
neuvector-enforcer-pod-nwhnf                         0/1     CrashLoopBackOff   569 (3m32s ago)    25d
neuvector-enforcer-pod-nzrzh                         1/1     Running            3 (8d ago)         25d
neuvector-enforcer-pod-pjgs7                         1/1     Running            5 (8d ago)         25d
neuvector-enforcer-pod-q2wr8                         0/1     CrashLoopBackOff   1290 (92s ago)     25d
neuvector-enforcer-pod-q4zdt                         1/1     Running            19 (10d ago)       25d
neuvector-enforcer-pod-qdfgv                         1/1     Running            6 (10d ago)        25d
neuvector-enforcer-pod-rtqdj                         1/1     Running            3 (14d ago)        25d
neuvector-enforcer-pod-rx49p                         0/1     CrashLoopBackOff   1349 (101s ago)    25d
neuvector-enforcer-pod-s8f9b                         0/1     CrashLoopBackOff   1297 (39s ago)     25d
neuvector-enforcer-pod-sxblr                         1/1     Running            6 (11d ago)        25d
neuvector-enforcer-pod-t97vz                         1/1     Running            2 (11d ago)        25d
neuvector-enforcer-pod-tn2vd                         1/1     Running            6 (10d ago)        25d
neuvector-enforcer-pod-vhsvj                         1/1     Running            9 (9d ago)         25d
neuvector-enforcer-pod-wcxc2                         1/1     Running            15 (9d ago)        25d
neuvector-enforcer-pod-wvrd5                         1/1     Running            1 (14d ago)        25d
neuvector-enforcer-pod-xvrkm                         1/1     Running            9 (10d ago)        25d
neuvector-enforcer-pod-zjd22                         1/1     Running            16 (10d ago)       25d
neuvector-enforcer-pod-zkvzx                         1/1     Running            5 (8d ago)         25d
neuvector-enforcer-pod-zpsg4                         1/1     Running            1277 (5m21s ago)   25d
neuvector-manager-pod-799bb568f4-24ggs               1/1     Running            0                  25d
neuvector-prometheus-exporter-pod-7f9d79d45d-bqcdz   1/1     Running            0                  25d
neuvector-scanner-pod-86976b45fc-5bgfg               1/1     Running            0                  9h
neuvector-scanner-pod-86976b45fc-dcs4w               1/1     Running            0                  9h
neuvector-scanner-pod-86976b45fc-hnxwd               1/1     Running            0                  9h
neuvector-updater-pod-28972800-75m5s                 0/1     Completed          0                  2d9h
neuvector-updater-pod-28974240-2ct8c                 0/1     Completed          0                  33h
neuvector-updater-pod-28975680-rjlv2                 0/1     Completed          0                  9h
```

Controller log files (time range)
```
// #1 log time range
2025-01-26T04:50:44.156|INFO|CTL|cache.CacheMethod.MatchK8sAdmissionRules: first image summary - Image=registry-push.idst.ibaintern.de:5002/istio-ipdt/proxyv2:1.22.6-distroless digest= imageID=
(to)
2025-02-03T09:24:45.864Z [ERROR] agent: Coordinate update error: error="No cluster leader"

// #2 log time range
2025-02-03T09:16:11.05 |ERRO|CTL|kv.clusterHelper.AcquireLock: Acquire lock error - error=failed to create session: Unexpected response code: 500 (No cluster leader) key=lock/policy
(to)
2025-02-03T09:24:52.947|ERRO|CTL|rest.(*WebhookServer).validate: cacheAdmCtrlAudit - error=Queue full

// #3 log time range
2025-01-27T14:46:47.791Z [ERROR] agent.server.rpc: rejecting RPC conn from because rpc_max_conns_per_client exceeded: conn=from=10.42.55.36:50201
(to)
2025-02-03T09:24:55.564Z [ERROR] agent.server.rpc: rejecting RPC conn from because rpc_max_conns_per_client exceeded: conn=from=10.42.55.36:53457
```

### Excerpts of logs

node#1: neuvector-controller-pod-854b7c7d46-fhw25.log
node#2: neuvector-controller-pod-854b7c7d46-nktdw.log
node#3: neuvector-controller-pod-854b7c7d46-rwcxp.log

<details><summary>scripts</summary>

</details>

### Findings

### Plans