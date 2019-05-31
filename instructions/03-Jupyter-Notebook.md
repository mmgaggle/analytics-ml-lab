## Create and Deploy Jupyter Notebook
```
oc new-app -i jupyter-notebook:latest \
           -e JUPYTER_NOTEBOOK_PASSWORD=developer \
           -e S3_ENDPOINT="http://rook-ceph-rgw-my-store.rook-ceph.svc.cluster.local:8000"
```

## Make RGW Credentials available to Jupyter Notebook environment
```
oc set env --from=secret/s3-user-demo dc/jupyter-notebook
```

## Expose route to Jupyter Notebook Service
```
oc expose svc/jupyter-notebook
```
