

# Display the current-context
kubectl config current-context

# get list contexts
kubectl config get-contexts

# You can switch from local (minikube) to gcloud and back with:
kubectl config use-context CONTEXT_NAME

# Grant Kubernetes Authorization
For step by step overview of how to setup Kubernetes access authorization, access Kubernetes cluster API via kubectl

kubectl edit -n kube-system configmap/aws-auth
