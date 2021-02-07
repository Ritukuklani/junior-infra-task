# Prometheus

Some of the features of Prometheus that make it a good fit for a monitoring tool are:
- Service discovery to make configuration easier.
- Hundreds of exporters built by the open-source community.
- Instrumentation libraries to get custom metrics from your application.
- It is OSS, under the CNCF umbrella, being the second project to graduate after Kubernetes.
- Kubernetes is already instrumented and exposes Prometheus metrics in all of its services.

Some of the challenges with Prometheus are:
- We need to have two different Grafana installations and need to switch between them to see metrics from development and staging.
- It doesn’t allow global visibility. Several production clusters would make this a new requirement.
- Operations can be cumbersome and time consuming.
- Security is not a feature included in Prometheus. As long as the communication between Prometheus and Grafana is intracluster, this is not an issue. However, as you get Grafana out of the cluster, you need to implement something on top of Prometheus to secure the connection and control access to the metrics. There are many solutions to this issue but they require some effort of implementation and maintenance (manage certificates, create ingress controllers, configure security in Grafana, etc.).
- If the clusters are dynamic or change, you often need to implement a way to automatically add datasources to Grafana every time you deploy a Prometheus in a cluster.
- This allows us to mix in a dashboard panels from different sources, but we still can’t query services across different clusters and perform really global queries.
- Controlling who is accessing what data becomes more important, and an RBAC system may be required. Integration with identity services is most likely necessary in order to keep the user base updated, and this might become a compliance requirement.

# New Relic

In addition to providing visibility into operational data—such as the number of resources used and namespaces per cluster and per pod—an important part of monitoring Kubernetes is having the ability to see the relationships between objects in a cluster using Kubernetes’ built-in labeling system.

New Relic integrates with Kubernetes in a number of ways:

- Google Kubernetes Engine (GKE): GKE provides an environment for deploying, managing, and scaling your containerized applications using Google-supplied infrastructure.

To get started monitoring Kubernetes with New Relic, you’ll need to activate the Kubernetes integration by deploying the newrelic-infra agent onto your Kubernetes cluster. The New Relic Kubernetes integration brings in system-level metrics, allowing you to view, troubleshoot, and alert on the most important parts of your cluster. Use the integration’s out-of-the-box dashboard to inspect a single container, or scale up to see large, multi-cluster deployments across different Kubernetes entities, including nodes, pods, namespaces, and containers.