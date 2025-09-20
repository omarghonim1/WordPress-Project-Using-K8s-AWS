# WordPress-Project-Using-K8s-AWS

Using Kubernetes To Deploy A WordPress Site With A MySQL Database On AWS

Cluster Setup 🛠️

- Created 3 VMs (1 Master + 2 Worker nodes).

- Installed Kubernetes using kubeadm.

- Configured CNI plugin for networking.

Installed AWS CSI Drivers:

- EBS CSI Driver → used for MySQL database storage (block storage).

- EFS CSI Driver → used for WordPress persistent files (shared storage).

- Created an IAM User and added its Access Key & Secret Key as a Secret inside the cluster.

- Created an IAM Role and attached the following policies:

- mazonEBSCSIDriverPolicy

- AmazonEC2ContainerRegistryPullOnly

- Custom policy for EFS access.

- Attached the IAM Role to the EC2 instances to allow pods to interact with AWS services securely.

<img width="1682" height="121" alt="Screenshot 2025-09-20 at 2 12 06 PM (2)" src="https://github.com/user-attachments/assets/d20d7906-d665-408c-8a1d-e66b11da5928" />

<img width="1824" height="555" alt="Screenshot 2025-09-20 at 2 12 43 PM (2)" src="https://github.com/user-attachments/assets/94d59315-5f90-4339-a25e-43ff0a78a38d" />

<img width="1797" height="354" alt="Screenshot 2025-09-20 at 2 13 27 PM (2)" src="https://github.com/user-attachments/assets/f0c32325-7c8e-4b9d-9980-dc14d82443cc" />

<img width="1893" height="687" alt="Screenshot 2025-09-20 at 1 42 39 PM (2)" src="https://github.com/user-attachments/assets/f73e1ff2-8d3d-4227-896d-aeeaa0c5b863" />


Project Architecture

<img width="1679" height="867" alt="Screenshot 2025-08-14 at 2 34 41 PM" src="https://github.com/user-attachments/assets/95d05beb-cd3f-4c29-897c-f7696651e875" />


How To Access 

- WordPress was exposed using a **Kubernetes Service (LoadBalancer type)**.  
- This automatically provisioned an **AWS Elastic Load Balancer (ELB)**.  
- The ELB forwards traffic from the Internet to the WordPress pods running inside the cluster.  
- To access the WordPress site, copy the **DNS name of the AWS Load Balancer** from the AWS Management Console and open it in your browser.



<img width="1416" height="314" alt="Screenshot 2025-09-20 at 1 57 56 PM (2)" src="https://github.com/user-attachments/assets/ee50724c-5926-4958-b3d4-017529c63115" />
<img width="1191" height="801" alt="Screenshot 2025-09-20 at 2 00 00 PM (2)" src="https://github.com/user-attachments/assets/47567706-6b9e-411b-ac15-3edf685b2fe8" />


