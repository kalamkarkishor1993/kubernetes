🔴 What is Kubernetes?
Kubernetes is an open-source container orchestration platform that automates deployment, scaling, networking, and self-healing of containerized applications across a cluster of machines.

🔴 Why is Kubernetes important?
Modern applications consist of many microservices running in containers. Kubernetes manages these containers efficiently by providing high availability, scalability, fault tolerance, and declarative infrastructure management.

🔴 What are the key features of Kubernetes?
Automatic container scheduling
Self-healing (restart, reschedule)
Horizontal & vertical scaling
Service discovery & load balancing
Rolling updates & rollbacks
Configuration & secret management
Cloud-agnostic design
🔴 What is Container Orchestration?
Container orchestration is the automated management of containerized applications, including deployment, networking, scaling, and lifecycle management. Kubernetes is the most widely used orchestration platform.

🔴 How are Docker and Kubernetes related?
Docker is used to build and package containers.
Kubernetes is used to orchestrate and manage those containers at scale.

🔴 Explain Kubernetes architecture.
Kubernetes consists of a control plane and worker nodes.

Control Plane:
kube-apiserver – Central API interface
etcd – Stores cluster state
kube-scheduler – Assigns Pods to nodes
controller-manager – Maintains desired state
Worker Node:
kubelet – Manages Pods on the node
kube-proxy – Handles networking and traffic routing
Container Runtime – Runs containers
🔴 What is etcd?
etcd is a distributed key-value store that stores all cluster configuration and state data. It is the single source of truth for Kubernetes.

🔴 What is kubelet?
kubelet is an agent running on each worker node that ensures containers described in Pod specs are running and healthy.

🔴 What is kube-proxy?
kube-proxy manages networking rules that allow Services to route traffic to the correct Pods using iptables or eBPF.

🔴 What is a Pod?
A Pod is the smallest deployable unit in Kubernetes.
It can contain one or more containers that share networking and storage.

🔴 What is a Deployment?
A Deployment manages stateless applications and provides:

Replica management
Rolling updates
Rollbacks
🔴 What is a StatefulSet?
StatefulSet is used for stateful applications such as databases.
It provides:

Stable Pod names
Persistent storage
Ordered deployment and scaling
🔴 ReplicaSet vs ReplicationController?
ReplicaSet is the modern replacement for ReplicationController.
It supports set-based selectors and is used internally by Deployments.

🔴 What is a Kubernetes Service?
A Service provides a stable IP and DNS name to expose a set of Pods and distribute traffic among them.

🔴 Types of Services?
ClusterIP – Internal access
NodePort – External access via node
LoadBalancer – Cloud load balancer
🔴 What is an Ingress?
Ingress manages external HTTP/HTTPS access and provides routing based on hostnames and paths using an Ingress Controller (NGINX, ALB, etc.).

🔴 ConfigMap vs Secret?
ConfigMap – Non-sensitive configuration
Secret – Sensitive data (base64 encoded, can be encrypted at rest)
🔴 PersistentVolume (PV) vs PersistentVolumeClaim (PVC)?
PV – Actual storage resource
PVC – Request for storage
🔴 How does Kubernetes perform self-healing?
Restarts failed containers
Reschedules Pods
Maintains desired replica count
🔴 How do you deploy a containerized application on a Kubernetes cluster? Walk me through the process.
First, the application is containerized using Docker.
The image is pushed to a container registry.
Then Kubernetes manifests (Deployment, Service, ConfigMap, etc.) are written and applied using kubectl.
Kubernetes schedules Pods, exposes them via Services, and continuously ensures the application is running as expected.

🔴 Describe Kubernetes Deployments and StatefulSets. What are the differences, and when would you use one over the other?
Deployments are used for stateless applications where Pods are interchangeable, such as web applications.
StatefulSets are used for stateful applications like databases, where stable Pod identity, storage, and ordering are required.
If data persistence and stable networking are important, StatefulSet is preferred.

🔴 How does Kubernetes handle load balancing for containerized applications?
Kubernetes uses Services to distribute traffic across multiple Pods.
Internally, kube-proxy routes traffic using iptables or eBPF.
For external access, Kubernetes supports NodePort, LoadBalancer, and Ingress-based load balancing.

🔴 What is a Kubernetes Namespace, and why would you use multiple namespaces in a cluster?
A Namespace is a logical partition within a cluster.
It is used to separate environments (dev, staging, prod), teams, or applications, and helps with access control, resource quotas, and organization.

