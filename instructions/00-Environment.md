
## Remote cpu and memory limits from default quota
```
oc edit userquota default
```

## Scale worker machinesets to 0
```
oc get machinesets -n openshift-machine-api
oc edit machineset -n openshift-machine-api <>
```

## Change worker machineset instance type to m5d.2xlarge, 4 replicas
```
oc edit machineset -n openshift-machine-api <>
```
