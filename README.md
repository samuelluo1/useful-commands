# Useful Commands

### shell

```
tail -f example.log
```

```
vi /etc/fstab
```

```
grep -o 'keyword' file_name | wc -l
```

```
while [ ! -d /tomcat/webapps/ROOT/mail ]; do sleep 1; done; rm -rf /tomcat/webapps/ROOT/images; ln -s /share/images /tomcat/webapps/ROOT/images
```

### redis-cli
```
redis-cli -h redis_domain keys key_prefix\* | sed 's/^/get /' | xargs -i sh -c 'echo {}; redis-cli -h redis_domain {}; echo'
```

```
redis-cli -h r-uf6pujrjvtzyceqlsj.redis.rds.aliyuncs.com scan 0 match tomcat-cache-\* count 10000 | sed 's/^/get /' | xargs -i sh -c 'echo {}; redis-cli -h r-uf6pujrjvtzyceqlsj.redis.rds.aliyuncs.com {}; echo'
```

```
redis-cli -h 10.8.96.8 -p 6379 KEYS "tomcat-cache-*" | xargs redis-cli -h 10.8.96.8 -p 6379 DEL
```

### docker
```
docker kill $(docker ps -q | grep tomcat)
```

### kubectl

```
kubectl logs -f -l app=label_name --all-containers
```

```
kubectl exec -it $(kubectl get pod -l app=label_name | grep Running | awk 'NR==1{print $1}') -- /bin/bash
```

```
kubectl port-forward pod_name 8080:8080
```
