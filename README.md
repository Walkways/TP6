# TP6

Create CRD (Custom Resource Definitions) for Prometheus Operator:

kubectl apply -f 01-prometheus-operator-crd

Deploy Prometheus Operator
kubectl apply -f 02-prometheus-operator
kubectl get pods -n default

Deploy Prometheus
kubectl apply -f 03-prometheus
kubectl get pods -n default
kubectl logs -f prometheus-prometheus-0 prometheus

Create Namespace Ingress
kubectl apply -f 04-ingress-nginx/namespace.yaml

Deploy Nginx Admission Webhook
kubectl apply -f 04-ingress-nginx/admission-webhooks

Deploy Nginx Ingress Controller
kubectl apply -f 04-ingress-nginx
kubectl get pods -n ingress

Create ServiceMonitor for Nginx Controller
kubectl apply -f 05-servicemonitor
kubectl get servicemonitors

Check Prometheus Targets
kubectl port-forward svc/prometheus 9090:9090 -n default

Deploy Sample App
kubectl apply -f 07-sample-app
kubectl get pods -n default
kubectl get ingress -n default

Create DNS record
kubectl get svc -n ingress

Deploy Grafana
kubectl apply -f 06-grafana
kubectl get pods -n default

Grafana Dashboard
kubectl port-forward svc/grafana 3000 -n default

kubectl delete all --all --namespace=default
