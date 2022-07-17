# DevOps Challenges
# Deploy GitHub, Jenkins, Docker, ECR, EKS and ELB with CaC


1. First, Fork the requirement repo - https://github.com/wariyakunatorn/azt_devops_challenges.git 
      * Prepare and edit to work well when creating docker image like ./app/html in Dockerfile

2. Second, add, commit and push to my own GitHub
      * git add app Dockerfile Jenkinsfile
      * git checkout -b 6branch
git remote add project-anz https://github.com/komoelwinaung/project-anz.git
git commit -m "this is new branch-6"
git push --set-upstream project-anz 6branch

3. Once RDS is ready, deploy a new pod for WordPress site 
    * kubectl apply -f wordpress-site.yaml
    * Expose your service with ELB - kubectl expose deployment/wordpress --port 80 --target-port 80 --name wordpress-service --type LoadBalancer

After that, browse your ELB url, configure the required settings in WordPress dashboard for your website.
Enjoy!!
