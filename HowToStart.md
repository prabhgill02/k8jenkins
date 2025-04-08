# Start the cluster
minikube start

# create the ns
kubectl create namespace jenkins

# Run the services
ansible-playbook up.yaml
(if getting error then make changes in the up.yaml)

# Check the svc runnings
kubectl get svc -n jenkins

# Forward the port
kubectl port-forward -n jenkins svc/jenkins 8080:8080

# Forward the ngrok-port
kubectl port-forward -n jenkins svc/ngrok 4040:4040

# Retrieve password
kubectl exec --namespace jenkins -it $(kubectl get pods --namespace jenkins -l "app=jenkins" -o jsonpath="{.items[0].metadata.name}") -- cat /var/jenkins_home/secrets/initialAdminPassword
