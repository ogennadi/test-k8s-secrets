# test-k8s-secrets

Use k8s secrets on Minikube
1. Install Minikube: https://kubernetes.io/docs/tasks/tools/#kubectl


2. Open an admin terminal


3. Create k8s cluster: https://minikube.sigs.k8s.io/docs/tutorials/kubernetes_101/module1/
	
```
minikube start
```
	 
4. Create secrets: https://kubernetes.io/docs/tasks/inject-data-application/distribute-credentials-secure/#configure-all-key-value-pairs-in-a-secret-as-container-environment-variables

```
kubectl create secret generic test-secret --from-literal=SECRET='my-app'

kubectl create -f pod-secret-envFrom.yaml

kubectl exec -i -t envfrom-secret -- env
```
	
5. Edit secrets: https://kubernetes.io/docs/tasks/configmap-secret/managing-secret-using-kubectl/#edit-secret

```
kubectl edit secrets test-secret

kubectl delete -f pod-secret-envFrom.yaml 

kubectl create -f pod-secret-envFrom.yaml

kubectl get pods

kubectl exec -i -t envfrom-secret -- env
```
	
6. Delete secrets: https://kubernetes.io/docs/tasks/configmap-secret/managing-secret-using-kubectl/#clean-up

```
kubectl delete secret test-secret

kubectl delete -f pod-secret-envFrom.yaml 

kubectl create -f pod-secret-envFrom.yaml

kubectl get pods

kubectl describe pod
```
