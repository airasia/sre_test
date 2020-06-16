# Cloud SRE Test

## Conditions for the test

- terraform 0.12.X
- GCP

### Current configuration

#### Application for web/mobile chat using WebSockets

![](/Images/OnPrem.png)

### Resource

1. DNS Server with zone for app.com
2. Nginx A Server
   1. Reverse Proxy
   2. URL redirect based on URI
   3. Listening on TCP/IP port 80
   4. redirect https://app.com/ to Nginx B Web Server
   5. redirect https://app.com/api/ to Node.js server
3. Nginx B Web Server serving static webpages "index.html" and CSS
4. Node.js service for backend processing
5. Redis keeps clients connectivity state
6. MySql keeps user accounts

## Objective

- migrate application from OnPrem Data Centre to GCP
  - Application on GCP should be Highly Available
  - Application on GCP should be Scalable
  - Application on GCP should be Highly Fault Tolerant
  - Application logs and stastics must be visible in ELK/EFK stack
- Write scripts and yaml files, in order to run this application on a Kubernetes cluster, i.e. Helm charts or Kubernetes manifests.
- Add security as a pipeline in your deployment pipeline. i.e. SAST, DAST.
- You can use any public code to develop application and deploy it on Kubernetes cluster. Need to make sure about using ENV variables in 12Factor style, create Dockerfile.
- You have to write documentation and/or instructions about what you have done. This documents must detail steps for other DevOps to understand how to deploy this application and maintain it.
- Do not make your code public.

### Architect and Design new application diagram for Cloud Native Implementation

- Present Diagram in Draw.io
- Present few options on architecture and design
- From multiple options use one in terraform code
- Describe migration plan for huge database which maybe on diffrent engine i.e. MSSQL required to migrate to Cloud SQL
- Describe how can you make whole project secure. Including Infra, System and Application.

### Write Infrastructure as Code in terraform 0.12

- use remote state
- terraform code should be promotable Dev > Staging > Production
- terraform code should be managed in source control system

