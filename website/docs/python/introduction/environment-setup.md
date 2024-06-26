---
title: Setting up the Development Environment
sidebar_position: 3
---
## Objective

This guide shows you how to up the necessary tools and environment to leverage the [python-fastapi-demo-docker](https://github.com/aws-samples/python-fastapi-demo-docker) project. For more samples, we recommend exploring the sample app collection (e.g., Python, Flask, FastAPI, PostgreSQL) at [docker/awesome-compose](https://github.com/docker/awesome-compose).

## 1. Installing Required Tools

To facilitate a beginner-friendly introduction to Kubernetes, this workshop is structured with user-friendly tools at its core. Central to this approach is the use of [eksctl](https://eksctl.io/), an Infrastructure as Code (IaC) tool that allows you to update the control plane, manage add-ons, and oversee worker node updates. 

If you're planning to complete the workshop in full, make sure you've set up the following tools on your local machine.

- [Install Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Create a DockerHub Account](https://hub.docker.com/)
- [Install Python 3.9+](https://www.python.org/downloads/release/python-390/)
- [Install the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
- [Install minikube](https://minikube.sigs.k8s.io/docs/start/)
- [Install eksctl](https://eksctl.io/installation)
- [Install kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl)
- [Install Helm](https://helm.sh/docs/intro/install/)

## 2. (Optional) Alternative Tools
Optionally, if you are using macOS catalina (10.15) or higher, you can use Finch, instead of Docker. Finch is an open source tool for local container development. It is available for macOS on Intel and Apple Silicon. Finch and Docker can be installed together; however, for performing the workshop exercises, we recommend using either Finch or Docker consistently for all the steps.

- [Install Finch](https://runfinch.com/docs/managing-finch/macos/installation/)

## 3. Configuring the Shell Environment

First, configure your AWS credentials to be able to create AWS resources from the command line. Configure the AWS CLI by running:

```bash
aws configure
```

Enter your AWS credentials:

```bash
AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
Default region name [None]: us-east-2
Default output format [None]: json
```

## 4. Setting Up the Application

Clone the [python-fastapi-demo-docker](https://github.com/aws-samples/python-fastapi-demo-docker) repository and navigate into the project directory:

```bash
git clone https://github.com/aws-samples/python-fastapi-demo-docker.git 
```

If you prefer not to use git, you can alternatively [download the Zip file](https://github.com/aws-samples/python-fastapi-demo-docker/archive/refs/heads/main.zip).

## 5. Creating the .env File

We'll be heavily reliant on environment variables to ease the set-up process throughout this workshop.

First, navigate into the project directory and make a copy of the example environment variables file.

```bash
cd python-fastapi-demo-docker
cp .env.example .env
```

Now add your AWS credentials to the `.env` file you just created:

```bash
AWS_ACCOUNT_ID=012345678901
AWS_ACCESS_KEY_ID=ASIAWNZPPVHEXAMPLE
AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLE
AWS_REGION=us-east-1
```

Update the sample value with your [DockerHub](https://hub.docker.com/) user name:

```
DOCKER_USERNAME=frank9
```

## 6. Import Environment Variables

Next, from the root directory of the 'python-fastapi-demo-docker' project, import all environment variables by running the following commands.

**macOS**

```bash
set -o allexport; source .env
printenv
```

**Windows**

```bash
@echo off
for /f "usebackq delims=" %%x in (".env") do set "%%x"
set
```

**Linux**

```bash
source .env
printenv
```

## 7. Install Other Tools (Recommended)

- Consider installing the [Docker VS Code Extension](https://code.visualstudio.com/docs/containers/overview). This tool simplifies the management of container images and allows you to access container logs and console output directly from VS Code 🔥.

- Verify the Finch installation by running the following commands:

```bash
finch vm init
finch run public.ecr.aws/finch/hello-finch:latest
```

## What's Next?

- [Containers](../containers/index.md)
