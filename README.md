# How to use
## Prerequisites
Have a Kubernetes cluster and kubectl connfigured
## Applying the manifests
`git clone https://github.com/VirajDalave/grafana-prometheus-without-helm.git`

`cd prometheus-setup && kubectl apply -f .`

`cd ../grafana-setup && kubectl apply-f .`

This will create the pods and services in "monitoring" namespace

## Accessing the services
Find the NodePort values:

`kubectl get svc -n monitoring`
You should see the NodePort assigned to Prometheus and Grafana. Access them via:

Prometheus: `http://<NODE-IP>:<PROMETHEUS-NODEPORT>`

Grafana: `http://<NODE-IP>:<GRAFANA-NODEPORT>`

You can also change the service type to ClusterIP and access using kubectl port-forward

`kubectl port-forward -n monitoring svc/prometheus-service 9090:9090`

`kubectl port-forward -n monitoring svc/grafana 3000:3000`

**The username for grafana is admin and pass is admin**
