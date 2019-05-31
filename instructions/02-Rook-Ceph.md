# Rook Deployment

## Setup security contexts and deploy rook-ceph operator
```
oc create -f scc.yaml
oc create -f operator.yaml


## Create Ceph cluster, 3 mons and OSDs on every host
```
oc create -f cluster.yaml
```

## Create toolbox deployment for Ceph CLI interaction
```
oc create -f toolbox.yaml
```

## Create object storage service
```
oc create -f object.yaml
```

## Create demo user
```
oc create -f object-user.yaml
```

## Copy S3 demo user credentials into default namespace
```
oc get secret -n rook-ceph rook-ceph-object-user-my-store-demo -o yaml | \
              egrep -v 'uid|namespace|selfLink|creation|resourceVersion' | \
              sed 's/rook-ceph-object-user-my-store-demo/s3-user-demo/g' | \
              oc create -f -
```
