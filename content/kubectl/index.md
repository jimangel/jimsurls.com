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
