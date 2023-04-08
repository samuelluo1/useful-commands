# Useful Commands

### shell

```
kill $(lsof -t -i:8080)
```

```
grep -o 'keyword' file_name | wc -l
```
```
grep -C 10 'keyword' file_name
```

```
while [ ! -d /tomcat/webapps/ROOT/mail ]; do sleep 1; done; ln -s /share/images /tomcat/webapps/ROOT/images
```

### redis-cli
```
redis-cli -h redis_domain keys key_prefix* | sed 's/^/get /' | xargs -i sh -c 'echo {}; redis-cli -h redis_domain {}; echo'
```

```
redis-cli -h redis_domain SCAN cursor match key_prefix* count 10000 | sed 's/^/get /' | xargs -i sh -c 'echo {}; redis-cli -h redis_domain {}; echo'
```

```
redis-cli -h 10.8.96.8 -p 6379 KEYS "key_prefix*" | xargs redis-cli -h 10.8.96.8 -p 6379 DEL
```

### docker
```
docker run -p 8080:8080 $(docker images -q | awk 'NR==1')
```
```
docker exec -u root -it $(docker ps -q | awk 'NR==1') /bin/bash
```
```
docker stop $(docker ps -q | awk 'NR==1')
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
