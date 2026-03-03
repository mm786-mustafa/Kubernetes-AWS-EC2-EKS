<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up Kubernetes Deployment

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-eks2)

**Author:** Muhammad Mustafa  
**Email:** pkisbim76@gmail.com

---

## Set Up Kubernetes Deployment

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks2_45e6c3de5)

---

## Introducing Today's Project!

In this project, I will prepare a backend app for Kubernetes deployment. This is because Kubernetes deployment requires apps to be containerized and for there to be a container image. This project will get me to create that container image.

### Tools and concepts

I used Amazon EKS, Git, Docker and Amazon ECR to prepare a backend app for deplyment with Kubernetes. This involved setting up an EKS cluster, cloning code from GitHub, building and pushing a docker image to Amazon ECR.

### Project reflection

This project took me approximately two hours. The most challenging part was running into multiple errors! My favourite part was seeing an image in my ECR repository.

One thing I didn't expect in this project was needing to refresh my EC2 Instance Connect session so that my ec2-user could obtain the permission to run Docker commands after I added her to the Docker group.

---

## What I'm deploying

To set up today's project, I launched a Kubernetes cluster. Steps I took to do this included launching an EC2 instance, installing eksctl, and modifying the IAM role for my instance so that it has AdministratorAccess. I also ran a eksctl command.

### I'm deploying an app's backend

Next, I retrieved the backend that I plan to deploy. An app's backend means the logic or the 'brain' that defines how the app 'works'. I retrieved backend code by cloning it from a GitHub repository.

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks2_1ebb86c71)

---

## Building a container image

Once I cloned the backend code, my next step is to build a container image of the backend. This is because Kubernetes needs container image for a successful app deployment. At the moment I haven't prepared a container image yet (just raw code).

When I tried to build a Docker image of the backend, I ran into a permissions error because I am logged into my EC2 instance as the ec2-user (created automatically from my EC2 instance's AMI). ec2-user can't run root user level commands.

To solve the permissions error, I added the ec2-user to the Docker group. The Docker group is a group in Linux system that grants a user the permission to run Docker commands (like Docker build).

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks2_45e6c3de5)

---

## Container Registry

I'm using Amazon ECR in this project to store my container image. ECR is a good choice for the job because it is an AWS service and integrates wall with other AWS services like EKS. This makes deploying the app even faster for me.

Container registries like Amazon ECR are great for Kubernetes deployment because I get to store tagged images from a single source of truth. This means that whenever users/other services pull my container image, they can do it without any manual downloading required.

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks2_l2m3n4o5)

---

## EXTRA: Backend Explained

After reviewing the app's backend code, I've learnt that the app functions by extracting data from another API, but I also have my own API in app.py that's responsible for others wanting access to my service!

### Unpacking three key backend files

The requirements.txt file lists all the dependencies and libraries that every container needs to install when the container is created.

The Dockerfile gives Docker instructions how it should build a container image of your backend app. It includes commands on where it can find a list of all dependencies to install (requirements.txt) and commands that will atuomatically run.

The app.py file contains three main parts: insatlling dependencies, formatting the data into JSON data, passing the formatted data back to the user/requester.

---

---