🔴 Explain the concept of Kubernetes Services and how they enable network connectivity for Pods.
Pods are ephemeral and their IPs change frequently.
Services provide a stable IP and DNS name that routes traffic to matching Pods.
This allows applications to communicate reliably without knowing Pod details.

🔴 What is the role of a Kubernetes Ingress controller, and how does it work?
An Ingress controller manages external HTTP/HTTPS access to services.
It routes traffic based on hostnames and URL paths and often provides TLS termination, authentication, and rate limiting.

🔴 What is Kubernetes' role in auto-scaling, and how can you set up Horizontal Pod Autoscaling (HPA)?
Kubernetes supports auto-scaling through HPA, which adjusts the number of Pods based on metrics like CPU or memory usage.
It requires a metrics provider such as Metrics Server or Prometheus.

🔴 Describe Kubernetes rolling updates and canary deployments. When and why would you use each approach?
Rolling updates replace Pods gradually to avoid downtime.
Canary deployments release a new version to a small subset of users to validate changes before full rollout.
Canary is preferred when risk is high.

🔴 Explain Kubernetes' role in self-healing and how it handles container failures.
Kubernetes continuously monitors Pods and nodes.
If a container crashes, Kubernetes restarts it.
If a Pod fails, a new one is created automatically to maintain the desired state.

🔴 What are Kubernetes ConfigMaps and Secrets, and how do they differ?
ConfigMaps store non-sensitive configuration data such as URLs or feature flags.
Secrets store sensitive data like passwords and tokens and are base64 encoded.

🔴 How would you upgrade a Kubernetes cluster to a new version while minimizing downtime?
The control plane is upgraded first, followed by worker nodes in a rolling manner.
Applications continue running using multiple replicas, ensuring no downtime.

🔴 What is a Helm chart, and how does it simplify application deployment?
Helm is a Kubernetes package manager.
Helm charts bundle Kubernetes manifests into reusable, configurable packages, making deployments consistent and easy to manage.

🔴 How do you monitor a Kubernetes cluster and its workloads?
Monitoring is done using Prometheus for metrics, Grafana for dashboards, and tools like Fluentd or Loki for logs.
Alerts are configured to detect failures early.

🔴 Explain Kubernetes RBAC and how you would configure it.
RBAC controls access to cluster resources.
Roles define permissions, and RoleBindings associate them with users or service accounts, following the principle of least privilege.

🔴 Describe Immutable Infrastructure and its relation to Kubernetes.
Immutable Infrastructure means servers or containers are never modified after deployment.
In Kubernetes, updates are done by replacing Pods, not changing running ones.

🔴 How do you handle secrets rotation in Kubernetes, and why is it important?
Secrets are rotated using external secret managers and rolling Pod restarts.
This reduces security risks caused by leaked or expired credentials.

🔴 Discuss challenges and best practices for running stateful applications in Kubernetes.
Challenges include storage persistence, backups, and recovery.
Best practices involve StatefulSets, persistent volumes, and scheduled backups.

🔴 Share an example of a complex Kubernetes project you've worked on.
Example: Deploying a CI/CD-driven three-tier application with Ingress, HPA, monitoring, secret management, and rolling updates while maintaining high availability.

🔹 SCENARIO-BASED QUESTIONS
🔴 How would you design a highly available microservices architecture on Kubernetes?
By deploying multiple replicas, using Services and Ingress, enabling HPA, implementing readiness probes, and distributing Pods across nodes.

🔴 How would you perform a zero-downtime deployment?
By using rolling updates or blue-green deployments with health checks and controlled traffic switching.

🔴 How would you ensure data persistence and backups for a database?
Using StatefulSets with persistent volumes and automated backup jobs or snapshots.

🔴 How would you implement a multi-cluster Kubernetes strategy?
Using GitOps, centralized CI/CD pipelines, shared monitoring, and service mesh for cross-cluster communication.

🔴 How would you diagnose high resource usage in a Pod?
By analyzing metrics, logs, resource limits, node pressure, and application behavior.

🔴 How would you enable secure pod-to-pod communication?
By defining Network Policies that allow only required traffic paths.

🔴 How would you configure HPA for variable traffic?
By setting CPU or memory thresholds along with minimum and maximum Pod limits.

🔴 Describe a GitOps workflow for Kubernetes.
All configuration changes are pushed to Git.
A GitOps tool automatically syncs the cluster with the repository state.

🔴 How would you optimize resource utilization in Kubernetes?
By right-sizing requests and limits, enabling autoscaling, and removing unused workloads.

🔴 How would you ensure consistency in hybrid cloud Kubernetes?
By standardizing configurations, using GitOps, and maintaining common tooling across clusters.

