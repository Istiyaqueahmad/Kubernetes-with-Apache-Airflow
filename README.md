# Kubernetes-with-Apache-Airflo

This repository contains the necessary configuration files and DAGs (Directed Acyclic Graphs) for setting up a robust data engineering environment using Kubernetes and Apache Airflow. It includes the setup for the Kubernetes Dashboard, which provides a user-friendly web interface for managing Kubernetes clusters, and Apache Airflow, a platform to programmatically author, schedule, and monitor workflows

# DAGs
 1-fetch_and_preview.py: A DAG for fetching data and providing a preview.

 2-hello.py: A simple example DAG to demonstrate basic Airflow concepts.

# Kubernetes (k8s) Configuration
 1-dashboard-adminuser.yaml: YAML file for setting up an admin user for the Kubernetes Dashboard.

 2-dashboard-clusterrole.yaml: YAML file defining the cluster role for the Kubernetes Dashboard.

 3-dashboard-secret.yaml: YAML file for managing secrets used by the Kubernetes Dashboard.

 4-recommended-dashboard.yaml: YAML file for deploying the recommended Kubernetes Dashboard setup.

 5-values.yaml: YAML file containing values for customizing the Kubernetes setup.

Getting Started
# Prerequisites

A Kubernetes cluster
kubectl installed and configured
Helm (optional, but recommended for managing Kubernetes applications)

# Setup
Deploy the Kubernetes Dashboard:

# To deploy the Kubernetes Dashboard, apply the YAML files in the k8s directory:

kubectl apply -f k8s/
This will set up the Kubernetes Dashboard with the necessary roles and permissions.

Accessing the Kubernetes Dashboard:

To access the Dashboard, you may need to start a proxy server:

# kubectl proxy
Then, access the Dashboard at: http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/.

Use the token generated for the admin user to log in (see dashboard-secret.yaml).

# Deploy Apache Airflow:

You can deploy Apache Airflow using Helm or by applying custom YAML files. For Helm:

1-helm repo add apache-airflow https://airflow.apache.org
2 helm install airflow apache-airflow/airflow -f k8s/values.yaml
3-This will deploy Airflow with the settings defined in values.yaml.

# Adding DAGs to Airflow:

Copy your DAG files (e.g., fetch_and_preview.py, hello.py) into the DAGs folder of your Airflow deployment. The method of copying depends on your Airflow setup (e.g., using Persistent Volume, Git-sync).

# Usage
1-Kubernetes Dashboard: Use the Dashboard to monitor and manage the Kubernetes cluster.
2-Apache Airflow: Access the Airflow web UI to manage, schedule, and monitor workflows.
