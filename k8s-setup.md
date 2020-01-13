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
