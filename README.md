Create a cluster in Amazon EKS and install kubectl
Step 1: Sign in to the AWS Management Console
1. Click on the Open Console button, and you will get redirected to AWS Console in a new browser tab

Task 2.  Create an EKS Cluster
1. Make sure you want to create in which Region.
2. Navigate to Elastic Kubernetes Service by clicking on the Services menu available under the Containers section.
3. Click on Add Cluster and then click on Create
4. Enter the cluster name as you wish but I have used Whiz
5. Keep the Kubernetes version as the default
6. For Specifying networking, Select the Default VPC
7. By default, all the subnets are selected Remove the subnets from us-east-1e and us-east-1f and select the default Security group present for the VPC.
8. NOTE: Make sure that only 4 subnets are selected for us-east-1a, us-east-1b, us-east-1c, and us-east-1d
9. Cluster endpoint Access: Public
10. Keep other options as default and click on the Next.
11. For Configure logging, Keep other options as default, and click on the Next.
12. Review and create, Click on the Create button.
13. Note: Cluster creation will take about 10-15 minutes.
14. Cluster is created now.

Task 3: Create an Environment in CloudShell
1. Make sure you are in the N.Virginia Region.

2. Click on the Arrow icon (Cloud Shell) on the top right AWS menu bar.

3. A new tab in your browser opens and if you see a welcome message to cloud shell then click on the Close button in that message.

4. You will see a creating environment message on the screen.
5. Wait for a few minutes to complete the environment creation. Once the environment is created, You are ready to use the terminal.

Task 4: Install Kubectl on AWS CloudShell
1. Once the environment is ready on CloudShell, Download the Amazon EKS vended kubectl binary for your cluster's Kubernetes version from Amazon S3. To do so, run the following command:
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.18.9/2020-11-02/bin/linux/amd64/kubectl
2. Apply to execute permissions to the binary.
   chmod +x ./kubectl
3. Copy the binary to a folder in your PATH. If you have already installed a version of kubectl, then we recommend creating a $HOME/bin/kubectl and ensuring that $HOME/bin comes first in your $PATH.
mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin
4. After you install kubectl , you can verify its version with the following command:
kubectl version --short --client

  Task 5: Configure your AWS CloudShell to communicate with your cluster
1. Once the environment is ready on CloudShell, you create a kubeconfig file for your cluster. The settings in this file enable the Kubectl CLI to communicate with your cluster.
   

3. To create a kubeconfig file, run the following command:
   aws eks update-kubeconfig --region us-east-1 --name whiz
4. Test your configuration, with the following command:
   kubectl get svc

