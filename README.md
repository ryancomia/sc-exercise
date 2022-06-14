# Task 3 - minikube/kubernetes - deployment

Branch Automation: YES

      A push to feature/kubernetes branch will trigger a workflow using github-actions using .github/workflows/build.yml
      It checks-out the source code, build coresponding images,and pushes it to docker hub registry

How to Use

# Part 1 - build image and push to Docker Hub

Requires:
      
      Git - install guide here: https://github.com/git-guides/install-git
      Docker Access Token (for github-actions)
      Docker Hub Login - install guide here: https://hub.docker.com/

Assumes:
      
      Docker DOCKER_USER | DOCKER_PASS has been stored into Github Secrets

Steps:
1. clone the repository and switch directory  
         
       $ git clone -b feature/kubernetes https://github.com/ryancomia/sc-exercise.git
       $ cd /sc-exercise            

2 Modify or update as necessary then 
         
       $ git add . / 
       $ git commit -m "my_changes_etc"

3. Push it back to branch feature/kubernetes 
 
       $ git push
       
       - github workflow will then trigger the actions to build and push the new image from the source code

5. Login to Docker hub to see the product images



# Part 2 - deploy to minikube

Requires:
      
      Minikube - install guide here: https://minikube.sigs.k8s.io/docs/start/
      Kubectl - install guide here: https://kubernetes.io/docs/tasks/tools/
  
Steps:
1. Before we begin lets get the minikube exposed IP 
        
        $ kubectl cluster-info
        
2. Add an entry to host file 
 
        $ sudo sed -i "mini_kube_ip  smartcow.local" /etc/hosts
      
3. From the same source code on Part 1. switch directory 

        $ cd ./k8s

4. Create a Namespace and set context
        
        $ kubectl create ns         
        $ kubectl config set-context --current --namespace=MY_NS_NAME
        
5. Deploy using
        
        $ kubetcl apply -f .
        
9. To verify the deployment and services

        $ kubectl get pods -o wide
        $ kubectl get services
        $ kubectl get ingress
        

Finally to verify the app. head over to your browser: 

         smartcow.local/
