# AUTH CAN I EXAMPLES:


# FUNKY JSONPATH EXAMPLES:
kubectl get apiservices.apiregistration.k8s.io -o=jsonpath='{range .items[?(@.spec.service)]}{.metadata.name}{"\n"}{end}'

# RBAC Impersonation
kubectl auth can-i get configmap/default-values -n test-ns --as=adminuser --as-group=system:masters
- the groups that a user belongs to is not known to the API server
- `userextras/key-name` with `resourceNames=value-name` to contstrain vaules someone can impersonate.
- system:authenticated is assumed

# YAML oneliners
cat <<EOF | kubectl apply -f -
apiVersion: v1
kind: Pod
metadata:
  name: busybox-sleep
spec:
  containers:
  - name: busybox
    image: busybox:1.28
    args:
    - sleep
    - "1000000"
EOF

# File creation
cat <<'EOF' > file
  SCHTUFF
EOF

# one line run
kubectl run dnsutils --rm -i --tty --image="registry.k8s.io/e2e-test-images/jessie-dnsutils:1.3" -- bash

# delete "Completed" pods
kubectl delete pods -A --field-selector=status.phase==Succeeded

# one line hacky filter
kubectl get pods | grep 'UnexpectedAdmissionError' | awk '{print $1}' | xargs kubectl delete pod

# dns
kubectl run dnsutils --restart=Never --rm -i --tty --image k8s.gcr.io/e2e-test-images/jessie-dnsutils:1.3 --overrides='{"apiVersion": "v1", "spec": {"nodeSelector": {"cloud.google.com/gke-nodepool": "h100"}, "tolerations": [{"key": "nvidia.com/gpu", "operator": "Equal", "value": "present", "effect": "NoSchedule"}], "hostNetwork": true, "dnsPolicy": "ClusterFirstWithHostNet"}}' -- /bin/bash
