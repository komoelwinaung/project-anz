# DevOps Challenges
# Deploy GitHub, Jenkins, Docker, EC2, ECR, EKS and ELB with CaC

I've implemented and accomplished the following scenario for the required systems, business applications to state of the art organizations.

1. Fork the requirement repo - https://github.com/wariyakunatorn/azt_devops_challenges.git 
    - Prepare and edit the config to work when creating docker image like ./app/html in Dockerfile

2. Put on these required files on my own Github: https://github.com/komoelwinaung/project-anz.git

3. Setup and configure automatic pipeline with Jenkins. Also Docker Service is running well in Jenkins host. Details explanation in my attached Powerpoint.

4. Update **index.html** and add, commit and push to my own GitHub
    - git add app Dockerfile Jenkinsfile
    - git checkout -b 6branch
    - git remote add project-anz https://github.com/komoelwinaung/project-anz.git
    - git commit -m "this is new branch-6"
    - git push --set-upstream project-anz 6branch

5. Create and merge the **pull request** to **master branch** by engineer and that will be automatically triggered by Jenkins pipeline and push the created image to ECR. Also step-by-step are in Powerpoint.

6. Configure aws cli in my Ubuntu with VS Code and create the EKS cluster with yaml file and wait for a couple of minutes.
    - eksctl create cluster -f cluster-anz.yaml
    - aws eks update-kubeconfig --name cluster-anz --region ap-southeast-1
    - kubectl get all
    - kubectl apply -f nginx-anz.yaml
    - kubectl expose deployment/nginx --port 8000 --name nginx-service --type LoadBalancer
    - kubectl get services nginx-service
       
7. BONUS: 1 We can browse the ELB url and that will be fine. Result screenshots are in Powerpoint.

8. BONUS: 2 Prepare and install Istio system in EKS, deploy sample BookApp and expose the application via ELB. Also screenshots are in Powerpoint. Some Commands are:
    - kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml
    - kubectl exec "$(kubectl get pod -l app=ratings -o jsonpath='{.items[0].metadata.name}')" -c ratings -- curl -sS productpage:9080/productpage | grep -o "<title>.*</title>
    - kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml
    - kubectl get gateway
    - kubectl -n istio-system get svc
          
Deployment of WordPress & RDS was done in my GitHub tutorial - https://github.com/komoelwinaung/wordpress_eks_with_rds and will need to integrate WordPress/Istio scenario.

Thank you.


## Some Tutorials of my GitHub

My tutorials and the finished results related with this scenarios:
 - https://github.com/komoelwinaung/sample-java-deployment-jenkins-sonartube.git 
 - https://github.com/komoelwinaung/installation-prometheus-grafana--monitor-eks-cluster.git 
 - https://github.com/komoelwinaung/ecs-blue-green-deployment.git

