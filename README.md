# devcontainer
DevContainer template: ubuntu + utilities, rust, java, nodejs, docker in docker, kubectl, helm, minikube

## VSCode extension
[Developing inside a Container](https://code.visualstudio.com/docs/devcontainers/containers)

## Open project in remote DevContainer
[Open a folder on a remote SSH host in DevContainer](https://code.visualstudio.com/docs/devcontainers/containers#_open-a-folder-on-a-remote-ssh-host-in-a-container)

## Kubernetes API port binding for minikube
```
minikube start --ports=8443:8443
```

## kubectl configuration in remote host for VSCode Kubernetes extension
1) get kube config in *remote DevContainer* with replaced server config
```
kubectl config view --flatten=true | sed -e 's/server: https:\/\/.*/server: https:\/\/localhost:8443/g'
```

2) copy kubectl config to *remote host*
```
mkdir ~/.kube
cat << EOF > ~/.kube/config
// kubectl config from previous command 
EOF
```
1) open minikube in you *host* by using "Set KubeConfig" menu in VSCode Kubernetes extension

## kubectl configuration in *host* for OpenLens

Add Clusters from Kubeconfig by using configuration from *remote DevContainer*
```
kubectl config view --flatten=true | sed -e 's/server: https:\/\/.*/server: https:\/\/localhost:8443/g'
```

