<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Create Kubernetes Manifests

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-eks3)

**Author:** Muhammad Mustafa  
**Email:** pkisbim76@gmail.com

---

## Create Kubernetes Manifests

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks3_b01876555)

---

## Introducing Today's Project!

In this project, I will set up manifest files because they are a key part of the Kubernetes deployment process. Manifest files give Kubernetes the instructions on HOW it should deploy my containerized application.

### Tools and concepts

I used Amazon EKS, eksctl, Git, Docker, Amazon ECR to create a Kubernetes cluster and build the container image of the backend of an app to deploy. Key concepts include using manifests files, deployments and services to get ready for a Kubernetes deployment.

### Project reflection

This project met my goals because I wanted to understand the details of Kubernetes deployment, and this project made me understand the broader strategy (i.e., deploying a cluster, building a container image) and the fine-grained details of manifest.

This project took me approximately two hours, including demo time. The most challenging part was understanding/breaking down the Deployment manifest. My favourite part was being able to set up manifest files and understand how it works together.

---

## Project Set Up

### Kubernetes cluster

To set up today's project, I launched a Kubernetes cluster. Steps I took to do this included granting my EC2 instance permissions over IAM and installing the eksctl command-line tool. I created the cluster using the eksctl create command.

### Backend code

I retrieved the backend that I plan to deploy by cloning it from Nextwork team member's GitHub repository. Backend is the 'brain' or the logic of an application. For example, how an app stores, retrieves and processes data.

### Container image

Once I cloned the backend code, I built a container image because Kubernetes requires apps to be in container images to deploy them. I used Docker to build a container image of my backend.

I also pushed the container image to a container registry to establish a single source of truth for the latest version. To push the image to ECR, I ran the push commands that built and tagged the image.

---

## Manifest files

Kubernetes manifests are instructions for Kubernetes on how it should deploy my application. Manifests are helpful because they reduce manual work when I want to deploy and manage applications across multiple containers (clusters).

A Kubernetes deployment manages multiple copies of the same containerized backend. The container image URI in my Deployment manifest tells Kubernetes the attributes of the container that I would like Kubernetes deploy.

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks3_b01876554)

---

## Service Manifest

A Kubernetes Service exposes my application to network traffic. You need a Service manifest because the Deployment Manifest takes care of creating/managing the application, except that users/apps will get access to it. No Service manisfest = No traffic.

My Service manifest sets up a NodePort and a targetPort, which means it maps traffic that gets to port 8080 of the Service to port 8080 of a container running the application.

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks3_b01876555)

---

## Deployment Manifest

Annotating the Deployment manifest helped me understand the ins and outs of each command in the Deployment manifest because you are breaking down and explaining each line and also their relationship to other commands and tools.

A notable line in the Deployment manifest is the number of replicas, which means the number of copies of my app I'd like to deploy across my cluster. Pods are relevant to this because 3 replicas = 3 pods (1:1 relationship).

One part of the Deployment manifest I still want to know more about is the namespace of a Deployment because it is not too clear, and how it impacts Deployment / how it's used as metadata.

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks3_6aae73e71)

---

---
