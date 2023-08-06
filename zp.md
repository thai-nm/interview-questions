1. How to access to a private cluster?
   - Execute kubectl from a bastion host
   - If it is a VM from GCP, we can still setup a SSH forwarding connection with gcloud command 

2. Explain StatefulSet in a Kubernetes cluster?
   - Pod is deployed in order: each pod will have an index and a hash number represent for a version 
   - Stable network identifier: each pod will have a stable fully qualified domain name
   - Stable storage: ensure that data for each pod is persistent even when pod is restarted or recheduled.

3. Which service have you deployed as StatefulSet in a cluster?


4. How did you deploy your application as well as services? Did you use any GitOps tools? What are the workflows?
- For the latest project:
  - For application deployment:
    - Step 1: Gather environment information such as cluster name, cluster namespaces, envinronment variables, secrets. Then feed into a YAML template generator to generate a YAML file containing all the configurations above.
    - Step 2: Feed the YAML above to a Terragrunt template generator to generate Terragrunt files for the above configurations. Terragrunt is now responsible for managing resources on over all namespaces.
    - Step 3: Terragrunt will trigger and provide input values into a Terraform module which is using Kubernetes provider to create Kubernetes resources. These resources are deployed as our microservices.
  - For third party services:
    - If the third party service is supposed to run on Kubernetes, then it will be deployed in a pretty same way as the application above.
    - If the third party service is supposed to run on a VM: ???

5. Explain the following concepts: Terraform states and modules
- Terraform state: 
  - Contains state of the infrastructure. 
  - Could be a local state or a remote state.
- Terraform module:
  - A group of resources for a Terraform provider, usually accepts input values to interacts with the resources.

6. Explain about Logging and Monitoring stacks. Prefer self-host solution such as ELK, Prometheus than managed service.
- Logging:
  - Non-prod environments: 
    - Cloud Logging
  - Prod environments:
    - Cloud Logging
    - Datadog
- Monitoring:
  - Non-prod environments:
    - Cloud Monitoring
    - Datadog
  - Prod environments:
    - Cloud Monitoring
    - Datadog
- For GCP services:
  - Use Terraform module to configure and interact with GCP resources, such as configuring log sink, log router and log folder, ...
- For Datadog:
  - Use Terraform module to setup, configure and interact with Datadog provider resources such as monitors, dashboards, integrations, alerts, ...

8. Explain about the Logging components and its workflow?

9.  How did you store Terraform backend state?
- On a remote bucket with version control enabled.

10.  What is the solution for storing long-live logs, about 7-8 years?
- For AWS, it can be an Amazon Glacier S3 bucket.
- For GCP, it can be an Archive Storage class bucket.

4.  Did your Grafana use any data sources other then Prometheus?
5.  How did you setup and configure Loki?
6.  What is your alert solution? Have you ever used Pagerduty?
7.  Explain about the Datadog configuration and setup?
8.  How did you monitor the status of your infras and application?
9.  How did you setup your Kubernetes cluster and deploy applications? What about patching operations for the cluster?
10. What is your experience with Python?
11. How do you apply terraform for different environments and multiple resources?
12. if you have a resource created manually, how do you replicate it into terraform state?
13. Explain about GitOps experience.