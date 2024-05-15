# python-web-server
python web server with responce 200 OK
Web server inside docker file

terraform apply -var="iam_profile=mfa" -var="region=eu-central-1"

aws eks --region eu-central-1 update-kubeconfig --name bukhenko --profile mfa

kubectl config use-context arn:aws:eks:eu-central-1:105742781415:cluster/bukhenko


argocd app create app --repo https://github.com/AlexRob2201/python-web-server.git --path kubernetes --dest-server https://kubernetes.default.svc --dest-namespace app
argocd app set app --sync-policy automated
argocd app set app --self-heal

argocd app set app --self-heal
spec:
  syncPolicy:
    automated:
      selfHeal: true
