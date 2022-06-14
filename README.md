# Task 2 - Cloud Deployment

Branch Automation: YES

    A push to main branch will trigger a workflow using git-hubaction using .github/workflows/deploy.yml
    it will checkout the source code, packages it and deploys to AWS Beanstalk environment

How to Use

Requires:
      
      Git - install guide here: https://github.com/git-guides/install-git

Assumes:
      
      AWS access and secret key has been stored in Github Secrets AWS_ACCESS_KEY_ID | AWS_SECRET_ACCESS_KEY

Steps:

1. clone the repository and switch directory  
         
         $ git clone -b main https://github.com/ryancomia/sc-exercise.git
         $ cd /sc-exercise            

2 Modify or update as necessary then 
         
         $ git add . / 
         $ git commit -m "my_changes_etc"

3. Update the build.yml application_name / environment_name based from the Elastic Beanstalk env

4. Push it back to branch main
 
        $ git push
        
          - github workflow will then trigger the actions to deploy it to AWS

5. Wait until the action succeeds. it takes 10-15mins for the environment update, afterwhich you can check the app by browsing

        http://smartcowdevopsapp-env.eba-rwbfpxum.ap-southeast-1.elasticbeanstalk.com/
        
        
note: the example uses elastic-beanstalk endpoint. in a Production setup, this needs to be CNAME'd of an actual URL. otherwise each EB app generation will create a different beanstalk endpoint
