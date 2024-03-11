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

# Usage
- Clone this repository to your local machine using:
```
git clone 
```
