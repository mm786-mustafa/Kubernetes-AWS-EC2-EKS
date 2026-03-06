<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Deploy Backend with Kubernetes

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-eks4)

**Author:** Muhammad Mustafa  
**Email:** pkisbim76@gmail.com

---

## Deploy Backend with Kubernetes

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks4_6cfb382f2)

---

## Introducing Today's Project!

In this project, I will deploy the backend of an application with Kubernetes. This project will start from scratch (i.e., launching an EC2 instance) and go all the way to having a live backend deployed.

### Tools and concepts

I used Kubernetes, ECR, kubectl, eksctl, Docker, gitHub to deploy the backend of an application. Key concepts include applying manifests files, building container images and pushing them to a container registry.

### Project reflection

This project took me approximately two hours inclding demo time. The most challenging part was creating the manifest files. My favourite part was verifying the deployment in the EKS console.

---

## Project Set Up

### Kubernetes cluster

To set up today's project, I launched a Kubernetes cluster. The cluster's role in this deployment is to be the control centre for using Kubernetes and orchestrating all the containers that will be running the application I want to deploy.

### Backend code

I retrieved backend code by cloning the Nextwork team member's repository in GitHub so I have the local copy of their work. Pulling code is essential to this deployment because I need to access it to build a container image of my application so that Kubernetes will deploy it.

### Container image

Once I cloned the backend code, I built a container image because Kubernetes needs my application to be packaged in an image to deploy it. Without an image, it would be difficult for Kubernetes to deploy my application consistently across the cluster.

I also pushed the container image to a container registry, which is a storage space for container images in the cloud. ECR facilitates scaling for my deployment because Kubernetes can easily grab whichever image is tagged latest for each container it creates in the cluster.

---

## Manifest files

Kubernetes manifests are the instruction manuals on how I'd like Kubernetes to deploy, expose, and run my containerized application. Manifests are helpful because it allows Kubernetes to repeat a deployment using the same instructions.

A Deployment manifest manages the creation/setting up of a Deployment resource that's responsible for creating containers/rolling out updates across my EKS cluster. The container image URL in my Deployment manifest tells Kubernetes where my image is.

A Service resource exposes a deployed application to users/traffic. My Service manifest sets up a Service resource that exposes my backend application at port 8080 within the EKS cluster.

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks4_b01876554)

---

## Backend Deployment!

To deploy my backend application, I applied the manifest files that I created. Applying a manifest file means giving Kubernetes the templates for creating the Deployment and Services resources to deploy and expose my application.

### kubectl

kubectl is the command-line tool for interacting with Kubernetes resources (like Deployment or Service resources) once your cluster is up and running. I'm using it to apply my manifest files and deploy my application. I can't use eksctl for the job because this tool is for creating the cluster.

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks4_6cfb382f2)

---

## Verifying Deployment

My extension for this project is to use the EKS console to verify my deployment. I had to set up IAM access policies because I don't access to see my cluster's nodes. I set up access by running 'create iamidentitymapping'.

Once I gained access to my cluster's nodes, I discovered pods running inside each node. Pods are the smallest deployable unit and represent bundles of containers. Containers in a pod share networking and storage resources, making the app run efficiently.

The EKS console shows you the events for each pod, where I could see a container image getting pulled and used to create a new container running the backend application. This validated that the deployment was a success, the backend is running.

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks4_3b391f873)

---

---
