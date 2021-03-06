# Autoscale my application
1. Set CPU and Memory limits on your deployment:
```
$ oc set resources dc manawa-todo --limits=cpu=200m,memory=512Mi --requests=cpu=100m,memory=256Mi
```

2. Then, configure the auto-scaling:
```
$ oc autoscale dc manawa-todo --min 1 --max 10 --cpu-percent=80
```

3. Check :
```
$ oc get hpa
```

4. Finally, launch an ab testing:
```
$ ab -n 10000 -c 20 https://manawa-todo-devweek-<LDAP>-todolist.euw1-gcp-poc.adeo.cloud/tasks
```

5. And now check hpa and pods:
```
$ oc get hpa && oc get po && oc get dc
```

