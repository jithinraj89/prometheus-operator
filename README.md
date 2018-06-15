# prometheus-operator

### Overview: ###

Prometheus is an open source monitoring and alerting toolkit made for monitoring applications in clusters. Inspired by Google’s Borgmon, it was designed from day one for the Kubernetes model of assigning and managing units of work. Prometheus also has beta support for using the Kubernetes API itself to discover cluster services and monitoring targets. Monitoring a Kubernetes cluster with Prometheus is a natural choice as Kubernetes components themselves are instrumented with Prometheus metrics, therefore those components simply have to be discovered by Prometheus and most of the cluster is monitored.
Prometheus runs as a pod in your Kubernetes cluster. Deploying Prometheus requires two Kubernetes objects: a deployment for the Prometheus pod itself, and a ConfigMap that tells Prometheus how to connect to your cluster.
This entire setup provides visualising, monitoring, and alerting based on metrics that are surfaced from the downstream systems.
You only need to have running Kubernetes cluster with deployed Prometheus. Prometheus will use metrics provided by cAdvisor via kubelet service (runs on each node of Kubernetes cluster by default) and via kube-apiserver service only.
Deploying Prometheus monitoring using Ansible


"Before starting the deployment you need to fill the group_vars, password_vars and inventory with relevant details"

Run below ansible playbook to start the deployment. ( New namespace monitoring will be created for this deployment )

cd prometheus/

ansible-playbook -i inventory/<deploy_env> prometheus.yml --ask-vault-pass

e.g.: <deploy_env> = dev ( under prometheus/inventory/dev)

Playbook will deploy Prometheus along with Grafana under the monitoring namespace in the <deploy_env> cluster.