🔴 How would you troubleshoot a Kubernetes performance issue?
By checking metrics, logs, events, node health, and application dependencies step by step.

🛠️ TROUBLESHOOTING
🔴 Pod is in CrashLoopBackOff. How do you troubleshoot?
CrashLoopBackOff means the container is crashing repeatedly.

Troubleshooting steps:

Check pod details and events using kubectl describe pod
Check application logs using kubectl logs
Verify environment variables, ConfigMaps, and Secrets
Check resource requests and limits (CPU / memory)
Validate container command, image, and startup logic
Common causes:

Application crash
Missing configuration
Incorrect command
Insufficient resources
🔴 Pod is stuck in Pending state. What could be the reasons?
Common reasons include:

Insufficient CPU or memory on nodes
PVC not bound to a PV
Node selector, affinity, or taints blocking scheduling
Image pull issues
Use:

kubectl describe pod
kubectl get nodes
🔴 Application is running but not accessible. How do you debug?
Steps:

Check Pod status
Verify Service selector matches Pod labels
Check Service type (ClusterIP / NodePort / LoadBalancer)
Validate Ingress rules and controller
Test internal connectivity using kubectl exec
🔴 Node is NotReady. What will you do?
Possible causes:

Kubelet stopped
Disk or memory pressure
Network issues
Steps:

Check node status and conditions
Restart kubelet service
Check system logs
Verify node connectivity with control plane
🔴 ImagePullBackOff error. How do you fix it?
Causes:

Incorrect image name or tag
Private registry authentication failure
Network issues
Fix:

Verify image name
Configure imagePullSecrets
Test registry connectivity
🔴 High CPU / Memory usage affecting other Pods. What will you do?
Steps:

Check metrics using Prometheus or kubectl top
Verify resource requests and limits
Tune application performance
Apply HPA if required
Use PodDisruptionBudget for stability
🔴 How do you debug DNS issues inside a cluster?
Steps:

Exec into Pod and test DNS resolution
Verify CoreDNS Pods
Check Service and namespace DNS names
Inspect CoreDNS logs
🚀 ADVANCED KUBERNETES TOPICS
🔴 What are resource requests and limits, and why are they important?
Requests guarantee minimum resources
Limits cap maximum usage
They help:

Prevent resource starvation
Enable efficient scheduling
Improve cluster stability
🔴 What are liveness, readiness, and startup probes?
Liveness Probe – Restarts container if app is unhealthy
Readiness Probe – Controls traffic routing
Startup Probe – Used for slow-starting applications
🔴 What are taints and tolerations? Give a real use case.
Taints prevent Pods from being scheduled on nodes.
Tolerations allow specific Pods to run on those nodes.

Use case:

Dedicated nodes for databases
Isolating GPU or critical workloads
🔴 What is PodDisruptionBudget (PDB)?
PDB ensures a minimum number of Pods remain available during:

Node maintenance
Cluster upgrades
Voluntary disruptions
🔴 What is Kubernetes autoscaling hierarchy?
HPA – Scales Pods
VPA – Adjusts resource requests
Cluster Autoscaler – Scales nodes
🔴 Explain GitOps in Kubernetes.
GitOps uses Git as the single source of truth.

Workflow:

Change pushed to Git
GitOps tool (ArgoCD / Flux) detects change
Cluster state is synced automatically
Benefits:

Auditable
Consistent
Easy rollback
🔴 What is Immutable Infrastructure in Kubernetes?
Infrastructure is never modified in-place.
Instead, new Pods replace old ones during updates.

This ensures:

Predictability
Easy rollback
Reduced configuration drift
🔴 What is CNI and why is it important?
CNI (Container Network Interface) manages Pod networking.

Examples:

Calico
Cilium
Flannel
It enables:

Pod-to-pod communication
Network policies
Security isolation
🔴 What are Network Policies?
Network Policies control traffic between Pods.

They help:

Restrict unauthorized access
Implement zero-trust networking
Secure microservices communication
🔴 How do you upgrade a Kubernetes cluster safely?
Steps:

Backup etcd
Upgrade control plane
Drain worker nodes one by one
Upgrade kubelet and kube-proxy
Validate workloads
🔴 How do you design Kubernetes for high availability?
Multiple control plane nodes
Multiple worker nodes
Replicas across nodes
Load balancers
Proper health checks
🔴 How do you design disaster recovery for Kubernetes?
Persistent volume backups
Multi-region or multi-cluster setup
Infrastructure as Code
Automated restore testing
