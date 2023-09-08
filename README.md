# K8S-Load-Balancer

Note: If in-case LoadBalancerIP is in pending. Then use (minikube tunnel) in a separate terminal.

IMP: To place the loadbalancing is working or not, means nginx request are coming continously for that we need to get into the POD.

Step:1 - kubectl get pods

Step:2 - kubectl exec -it [PODNAME] -- sh

Step:3 - Write the code to hit requests continouly it is working or not. -- Terminal-1
         i=1
         while [ "$i" -le 20 ]; do
           curl curl http://192.168.49.2:31000
           i=$(( i+1 ))
           done
           
Step:4 - To see weather load is distributing or not. -- Terminal-2
         kubectl logs [PODNAME] -f [to monitor the logs]
         
Step:5 - Now, move to step3[Terminal-1] - and hit nginx service 20 times.

Note: Load is distributing 20 times.

Step:6 - kubectl get endpoints - To see which pods associated with the sevrice.
