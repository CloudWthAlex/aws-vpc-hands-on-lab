\# AWS VPC Hands-On Lab – Network Foundations



\## 📌 Overview



This project documents a \*\*hands-on Amazon VPC (Virtual Private Cloud) lab\*\* completed using the \*\*AWS VPC Wizard\*\*. The lab focuses on building and understanding a secure, production-style cloud network with \*\*public and private subnets\*\*, \*\*routing\*\*, and \*\*controlled internet access\*\*.



This repository is designed to demonstrate \*\*practical cloud networking fundamentals\*\* to recruiters, hiring managers, and ATS systems, showing not just theory but real AWS console experience.



---



\## 🎯 Lab Objectives



By completing this lab, I demonstrated the ability to:



\* Design and create an Amazon VPC using AWS best practices

\* Configure public and private subnets

\* Understand and apply routing concepts

\* Implement secure outbound internet access using a NAT Gateway

\* Explore core VPC security components (Route Tables, NACLs, Security Groups)



---



\## 🧱 Architecture Diagram



```

```mermaid
%% AWS VPC Lab – Colorful Visualization
graph TB
    classDef internet fill:#fef9c3,stroke:#f59e0b,stroke-width:2px;
    classDef vpc fill:#dbeafe,stroke:#3b82f6,stroke-width:2px,stroke-dasharray:5 5;
    classDef public fill:#d1fae5,stroke:#10b981,stroke-width:2px;
    classDef private fill:#fee2e2,stroke:#ef4444,stroke-width:2px;
    classDef resource fill:#f0f9ff,stroke:#3b82f6,stroke-width:2px;

    Internet[🌐 Internet]:::internet

    subgraph "VPC: lab-vpc (10.0.0.0/16)":::vpc
        IGW[📡 Internet Gateway]:::resource
        
        subgraph "Public Subnet (10.0.25.0/24)":::public
            NAT[NAT Gateway]:::resource
            RouteTablePublic[Route Table]:::resource
        end
        
        subgraph "Private Subnet (10.0.50.0/24)":::private
            AppServer[Application Instance]:::resource
            RouteTablePrivate[Route Table]:::resource
        end
        
        IGW --> RouteTablePublic
        NAT --> IGW
        RouteTablePublic --> NAT
        RouteTablePrivate --> NAT
        AppServer --> RouteTablePrivate
    end

    Internet --> IGW


```



---



\## ⚙️ Technical Steps Completed



\### 1. VPC Creation



\* Created a custom VPC using \*\*AWS VPC Wizard (VPC and more)\*\*

\* CIDR block: \*\*10.0.0.0/16\*\*

\* Deployed in \*\*1 Availability Zone\*\*



\### 2. Subnet Design



\* \*\*Public Subnet\*\*: `10.0.25.0/24`

\* \*\*Private Subnet\*\*: `10.0.50.0/24`

\* Each subnet scoped to a single AZ



\### 3. Internet Connectivity



\* Attached an \*\*Internet Gateway (IGW)\*\* to the VPC

\* Configured routing for public subnet to allow internet access



\### 4. NAT Gateway Configuration



\* Deployed a \*\*Zonal NAT Gateway\*\* in the public subnet

\* Enabled \*\*outbound-only internet access\*\* for private subnet resources



\### 5. Route Tables



\* \*\*Public Route Table\*\*:



&nbsp; \* `10.0.0.0/16 → local`

&nbsp; \* `0.0.0.0/0 → Internet Gateway`



\* \*\*Private Route Table\*\*:



&nbsp; \* `10.0.0.0/16 → local`

&nbsp; \* `0.0.0.0/0 → NAT Gateway`



\### 6. Network Security



\* Reviewed \*\*Network ACLs\*\* (stateless, subnet-level)

\* Explored \*\*Security Groups\*\* (stateful, instance-level)

\* Verified default security group behavior



---



\## 🔐 Cloud \& Networking Fundamentals Demonstrated



\* VPC isolation and IP addressing (CIDR)

\* Public vs Private subnet design

\* Secure internet access patterns

\* Stateless vs Stateful security controls

\* AWS-managed high availability networking components



---



\## 🌍 Real-World Relevance



This architecture reflects a \*\*common production-ready AWS network design\*\*, where:



\* Web-facing components reside in public subnets

\* Application and database layers remain private

\* Internet access is tightly controlled

\* Security is layered and intentional



These concepts are foundational for roles such as:



\* Cloud Engineer

\* DevOps Engineer

\* Site Reliability Engineer (SRE)

\* Junior Solutions Architect



---



\## 🧠 Key Takeaways



\* A subnet is "public" or "private" based on its \*\*route table\*\*, not its name

\* NAT Gateways enable secure outbound access without exposing private resources

\* AWS networking emphasizes \*\*least privilege and defense-in-depth\*\*



---



\## 📂 Repository Purpose



This repository is part of my \*\*cloud engineering portfolio\*\*, showcasing hands-on AWS experience and continuous learning through structured labs.



> 📌 \*Note: EC2 deployment was intentionally excluded as per lab constraints.\*



---



\## 👤 Author



\*\*Alexander Lim Zhi Sean\*\*

Aspiring Cloud Engineer | AWS | Linux | Networking

Part of \*\*#200DaysOfCloudEngineer\*\* journey



---



\## 🏷️ Keywords (ATS Optimization)



AWS VPC, Cloud Networking, Amazon Web Services, Public Subnet, Private Subnet, NAT Gateway, Internet Gateway, Route Tables, Network ACL, Security Groups, Cloud Fundamentals, Infrastructure, DevOps, Entry-Level Cloud Engineer



