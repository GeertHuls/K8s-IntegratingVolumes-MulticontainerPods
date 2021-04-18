FROM alpine
LABEL maintainer="Nigel Poulton nigelpoulton@hotmail.com @nigelpoulton"

# Install curl and latest version of kubectl
RUN apk update && \
  apk add curl && \
  curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl && \
  chmod +x ./kubectl && \
  mv ./kubectl /usr/local/bin/kubectl

# Copy main app file
COPY ambassador.sh /ambassador.sh

RUN chmod +x /ambassador.sh

# Set app to run when container is started
ENTRYPOINT /ambassador.sh

# View config
# kubectl config view
# Cluster info
# kubectl cluster-info
# Config located at: C:\Users\<username>\.kube\config

# View current context
# kubectl config current-context
# View pod yaml
# kubectl get pods -o yaml
# List secret of token
# kubectl get secret default-token-dmcf6
# kubectl describe secret default-token-dmcf6

# Show full yaml spec of service account
# kubectl get sa default -o yaml

# Service account secrets are injected into every pod:
# kubectl exec -it <podname> bash
# > ls /var/run/secrets/kubernetes.io/serviceaccount/
