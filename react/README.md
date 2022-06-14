# Task 3 - Minikube/Kubernetes - Deployment

# # Note: This branch holds the automation to create Docker Images from the Source Code # #

How to Use

# Part 1 - build image and push to Docker CR

Requires:
      a. Git - install guide here: https://github.com/git-guides/install-git

Steps:
1. From your local env clone this repo  
         
         $ git clone https://github.com/ryancomia/sc-exercise.git

2. Switch to feature/kubernets branch 
       
         $ git checkout -b feature/kubernetes

3. Modify or update as necessary then 
         
         $ git add . / 
         $ git commit -m "my_changes_etc"

4. Push it back to feature/kubernetes 
 
        $ git push


  the github workflow will then trigger the actions to build and push the new image from the source code

5. Login to Docker hub to see the product images



# Part 2 - deploy to minikube

Requires:
       a. Minikube - install guide here: https://minikube.sigs.k8s.io/docs/start/
       b. Kubectl - install guide here: https://kubernetes.io/docs/tasks/tools/
  
Steps:
1. Before we begin lets get the minikube exposed IP 
        
        $ kubectl cluster-info
        
2. Add an entry to host file 
 
        $ sudo vi /etc/hosts 
          add entry MINI_KUBE_IP smartcow.local
      
3. From the same source code on Part 1. switch directory 

        $ cd ./k8s

4. Create a Namespace for the app 
        
        $ kubectl create ns
         Optional: Switch to the crated ns context using 
        $ kubectl config set-context --current --namespace=MY_NS_NAME
        
5. Deploy using
        
        $ kubetcl apply -f .
        
9. To verify the deployment and services

        $ kubectl get pods -o wide
        $ kubectl get services
        $ kubectl get ingress
        

Finally to verify if the app works, go over to your browser: smartcow.local/


