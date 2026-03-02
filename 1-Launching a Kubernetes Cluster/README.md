<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Launch a Kubernetes Cluster

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-eks1)

**Author:** Muhammad Mustafa  
**Email:** pkisbim76@gmail.com

---

## Launch a Kubernetes Cluster

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks1_e5f6g7h8)

---

## Introducing Today's Project!

In this project, I will deploy my very first Kubernetes cluster using Amazaon EKS because EKS is AWS' service for deploying Kubernetes clusters in the cloud and to get hands on experience with Kubernetes and how it works. It will involve multiple steps like launching an EC2 instance, create my own Kubernetes cluster, monitor cluster creation using CloudFormation and access cluster using IAM access entry.

### What is Amazon EKS?

### One thing I didn't expect

### This project took me...

---

## What is Kubernetes?

Kubernetes is a tool for automating the management of running containers/containerized applicaitons; aka container orchestration. Companies and developers use Kubernetes to deploy and manage large scale containerized applications.

I used eksctl to create a Kubernetes cluster using the command line. The 'eksctl create cluster' command I ran defined the name of the cluster, its node group's name and node size settings. I also define the region and the instance type of EC2.

I initially ran into two errors while using eksctl. The first one was because of not having installed eksctl too yet. The second one was because my EC2 instance did not have permissions to my AWS account and services.

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks1_ff9bfc221)

---

## eksctl and CloudFormation

CloudFormation helped create my EKS cluster because eksctl uses CloudFormation under the hood to actually create my cluster when I run an eksctl command. It created VPC resources because creating the EKS cluster in my default VPC would cause compatibility and permission issues.

There was also a second CloudFormation stack for the node group. The difference between a cluster and node group is that the cluster is the entire Kubernetes setup (including the control plane), while the node group is just a group of EC2 instances inside.

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks1_w3e4r5t6)

---

## The EKS console

I had to create an IAM access entry in order to see the nodes in my new node group. An access entry is a mapping of AWS IAM policies to Kubernetes access control system. I set it up by using the Access Entries page within the EKS management console.

It took at least 40 minutes to create my cluster. Since I'll create this cluster again in the next project of this series, maybe this process could be sped up if I used templates e.g. Terraform or CloudFormation. And install dependencies ahead.

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks1_e5f6g7h8)

---

## EXTRA: Deleting nodes

Did you know you can find your EKS cluster's nodes in Amazon EC2? This is because an EC2 is the node in Kubernetes clusters/setup using AWS.

Desired size in a Kubernetes node group is the number of nodes I would like to maintain. Mininum and maximum sizes are helpful for maintaining high availability (even in low traffic periods) and also preparation for traffic in general.

When I deleted my EC2 instances, new EC2 instances started to launch by Kuebernetes cluster. This is because my Kubernetes cluster wanted to maintain its desired size/state (3).

![Image](http://learn.nextwork.org/excited_gray_glamorous_dog/uploads/aws-compute-eks1_q7r8s9t0)

---

---
