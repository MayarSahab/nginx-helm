# nginx-helm
# Notes on the Chart
- I have reused the default bitnami chart for nginx with its default values.
- If we need to change any defaults like replicas, service type,.... etc. It can be modified through the Values.yaml file.

# Notes on the pipeline
Here are some assumptions:

- Two created namespaces Dev and Stage.
- Kubeconfig is adjusted to be used for the two namespaces with the same user.
- Kubeconfig is stored as a Secretfile inside Jenkins Credentials (Withcredentials).
- Two stages for deployment on both namespaces with parameter "--namepsace" to override the default namespace configured inside the Chart.
- Kubernetes Jenkins plugin is used to add the cluster connection, agents with the Containers images and the needed pod configuration.
- Container "helm" Image used by the labeled agent/pod "Kubernetes" should have helm installed inside it. You can find the pod template that can be added to Jenkins "Configure nodes and Clouds" inside "agent.yaml" file. 

