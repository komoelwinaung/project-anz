# DevOps Challenges
# Deploy GitHub, Jenkins, Docker, ECR, EKS and ELB with CaC

1. First, Fork the requirement repo - https://github.com/wariyakunatorn/azt_devops_challenges.git 
      * Prepare and edit to work well when creating docker image like ./app/html in Dockerfile

2. Second, put on these required files on my own Github: https://github.com/komoelwinaung/project-anz.git

3. Third, Setup and configure automatic pipeline with Jenkins. Also Docker Service is running well in Jenkins host. Details explanation is my attached Powerpoint.

4. Fourth, update index.html and add, commit and push to my own GitHub
      * git add app Dockerfile Jenkinsfile
      * git checkout -b 6branch
      * git remote add project-anz https://github.com/komoelwinaung/project-anz.git
      * git commit -m "this is new branch-6"
      * git push --set-upstream project-anz 6branch

5. Fifth, create and merge the pull request to master branch by engineer and that will be automatically done by Jenkins and push the created image to ECR. Also step-by-step are in Powerpoint.

6. Sixth, configure aws cli in my Ubuntu and create the EKS cluster with yaml file and wait a couple of minutes.
       *  eksctl create cluster -f cluster-anz.yaml
       * aws eks update-kubeconfig --name cluster-anz --region ap-southeast-1
       * kubectl get all
       * kubectl apply -f nginx-anz.yaml
       * kubectl expose deployment/nginx --port 8000 --name nginx-service --type LoadBalancer
       * kubectl get services nginx-service
    After that, we can browse the ELB url and that will be fine. Result screenshot is in Powerpoint.


