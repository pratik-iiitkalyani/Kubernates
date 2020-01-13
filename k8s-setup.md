Setup Kubernetes (K8s) Cluster on AWS

    1. Create Ubuntu EC2 instance
    
    2. install AWSCLI
        
        -> curl https://s3.amazonaws.com/aws-cli/awscli-bundle.zip -o awscli-bundle.zip
        -> apt install unzip python
        * (if it gives error like IP Not found - run # sudo apt-get update
            then run above command)
        -> unzip awscli-bundle.zip
        #sudo apt-get install unzip - if you dont have unzip in your system
        -> ls -l (run to see awscli-bundle is unzipped or not)
        -> ./awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws
        
        -> aws (run to see aws cli is installed or not)
        
    
     3. install kubectl (Kubectl is a command line interface for running commands against Kubernetes clusters)
     
        -> curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-                   release/release/stable.txt)/bin/linux/amd64/kubectl
          chmod +x ./kubectl
          sudo mv ./kubectl /usr/local/bin/kubectl
          
          
     4. Create an IAM user/role with Route53, EC2, IAM and S3 full access
     
     5. Attach IAM role to ubuntu server
        
        Note: If you create IAM user with programmatic access then provide Access keys.
        -> aws s3 ls (to see your bucket and verify that given role have access to s3 or not)
        -> aws configure
        (* don't provide Access Key ID and Secret Access Key because currently we are using role
         * provide your region and output leave as default)
         
         *Note - if your region is us-east-1d - provide region as us-east-1
         
     6. Install kops on ubuntu instance 
     
        -> curl -LO https://github.com/kubernetes/kops/releases/download/$(curl -s                                                                https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag_name | cut -d '"' -f 4)/kops-linux-amd64
         chmod +x kops-linux-amd64
         sudo mv kops-linux-amd64 /usr/local/bin/kops
         
     7. Create a Route53 private hosted zone
        ( * we can create Public hosted zone if you have a domain)

     8. create an S3 bucket
     
        -> aws s3 mb s3://dev.k8s.pratik.in
        
     9. Expose environment variable (expose our S3 Bucket)
     
        -> export KOPS_STATE_STORE=s3://dev.k8s.pratik.in
        
     10. Create ssh keys before creating cluster
        
        -> ssh-keygen
        
     11. 
        
        
