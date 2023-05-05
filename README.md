# demo-policygenerator

This repo is designed to provide a RHACM Policy Generator code example.

This PolicyGenerator definition will achieve 2 configuration policies:
 - **openshift-gitops-installed**: The goal of the first one is to inform if the OpenShift GitOps operator is installed on managed clusters. 
 - **kubeadmin-removed**: The goal of this second policy is to inform if the kubeadmin user is removed from managed clusters.

Both policies are informative. If you want to either enforce the OpenShift GitOps operator installation or the kubeadmin user removal, just access the RHACM Governance view, click on the selected policy three dots button (...) and select "Enforce".

Note: Be cautious, just enforce the **kubeadmin-removed** policy if you know what you're doing as this configuration may not be undone.
 
__Pre-requesites:__

ClusterRoleBinding open-cluster-management:subscription-admin must be applied to your user or kube:admin/system:admin users.

```
cat << EOF | kubectl apply -f -
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: open-cluster-management:subscription-admin
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: open-cluster-management:subscription-admin
subjects:
- apiGroup: rbac.authorization.k8s.io
  kind: User
  name: kube:admin
- apiGroup: rbac.authorization.k8s.io
  kind: User
  name: system:admin
EOF
```

__Demo__
When you're ready, deploy an app in RHACM using this repo url, and the policies should be created in a few moments under the governance menu.
![Applications Topology view](https://github.com/levenhagen/demo-policygenerator/blob/main/img/image.jpg?raw=true)

