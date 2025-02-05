# demo-policygenerator

This repo is designed to provide a RHACM Policy Generator code example.

This PolicyGenerator definition will achieve 2 configuration policies:
 - **openshift-gitops-installed**: The goal of the first one is to inform if the OpenShift GitOps operator is installed on managed clusters. 
 - **kubeadmin-removed**: The goal of this second policy is to inform if the kubeadmin user is removed from managed clusters.

Both policies are **informative**. If you want to either enforce the OpenShift GitOps operator installation or the kubeadmin user removal, just access the RHACM Governance view, click on the selected policy three dots button (...) and select "Enforce".

Note: **Be cautious**, just enforce the **kubeadmin-removed** policy if you know what you're doing as this configuration may not be undone and it might cause fatal errors. DO NOT USE THIS IN PRODUCTION.
 
## Pre-requesites: ##

- A supported version of RHACM.
- A supported version of OpenShift GitOps integrated into RHACM.
- PolicyGenerator plugin enabled in ArgoCD - [RHACM docs](https://docs.redhat.com/en/documentation/red_hat_advanced_cluster_management_for_kubernetes/2.12/html/gitops/gitops-overview#gitops-policy-definitions)


## Demo ##
When you're ready, deploy an ApplicationSet in RHACM using this repo url. 
Select **branch: main** and **path: dir**.
In just a few moments, the policies should be created under the governance menu.
![Applications Topology view](https://github.com/levenhagen/demo-policygenerator/blob/main/img/image.png?raw=true)

