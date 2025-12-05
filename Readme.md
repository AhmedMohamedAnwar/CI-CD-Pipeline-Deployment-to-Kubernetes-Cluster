# CI/CD Project "Deployment To Kubernetes Cluster KinD"

## Overview
This project implements a complete CI/CD workflow using **Jenkins** running as a pod inside a **Kubernetes cluster**.  
The CI process integrates **Trivy** for security scanning, while the CD process deploys directly to the same Kubernetes environment.

When a developer pushes code, Jenkins automatically scans the repository.  
The repository contains:
- **main** → Production branch (fully scanned)
- **test** → Testing environment branch (fully scanned)
- **development** → Development branch (not scanned)

Once the pipeline is triggered, Jenkins performs the following:
1. Fetches the latest code from the selected branch  
2. Runs a **Trivy security scan**  
3. If the branch is `main`, Jenkins proceeds with **applying the Kubernetes deployment** to update production  
4. For other branches, validations and scan results are produced without applying production changes

In the `main` branch, whenever changes occur in the application, the pipeline triggers the **build** and **deploy** stages automatically.
It will not build or deploy if there is changes in kubernetes or Readme file but it exists for trivy scann

---

## Architecture
<!-- ![Architecture Diagram](./architecture.png) -->

---

## Output
<!-- The pipeline outputs:
- Trivy vulnerability scan report  
- Build logs and validation results  
- Deployment status (if triggered from main)  
- Updated Kubernetes application running in the cluster -->
