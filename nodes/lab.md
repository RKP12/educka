## Lab
```
kubectl get nodes                    # get list of node in the cluster
kubectl get nodes -o wide            # get list of node in the cluster with wider output
kubectl describe node kube-node      # describe a node for detailed output

kubectl get node --selector='!node-role.kubernetes.io/master'  # Get all worker nodes

kubectl get nodes --show-labels      # display the labes for a all nodes in the cluster
kubectl label node kube-node env=prod # label the nodes
kubectl get node --selector='env=prod' # get all node with env=prod

kubectl taint nodes node1 key=value:NoSchedule  #  places a taint on node node1. The taint has key key, value value, and taint effect NoSchedule. This means that no pod will be able to schedule onto node1 unless it has a matching toleration
kubectl taint nodes node1 key:NoSchedule-  # to remove the taint

kubectl get node kube-node -o yaml   # view the node configuration yaml
kubectl edit node kube-node          # edit & apply the node configuration 

kubectl cordon kube-node             # Mark kube-node as unschedulable
kubectl drain kube-node              # Drain kube-node in preparation for maintenance
kubectl drain kube-node --ignore-daemonsets --force  
kubectl uncordon kube-node           # Mark kube-node as schedulable
kubectl delete node kube-node        # remove node from cluster
kubectl run nginx --image=nginx --generator=run-pod/v1 #Create a new pod with the NGINX image
kubectl get pods                      # count how many pod created now 
kubectl describe pod newpod-<id>' or 'kubectl get pods -o wide' and look under the containers section.   #What is the image used to create the new pods? You must look at one of the new pods in detail to figure this out.
kubectl describe pod newpod-<id>     #Which nodes are these pods placed on?
kubectl delete pod webapp            #delete webapp pod
kubectl run redis --image=redis123 --generator=run-pod/v1 #Create a new pod with the name 'redis' and with the image 'redis123'
kubectl apply or kubectl edit pod redis command. #Now fix the image on the pod to 'redis'. Update the pod-definition file
