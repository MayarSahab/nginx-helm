# nginx-helm
# Notes on the Chart
- I have reused the default bitnami chart for nginx with its default values.
- If we need to change any defaults like replicas,resources,volumes, .... etc. It can be modified through the charts/bitnami/nginx/values.yaml file.

# Notes on the pipeline
Here are some assumptions:

- Two created namespaces prod and stage.
- Kubeconfig is adjusted to be used for the two namespaces with the same user.
- Kubeconfig is stored as a Secretfile inside Jenkins Credentials (Withcredentials) then the credentialID is used inside Jenkinsfile.
- Jenkins project is multibranch project to enable deployment for different branches.
- One stage for deployment on both namespaces with parameter "--namepsace" to override the default namespace configured inside the Chart with conditions according to the branch name the deployment will take place inside which namespace.
- Kubernetes Jenkins plugin is used to add the cluster connection (URL) and namespace inside slaves will be launched every time the pipeline starts., agents (Jenkins slaves) with the Containers images and the needed pod configuration as pod matching labels.
- Container "helm" Image used by the labeled agent/pod "kubernetes" should have helm installed inside it. You can find the pod template that can be added to Jenkins "Configure nodes and Clouds" inside "agent.yaml" file containing the "helm" container with public latest image of alpine/helm.

