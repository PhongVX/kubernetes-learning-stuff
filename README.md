# Install kubeadm, kubectl, kubelet
https://www.mirantis.com/blog/how-install-kubernetes-kubeadm/
## Create Token
```kubeadm token create --print-join-command```
## Join Cluster
```kubeadm token create --print-join-command```
# Install kubernetest-dashboard
https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/
# Deploy Pod On Master Node
```kubectl taint nodes --all node-role.kubernetes.io/master-```
# Pods
Explain pod
```kubectl explain pod --recursive=true```
Apply pod
```kubectl apply -f pod.yml```
Delete pod
```kubectl delete -f pod.yml```
```kubectl delete pod/podname```
# Proxy Or Port Forward
```kubectl proxy```
```kubectl port-forward pod/nginx-volume-mnt 8080:80```
# ReplicaSet
```kubectl get rs```
```kubectl describe rs/nginx-rs```
## Get Pod By Label
```kubectl get po -l "app=nginx-rs"```
# Horizontal Pod Autoscaler
```kubectl autoscale rs nginx-rs --max=2 --min=1```
```kubectl delete hpa nginx-rs```
## Get HPA
```kubectl get hpa```
# Deployment 
```kubectl apply -f ./deploy/nginx-deploy.yml```
```kubectl get deploy -o wide```
## Update Deployment
```kubectl set image deploy/nginx-deployment container-nginx=httpd --record```
Check status:
```kubectl rollout status deploy/nginx-deployment ```
Update cpu-limits and memory of pod
```kubectl set resources deploy/nginx-deployment -c=container-nginx --limits=cpu=200m,memory=200Mi```
Check history
```kubectl rollout history deploy/nginx-deployment```
Detail history
```kubectl rollout history deploy/nginx-deployment --revision=1```
Rollback deployment
```kubectl rollout undo deploy/nginx-deployment --to-revision=1```
Rollback previous
```kubectl rollout undo deploy/nginx-deployment```
Scale Deployment
```kubectl scale deploy/nginx-deployment --replicas=10```
HPA Scale Deployemnt
```kubectl autoscale deploy/nginx-deployment --min=2 --max=5 --cpu-percent=50```
Output Scale File
```kubectl get hpa/nginx-deployment -o yaml > nginx-deployment-hpa.yaml```