# eksctl-deployment
This repo outlines a custom template that can be used to deploy the Amazon EKS service with some custom fields within a linux environment

# Requirements

- Make sure `eksctl` is installed on your machine:
```
# Download and extract the latest release of eksctl with the following command.
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
# Move the extracted binary to /usr/local/bin.
sudo mv /tmp/eksctl /usr/local/bin
# Test that your installation was successful with the following command. 
eksctl version
```

- Install `kubectl` using the [official guide](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/#install-kubectl-on-linux).
- Create an AWS access key on the AWS console and populate the `.aws/credentials` file with the `aws_access_key_id` and `aws_secret_access_key` using the following template:
```
[default]
aws_access_key_id = **************
aws_secret_access_key = ****************************************
```

# Create eksCluster
Perform the following steps on your linux machine:

## Option 1
- Clone this repository to your local machine:
```
git clone https://github.com/SamsonIdowu/eksctl-deployment.git
```

- Edit the `config.yaml` file and save the changes
```
nano ./eksctl-deployment/config.yaml
```

- Create an eksCluster using the `eksctl create` command as shown below:
```
eksctl create cluster -f ./eksctl-deployment/config.yaml
```

## Option 2

- Edit the following commands and run on a linux shell:
```
eksctl create cluster \
--name=test-cluster \
--version=1.29 \
--region=us-east-1 \
--zones=us-east-1a,us-east-1b,us-east-1c \
--nodegroup-name=eks-nodes \
--node-type=t2.micro \
--nodes=2 \
--nodes-min=2 \
--nodes-max=4 \
--vpc-name=<your-vpc-name> \
--vpc-cidr=<your-vpc-cidr> \
--vpc-private-subnets=<comma-separated-list-of-private-subnets> \
--vpc-public-subnets=<comma-separated-list-of-public-subnets> \
--alb-ingress-access \
--vpc-endpoints=S3
```

# Destroy eksCluster
Perform the following steps on your linux machine:
## Option 1
- To remove your eksCluster, run the following command:
```
eksctl delete cluster -f ./eksctl-deployment/config.yaml --all
```

## Option 2
- To remove your eksCluster, run the following command:
```
eksctl delete cluster --name <cluster-name> --region <region> --all
```
