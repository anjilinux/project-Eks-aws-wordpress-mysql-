# Eks-project

Launching an #infrastructure with :
1) wordpress
2) mysql
3) prometheus
4) grafana
5) helm
6) tiller
7) eks, #efs on top of our public Amazon Web Services (AWS) cloud
And I also showed u some concepts of pvc, pv, sc, secret box of kubernetes part and why we prefer to efs than ebs.

> In my first video I showed you how to create cluster and Elb with eks on aws cloud
https://www.youtube.com/watch?v=MWlvEWAe63o&t=1201s


>This is my second video on eks ---> I showed u multiple intrications of services to launch a whole architecture
https://youtu.be/TN-bUB9Sa7M

Also see my linkedin post and connect me for any other queries:
https://www.linkedin.com/posts/v-roshan-kumar-patro-6222741a2_aws-eks-part-2-efs-helm-tiller-activity-6689562525857665024-iiNR


Guys this is my second video on eks service which includes the things above written in head part plus we will do launch a wordpress+mysql infrastructure on top of everything using these services and store the data in mysql database server.
.-----Wordpress is a content delivery system where u can post ur blogs.
We are going to cover also some parts of kubernetes like
  ...Pvc(Persistent Volume Claim), Pv(Physical volume), Sc (Storage class), Deployments, Secret Box

Intro: (0.00)
EFS,Pvc,pv,sc: (1:45)     
Main: (11:51)  
Helm,prometheus,graphana: (26:07)
Ending: (30:20)

All my codes are there in this github link -- https://github.com/varanasiroshan2001...
For Helm the codes are--
1) helm repo add incubator https://kubernetes-charts-incubator.s...
2) kubectl -n kube-system create serviceaccount tiller 
3) kubectl create clusterrolebinding tiller --clusterrole cluster-admin --serviceaccount=kube-system:tiller
4) helm init --service-account tiller --upgrade

For Prometheus codes are:
1) helm install stable/prometheus   --namespace prometheus   --set alertmanager.persistentVolume.storageClass="gp2"   --set server.persistentVolume.storageClass="gp2"
2) kubectl get svc -n prometheus
3) kubectl -n prometheus port-forward svc/intentional-arachnid-prometheus-server 8888:80

For Grafana:--
1)  helm install stable/grafana  --namespace grafana     --set persistence.storageClassName="gp2" --set adminPassword='GrafanaAdm!n'    --set datasources."datasources\.yaml".apiVersion=1     --set datasources."datasources\.yaml".datasources[0].name=Prometheus   --set datasources."datasources\.yaml".datasources[0].type=prometheus    --set datasources."datasources\.yaml".datasources[0].url=http://prometheus-server.prometheus.s...   --set datasources."datasources\.yaml".datasources[0].access=proxy     --set datasources."datasources\.yaml".datasources[0].isDefault=true  --set service.type=LoadBalancer
2) kubectl get  secret  worn-bronco-grafana   --namespace  grafana  -o yaml

First u need to setup prometheus then grafana
like share subscribe guys new video will be out soon for u guys😍😍🤩
