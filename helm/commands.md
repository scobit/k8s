### HELM REPO

#### list local repo
helm repo list

#### delete local repo
helm repo remove RepoName

#### update local repos
helm repo update


#### pull chart
helm pull [chart URL | repo/chartname]

#### pull chart and untar it in current directory
helm pull [chart URL | repo/chartname] --untar


#### helm install from local chart
helm install -f values.yaml MyChartName .

#### helm upgrade
helm upgrade MyChartName --install . -f values.yaml --namespace NameSpaceName --wait

#### search repo 
helm search repo | grep ...


#### create package
helm package PathToChart


helm repo add --username ${HELM_REGISTRY_USER} --password ${HELM_REGISTRY_PASSWORD} ${HELM_REPO_NAME} ${HELM_REPO_URL}
helm repo update
helm fetch ${HELM_REPO_NAME}/postgresql --version 11.9.11 --untar --untardir ./



k create ns gatus

helm inspect values gatus/gatus

helm delete gatus

helm upgrade gatus --install gatus/gatus -f values.yaml --namespace gatus


kubectl create configmap config --from-file=config.yaml -n gatus --dry-run -o yaml | kubectl apply -f -
