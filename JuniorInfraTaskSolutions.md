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