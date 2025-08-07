# DVA-C02: AWS Certified Developer Associate
[**freeCodeCamp**](https://www.youtube.com/watch?v=TTcyhhH2FWE)
[**Exam Guide**](https://d1.awsstatic.com/onedam/marketing-channels/website/aws/en_US/certification/approved/pdfs/docs-dev-associate/AWS-Certified-Developer-Associate_Exam-Guide.pdf)

1. Development with AWS services(32%)
2. Security(26%)
3. Deployment(24%)
4. Troubleshooting and optimization(18%)

## EB(Elastic Beanstalk)

### Introduction

1. Environment
    a. Web Environment
    * Single-Instance Env
    * Load-Balanced Env
    
    b. Worker Environment
    
2. Deployment policies and methods
    a. Availability of deployment policies:
    ![image](https://hackmd.io/_uploads/BJtKZBuEge.png)
    
    b. Comparison of deployment methods:
    * Blue/Green deployment:
        - Clone the current(Blue) environment to create Green environment
        - Deploy new version(code) to Green environment
        - Swap traffic to Green(swap URL) after testing
    ![image](https://hackmd.io/_uploads/SyvJNSd4xl.png)

### Deploy Sample Web App Using EB
[**Tutorial**](https://www.youtube.com/watch?v=Ht1COADOsNI)

1. Definition
    ![image](https://hackmd.io/_uploads/Skpxkvh4xx.png)
    ![image](https://hackmd.io/_uploads/HJGgeDnNel.png)

2. Steps
    a. Create an IAM rule as **Service role**
    ![image](https://hackmd.io/_uploads/BJhLcwn4ee.png)
    ![image](https://hackmd.io/_uploads/B11t9PhVgl.png)
    ![image](https://hackmd.io/_uploads/ryLnqvhVxe.png)
    
    b. Create an IAM rule as **EC2 instance profile**
    ![image](https://hackmd.io/_uploads/rktLnwnNee.png)
    ![image](https://hackmd.io/_uploads/rJ1hhDnNlx.png)
    ![image](https://hackmd.io/_uploads/HyVlTDnVgx.png)
    
    c. Create environment
    ![image](https://hackmd.io/_uploads/r1FL_D2Vgx.png)
    ![image](https://hackmd.io/_uploads/r1jtdPnEle.png)
    ![image](https://hackmd.io/_uploads/ByeZYvn4lx.png)
    ![image](https://hackmd.io/_uploads/SkSmFw2Vgx.png)
    ![image](https://hackmd.io/_uploads/SJQrpv2Vgx.png)
    ![image](https://hackmd.io/_uploads/BJ9kJOhEeg.png)
    ![image](https://hackmd.io/_uploads/HJ2UJOnNxx.png)
    ![image](https://hackmd.io/_uploads/SJWdkd3Nlx.png)
    ![image](https://hackmd.io/_uploads/rJQ6yOhVxl.png)
    ![image](https://hackmd.io/_uploads/HJVke_2Exe.png)
    ![image](https://hackmd.io/_uploads/B1wSg_h4eg.png)
    
    d. Successfully launched web app
    ![image](https://hackmd.io/_uploads/HyFFG_hEel.png)
    ![image](https://hackmd.io/_uploads/SkVvzunEge.png)
    ![image](https://hackmd.io/_uploads/Sk2Rf_24lg.png)
    
    e. Testing
    * Attach **Session Manager policy** to **EC2 instance profile**: new-aws-elasticbeanstalk-ec2-role
    ![image](https://hackmd.io/_uploads/rJ1Y8934ex.png)
    * Stop instance and **Auto Scaling** will terminate it and automatically launch a replacement
    ![image](https://hackmd.io/_uploads/rkESY52Nex.png)
    ![image](https://hackmd.io/_uploads/Hk0x9qnExl.png)
    * Connect to EC2 instance by **Session Manager**
    ![image](https://hackmd.io/_uploads/SyGeic3Eel.png)
    ![image](https://hackmd.io/_uploads/H1rbs9hVxg.png)
    ![image](https://hackmd.io/_uploads/SJZXoqnNxl.png)
    * Modify sample code under `/var/app` folder
    ![image](https://hackmd.io/_uploads/SJpVm33Nxe.png)
    ![image](https://hackmd.io/_uploads/rJKQ4nhEeg.png)
    * Restart app server
    ![image](https://hackmd.io/_uploads/rkfL42n4le.png)
    * Successfully modify the web app
    ![image](https://hackmd.io/_uploads/rkva422Vex.png)
    * You can also link to the website by `http://`+`EIP`
    ![image](https://hackmd.io/_uploads/rJspI3nEeg.png)
    ![image](https://hackmd.io/_uploads/SJbUvhhVxe.png)

### Deploy Customized Web App Using EB CLI

1. Security Groups
    [**Tutorial**](https://www.youtube.com/watch?v=uYDT2SsHImQ)
    ![image](https://hackmd.io/_uploads/SytGOuhElg.png)
    
    a. Inbound Rules: allow specific IP access EC2 server via specific port
    ![image](https://hackmd.io/_uploads/rySHtu3Vee.png)
    
    b. Outbound Rules: allow EC2 server send response back to any IP via any port
    ![image](https://hackmd.io/_uploads/SJejq_hVlg.png)

2. Steps
    [**Web App Repository**](https://github.com/eva81829/AWS/tree/main/EB)
    [**EB CLI Repository**](https://github.com/aws/aws-elastic-beanstalk-cli-setup)
    
    a. Create web app on EC2
    * Create an EC2 instance
    ![image](https://hackmd.io/_uploads/SkIIMjWHlx.png)
    ![image](https://hackmd.io/_uploads/BkF_zi-Bee.png)
    ![image](https://hackmd.io/_uploads/rkQozibBxg.png)
    ![image](https://hackmd.io/_uploads/ryzpfi-rxe.png)
    * Create an IAM role with the following policies
    ![image](https://hackmd.io/_uploads/BkxOVjZrle.png)
    * Attach the IAM role to EC2 instance
    ![image](https://hackmd.io/_uploads/ByNaNsZrel.png)
    ![image](https://hackmd.io/_uploads/Hk8ySsWHxx.png)
    * Edit the security group inbound rules
    ![image](https://hackmd.io/_uploads/BJwcLoWrle.png)
    ![image](https://hackmd.io/_uploads/BkymFobBeg.png)
    * Stop, start, then connect to EC2 instance
    * Login as ec2-user: `sudo su - ec2-user`
    * Install **git**: `sudo yum install git -y`
    * Gen **SSH key**: `ssh-keygen`
    * Paste the **public key** saved in `id_rsa.pub` on GitHub
    * Clone the **web app repository**: `git clone git@github.com:eva81829/AWS.git`
    ![image](https://hackmd.io/_uploads/rJ0AWhbSlx.png)
    * Install **Node.js**:
    `curl -fsSL https://rpm.nodesource.com/setup_18.x | sudo bash -`
    `sudo yum install -y nodejs`
    * Install **express**: `npm install express`
    * Launch web app: `PORT=8080 npm start`
    ![image](https://hackmd.io/_uploads/H1rLVhZHel.png)
    ![image](https://hackmd.io/_uploads/B1Z2I2brll.png)
    ![image](https://hackmd.io/_uploads/SyhV8nbSee.png)
    
    b. Install EB CLI on EC2
    * Install **pip**: `sudo yum install -y python3-pip`
    * Install **virtualenv**: `pip3 install --user virtualenv`
    * Link **python3** to **python**: `sudo ln -s /usr/bin/python3 /usr/bin/python`
    * Clone the **EB CLI repository**: `git clone https://github.com/aws/aws-elastic-beanstalk-cli-setup.git`
    * Install **EB CLI**: `python3 ./aws-elastic-beanstalk-cli-setup/scripts/ebcli_installer.py`
    * Set EB CLI in **PATH**: `echo 'export PATH="/home/ec2-user/.ebcli-virtual-env/executables:$PATH"' >> ~/.bash_profile && source ~/.bash_profile`
    * Launch EB CLI: `eb`
    ![image](https://hackmd.io/_uploads/BJLx4szBxg.png)
    
    c. Create EB web app
    * Enter **AWS/EB/** directory
    * Initialize directory with EB CLI
    ![image](https://hackmd.io/_uploads/B1EuUjMHeg.png)
    ![image](https://hackmd.io/_uploads/S1EaIjfrxx.png)
    ![image](https://hackmd.io/_uploads/SyWIuiMBge.png)
    * Create and enter **.ebextensions/** directory
    * Create file **001_envar.config**:
        ```
        option_settings:
            aws:elasticbeanstalk:application:environment:
                PORT: 8081
                NODE_ENV: production
        ```
    * Go back to **AWS/EB/** directory
    * Create file **Procfile**:
        ```
        web: npm start
        ```    
    * Create EB environment: `eb create --single --instance_type t2.micro`
    ![image](https://hackmd.io/_uploads/ryQmMaGreg.png)
    * Successfully launched web app
    ![image](https://hackmd.io/_uploads/rJPUMpMrgg.png)
    ![image](https://hackmd.io/_uploads/ryxFGazrlg.png)
    ![image](https://hackmd.io/_uploads/HJC5zTfHxx.png)

## ECS(Elastic Container Service)

### Introduction

1. Virtual Machine vs. Container
    ![image](https://hackmd.io/_uploads/SytEizNrgx.png)
    ![image](https://hackmd.io/_uploads/SJ1qBHNLex.png)
    
2. ECS definition
    ![image](https://hackmd.io/_uploads/H1JT9fVBge.png)
    ![image](https://hackmd.io/_uploads/r18mgjNSgl.png)
    * On-premises: IT infrastructure (like servers, storage, and networking) that is physically located in your own building or data center, instead of being hosted in the cloud (like AWS, Azure, etc.) 
    ![image](https://hackmd.io/_uploads/HknKOdSHge.png)
    * ECS Anywhere:
    ![image](https://hackmd.io/_uploads/HkfugiNrlx.png)
    ![image](https://hackmd.io/_uploads/BkBxrtEree.png)
     
3. ECS Exec
    ![image](https://hackmd.io/_uploads/Syox5YEBle.png)
    
4. ECS Service Connect: Simplifies service-to-service communication within Amazon ECS. It enables ECS services to discover and connect with each other using names, without requiring manual configuration of service discovery mechanisms, load balancers, or DNS.
    ![image](https://hackmd.io/_uploads/H1VeNLBSeg.png) 

5. ECR(Elastic Container Registry):
    * Mutable: Image tags can be overwritten
    * Immutable: Image tags can't be overwritten
    ![image](https://hackmd.io/_uploads/SyeovOPBSgg.png)
    
6. Copilot: Is a **CLI** tool that helps you easily deploy and manage containerized applications on Amazon ECS (Elastic Container Service) with best practices built-in (**Simplified ECS deployments**)

### Launching ECS on Fargate
[**Tutorial**](https://www.youtube.com/watch?v=86Ys0LnMSnY&t=15s)
![image](https://hackmd.io/_uploads/SJuQDFVrxe.png)

1. Steps
    a. Create ECS cluster
    ![image](https://hackmd.io/_uploads/SkOZriVrel.png)

    b. Create task definition
    ![image](https://hackmd.io/_uploads/SkO-LiNrgl.png)
    ![image](https://hackmd.io/_uploads/B1V8IsNBgg.png)
    ![image](https://hackmd.io/_uploads/ryHOUiNSgl.png)
    * Go to Amazon ECR Public Gallery, copy NGINX docker image URL
    ![image](https://hackmd.io/_uploads/Hkbxwi4Sll.png)
    ![image](https://hackmd.io/_uploads/BkdTDsNBel.png)
    ![image](https://hackmd.io/_uploads/r1I7_s4Hxl.png)
    * Automatically generated **ecsTaskExecutionRole**
    ![image](https://hackmd.io/_uploads/BJyh_jNSlx.png)

    c. Create service
    ![image](https://hackmd.io/_uploads/Hy5tjjVSle.png)
    ![image](https://hackmd.io/_uploads/SJshjo4Bge.png)
    ![image](https://hackmd.io/_uploads/H1WN3sNBgg.png)

    d. Successfully deployed nginx service
    ![image](https://hackmd.io/_uploads/H1wbCo4Hee.png)
    ![image](https://hackmd.io/_uploads/ByjzAi4Hxx.png)
    ![image](https://hackmd.io/_uploads/Hk6QRoNrgx.png)

## EKS(Elastic Kubernetes Service)

### Introduction

1. K8s(Kubernetes)
    ![image](https://hackmd.io/_uploads/BkDPLjUBeg.png)
    * **K8s cluster** architecture:
    ![image](https://hackmd.io/_uploads/B1ueDiUBge.png)
    
2. ECS vs. EKS
    ![image](https://hackmd.io/_uploads/S1H0vcIBel.png)
    ![image](https://hackmd.io/_uploads/H1lytqUHgx.png)
    ![image](https://hackmd.io/_uploads/BkcZYq8Bge.png)
    
3. EKS Anywhere vs. EKS Connector
    ![image](https://hackmd.io/_uploads/rJNOJoIBex.png)
    ![image](https://hackmd.io/_uploads/SkKjp5USxe.png)
    * You want to set up and manage a production-grade EKS-compatible cluster on-prem: EKS Anywhere
    * You already have Kubernetes clusters outside AWS and just want to view them in the AWS Console: EKS Connector


### Create K8s Cluster on EKS Using EKS CTL
[**Tutorial**](https://www.youtube.com/watch?v=p6xDCz00TxU)

1. Steps
    a. Sign in as **IAM user** (**root user** can't be add to **system:masters** K8s admin group)
    * Sign in as **root user** first
    * Create **IAM user**(TEST)
    ![image](https://hackmd.io/_uploads/rkhtxfUrxe.png)
    * Enable **console access**
    ![image](https://hackmd.io/_uploads/r1y4zz8Bgg.png)
    * Create **user group**(GROUP)
    ![image](https://hackmd.io/_uploads/B15OMfIBlg.png)
    * Add policies
    ![image](https://hackmd.io/_uploads/rk05sfLHgg.png)
    ![image](https://hackmd.io/_uploads/HJj2bhHSgl.png)
    ![image](https://hackmd.io/_uploads/Syv1fnBreg.png)
    ![image](https://hackmd.io/_uploads/HkO0AGIrxl.png)
    * Add **IAM user**(TEST) to **user group**(GROUP)
    * Sign out, then Sign in as **IAM user**(TEST)

    a. Launch an EC2
    * Attach an IAM role with the following policies
    ![image](https://hackmd.io/_uploads/SJSUM2SBgx.png)
    * Login as ec2-user

    b. Install **EKS CTL**(EKS CLI) :
    `curl --silent --location "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp`
    `sudo mv /tmp/eksctl /usr/local/bin`
    ![image](https://hackmd.io/_uploads/Syqp0cSSxx.png)
    
    c. Create cluster using **latest version K8s**(1.33): `eksctl create cluster --name test-cluster --version 1.33 --region us-east-2 --nodegroup-name linux-nodes --node-type t2.micro --nodes 2`
    
    d. Set **IAM user** as **K8s admin** (full administrative access to K8s cluster)
    * Put **IAM user**(TEST) to **system:masters** group: `eksctl create iamidentitymapping \
    --cluster test-cluster \
    --region us-east-2 \
    --arn arn:aws:iam::042005747585:user/TEST \
    --group system:masters \
    --username admin`
    
    e. Set **IAM role** that attached to EC2  as **K8s admin**
     * Put **IAM role**(new-EC2-role) to **system:masters** group: `eksctl create iamidentitymapping \
      --cluster test-cluster \
      --region us-east-2 \
      --arn arn:aws:iam::042005747585:role/new-EC2-role \
      --group system:masters \
      --username ec2-user`
    
    f. Successfully created cluster with 2 nodes on EKS
    ![image](https://hackmd.io/_uploads/Skr7IfIrel.png)
    ![image](https://hackmd.io/_uploads/SkdIvfUSex.png)
    ![image](https://hackmd.io/_uploads/ry1iwMIHgl.png)
    * Each node is running 4 pods
    ![image](https://hackmd.io/_uploads/HJA-ojUSgl.png)
    ![image](https://hackmd.io/_uploads/Byk7ooLHlg.png)
    * Automatically generated **IAM roles**
    ![image](https://hackmd.io/_uploads/SkpnvGLrel.png)

    g. Delete cluster: `eksctl delete cluster --name test-cluster --region us-east-2`
    
## Route 53

### Introduction

1. IP address
    ![image](https://hackmd.io/_uploads/B132UtKHxe.png)
    
2. DNS(Domain Name System): Maps **IP addresses**(142.251.215.238) to **domain names**(google.com), like a phone book
    ![image](https://hackmd.io/_uploads/HkfTFwtree.png)

3. Route 53: Amazon’s managed DNS service
    ![image](https://hackmd.io/_uploads/Hy7xeuFrxg.png)
    * Hosted zone: A container for record sets where you manage the DNS records to point your domain to IP addresses or other AWS services
        - Public hosted zone: Resolves domain names to **public IP** addresses or other AWS services from the **internet**(IPv4 or IPv6)
        - Private hosted zone: Resolves domain names to **private IP** addresses or other AWS services within AWS **VPC** (Virtual Private Cloud), only inside your private network
    * Record set
        - Record type
    ![image](https://hackmd.io/_uploads/Hkvlb_tHlx.png)
    ![image](https://hackmd.io/_uploads/BkTWqOtBxx.png)
    ![image](https://hackmd.io/_uploads/BJfRKOFBgl.png)
    ![image](https://hackmd.io/_uploads/HycEtdYrxe.png)
    * Routing policies
    ![image](https://hackmd.io/_uploads/SkUdgOKSge.png)
    
### Point a domain name to a IP address

1. Steps
    a. Register a domain
    *  Need to own a domain name in order to legally use it on the internet. Otherwise, you're just setting up DNS for a name that doesn't exist, and no one will be able to find you!
    ![image](https://hackmd.io/_uploads/BJfuHYYrel.png)
    
    b. Create Record
    * Automatically generated hosted zone after registering domain
    ![image](https://hackmd.io/_uploads/HyztDFtSlg.png)
    * Exist 2 default records 
    ![image](https://hackmd.io/_uploads/HJuBdttreg.png)
    * Get web app IP address. It's better to set up **Elastic IP address**, otherwise the temporary **Public IPv4 address** would change after restart EC2
    ![image](https://hackmd.io/_uploads/rkIcctFrgg.png)
    * Point **domain name**(www.coolexample.site) to **IP addresses**(18.191.238.106)
        - Enter **subdomain**(www)
        - Select **record type**(A)
        - Select **routing policy**(Simple routing)
    ![image](https://hackmd.io/_uploads/SJwYhtYSgx.png)

    c. Successfully point the domain to IP address
    * Typing domain name(http://www.coolexample.site:8080) in browser will show the same result as typing IP address(http://18.191.238.106:8080)
    ![image](https://hackmd.io/_uploads/HyJw6FYSex.png)

## Cognito

### Introduction
[**Tutorial**](https://www.youtube.com/watch?v=QEGo6ZoN-ao)

1. Cognito
    ![image](https://hackmd.io/_uploads/HJ6pnknHgl.png)
    ![image](https://hackmd.io/_uploads/Sk_LCkhHxe.png)

2. User pools
    ![image](https://hackmd.io/_uploads/rk_3AynSxx.png)

3. Identity pools
    ![image](https://hackmd.io/_uploads/Sy-ZR12Bll.png)

## Message Processing Services: SNS, SQS, EventBridge

### SNS(Simple Notification Service)
[**Tutorial**](https://www.youtube.com/watch?v=bktTomENEX8)
![image](https://hackmd.io/_uploads/SyWKUk2Hee.png)
![image](https://hackmd.io/_uploads/B1AVPJ2Hge.png)
![image](https://hackmd.io/_uploads/B11Fwy2Hlg.png)

### SQS(Simple Queue Service)
[**Tutorial**](https://www.youtube.com/watch?v=CyYZ3adwboc)
![image](https://hackmd.io/_uploads/r1pyok2Sex.png)
![image](https://hackmd.io/_uploads/rJscKJnBxx.png)
![image](https://hackmd.io/_uploads/S1CnKk2Hge.png)

### EventBridge
[**Tutorial**](https://www.youtube.com/watch?v=RoKAEzdcr7k&t=120s)
![image](https://hackmd.io/_uploads/HJlRNf2Uge.png)

## Analytics Tools: Kinesis, OpenSearch Service, Athena

### Kinesis
[**Tutorial**](https://www.youtube.com/watch?v=_bRTlb9b59Y)

1. **Kinesis**: Is AWS’s **real-time data streaming service**. It allows you to collect, process, and analyze data streams from millions of sources in real time
    ![image](https://hackmd.io/_uploads/SkpTGJ2Bee.png)

    * **Data Streams**
    ![image](https://hackmd.io/_uploads/rknrmJ3rxx.png)
        - Roll back data

    * **Data Firehose**
    ![image](https://hackmd.io/_uploads/r1YV4yhHxg.png)
        - Batching: Improves efficiency by grouping records and sending them together, based on size or time

    * **Data Analytics**
    ![image](https://hackmd.io/_uploads/S1UOHknSle.png)

### OpenSearch Service
[**Tutorial**](https://www.youtube.com/watch?v=SIl5PM4m2KM)

1. **OpenSearch Service**: Is AWS’s managed version of the OpenSearch (formerly Elasticsearch) engine — a search and analytics engine designed for **real-time, large-scale log and data analysis**.
    * You can use OpenSearch to:
    🔎 Search across large datasets quickly (e.g. products, articles, logs)
    📈 **Visualize data** with dashboards (like Kibana or OpenSearch Dashboards)
    🔧 Power real-time applications (e.g. autocomplete, monitoring, security analytics)

2. How it works:
    a. You send data into OpenSearch (via REST API, Logstash, FluentBit, etc.)
    
    b. It indexes the data, making it searchable
    
    c. You can then:
    * Query it using DSL or SQL-like syntax
    * Visualize it with OpenSearch Dashboards

### Athena
[**Tutorial**](https://www.youtube.com/watch?v=Wkpl66NaqEA&list=PLwyXYwu8kL0wg9R_VMeXy0JiK5_c70IrV&index=86)

1. **Athena**: Is an interactive **query service** that makes easy to **analyze data dirctly from S3** 
    ![image](https://hackmd.io/_uploads/BJ0_antLle.png)
    * Creating a new table in Athena using the AWS Glue Crawler
    ![image](https://hackmd.io/_uploads/S1KC0nKLex.png)
    * Using Athena to query S3 data
    ![image](https://hackmd.io/_uploads/HyzD02tLeg.png) 

## Troubleshooting Tools: X-Ray, CloudTrail, CloudWatch

### X-Ray
[**Tutorial**](https://www.youtube.com/watch?v=5lIdNrrO_o8)
![image](https://hackmd.io/_uploads/Hkxys4hUee.png)
```
[Your App with X-Ray SDK]
       │   (generates segments/subsegments)
       ▼
[X-Ray Daemon on Host]
       │   (receives and sends)
       ▼
[AWS X-Ray Service]
           (creates, stores, visualizes, analyzes full trace)
```
```
Trace
 ├ <── Segment (e.g., API Gateway)
 ├ <── Segment (e.g., Lambda)
 │   ├── Subsegment (e.g., call to DynamoDB)
 │   └── Subsegment (e.g., HTTP call to external API)
 └ <── Segment (e.g., another Lambda or S3 call)
```
![image](https://hackmd.io/_uploads/BJ54hN2Ule.png)
* **X-Ray daemon**
The AWS X-Ray SDK does not send trace data directly to AWS X-Ray. To avoid calling the service every time your application serves a request, the SDK sends the trace data to a daemon, which collects **segments** for multiple requests and uploads them in batches

![image](https://hackmd.io/_uploads/SkLOKNhUll.png)

### CloudTrail

1. CloudTrail: Logs API calls between AWS services when you need to know who to blame. Enables **governance**, **compliance**, **operational auditing**, and **risk auditing** of your AWS account
    ![image](https://hackmd.io/_uploads/Sk2qUipSgx.png)
    * Trail
    ![image](https://hackmd.io/_uploads/S1WMFo6Hgl.png)
        - Management events(main events): Capture management operations performed on your AWS resources
        - Data events: Log the resource operations performed on or within a resource
        - Insights events: Identify unusual activity, errors, or user behavior in your account
        - Network activity events: Network activity events provide information about resource operations performed on a resource within a virtual private cloud endpoint
    ![image](https://hackmd.io/_uploads/ryBuKi6rxg.png)

### CloudWatch
[**Tutorial**](https://www.youtube.com/watch?v=Yxl7e88cTAQ)
![image](https://hackmd.io/_uploads/r1DRUspree.png)
* **Logs**
    - **CloudTrail**: Tracks API actions(AWS service API calls) across AWS (Who did what in your AWS account)
    - **CloudWatch**: Captures events and outputs from apps or AWS services (What happened inside your services or applications)
![image](https://hackmd.io/_uploads/HJjri_3Ull.png)
* Metrics
    ![image](https://hackmd.io/_uploads/Hk5Tj_28ee.png)
    ![image](https://hackmd.io/_uploads/SJflnu28xe.png)
    ![image](https://hackmd.io/_uploads/BJt-nu38xl.png)
    ![image](https://hackmd.io/_uploads/Skn_ENSDgg.png)
    ![image](https://hackmd.io/_uploads/ByXgHVHwee.png)

### Creating CloudTrail logs in S3 and CloudWatch
[**Tutorial**](https://www.youtube.com/watch?v=CXbdsp9ThvM)

1. Steps
    a. Create trail
    ![image](https://hackmd.io/_uploads/Sy6Kmnprlg.png)
    ![image](https://hackmd.io/_uploads/HJJp7naBeg.png)
    ![image](https://hackmd.io/_uploads/B141E36Sll.png)
    ![image](https://hackmd.io/_uploads/SJyb42pSee.png)
    ![image](https://hackmd.io/_uploads/r1tBN2pHlg.png)
    
    b. Launch an EC2 instance
    ![image](https://hackmd.io/_uploads/r12HwhTHxl.png)
    
    c. Viewing the output of CloudTrail logs in S3
    ![image](https://hackmd.io/_uploads/BkHDOh6See.png)
    ![image](https://hackmd.io/_uploads/SkqqdnaBge.png)
    ![image](https://hackmd.io/_uploads/By_id36Sxg.png)
    ![image](https://hackmd.io/_uploads/ryEnd3TBee.png)
    
    d. Viewing the output of CloudTrail logs in CloudWatch
    ![image](https://hackmd.io/_uploads/SyGmF2pSxe.png)
    ![image](https://hackmd.io/_uploads/SyzrthTSxe.png)
    ![image](https://hackmd.io/_uploads/B1AwF3aHll.png)
    
## CloudFormation

### Introduction

1. **Infrastructure as Code**(IaC)
    ![image](https://hackmd.io/_uploads/ByXLTJ4Ulg.png)

2. **Drift**
    ![image](https://hackmd.io/_uploads/BJapMe4Lge.png)

3. CloudFormation Pros and Cons
    ![image](https://hackmd.io/_uploads/Bkycpy4Lxx.png)
    
4. **SAM**(Serverless Application Model):
    ![image](https://hackmd.io/_uploads/B1q--kuUel.png)
    ![image](https://hackmd.io/_uploads/rJVNbyOLex.png)
    ![image](https://hackmd.io/_uploads/r1KSby_Ilx.png)
    
5. **Amplify**: Is an opinionated framework and **fully-managed infrastructure** that helps you quickly **build and deploy full-stack applications** (frontend + **serverless backend**) on AWS. When you use Amplify CLI to add backend features (e.g., an API or auth), Amplify automatically generates CloudFormation templates under the hood. It provides tools like:
    * Authentication (via Cognito)
    * APIs (REST or GraphQL via API Gateway & Lambda)
    * Storage (via S3 or DynamoDB)
    * Hosting (with continuous deployment from Git repos)

### Create a DynamoDB Table using CloudFormation
[**Tutorial**](https://www.youtube.com/watch?v=YXVCdGyHDSk)
[**Template File Repository**](https://gist.github.com/awssimplified/f96437a5a3beed65bf4782eb7b69afa4)

1. Steps
    a. Create stack
    ![image](https://hackmd.io/_uploads/HkxK8e4Lxg.png)
    ![image](https://hackmd.io/_uploads/SyXWOg4Ull.png)
    ![image](https://hackmd.io/_uploads/BJIfueV8xl.png)
    ![image](https://hackmd.io/_uploads/ByCUOxELeg.png)
    * Template file is stored in S3
    ![image](https://hackmd.io/_uploads/rJCZteVIxe.png)
    ![image](https://hackmd.io/_uploads/B1c5txNIgl.png)
    ![image](https://hackmd.io/_uploads/rkjJ9eNLle.png)
    ![image](https://hackmd.io/_uploads/SJ9M9lNLll.png)
    ![image](https://hackmd.io/_uploads/rkYBsxVUxe.png)
    ![image](https://hackmd.io/_uploads/S1NspgELxg.png)
    ![image](https://hackmd.io/_uploads/r1QapxNUgg.png)

    b. Create a change set
    * Modify template file
    ![image](https://hackmd.io/_uploads/HktBAeEIgg.png)
    ![image](https://hackmd.io/_uploads/BJ5tRgNLgg.png)
    ![image](https://hackmd.io/_uploads/By4TClEUgg.png)
    ![image](https://hackmd.io/_uploads/SkjCRl4Ueg.png)
    ![image](https://hackmd.io/_uploads/Bydy1-48le.png)
    ![image](https://hackmd.io/_uploads/BJNekZ4Ugg.png)
    ![image](https://hackmd.io/_uploads/ByaEy-N8xe.png)
    ![image](https://hackmd.io/_uploads/SkHwy-NUel.png)
    ![image](https://hackmd.io/_uploads/ByhYy-VLlx.png)

    c. Detect stack drift
    * Modify the table in the DynamoDB manually
    ![image](https://hackmd.io/_uploads/HkhlxWN8gx.png)
    ![image](https://hackmd.io/_uploads/H1t4gWE8gl.png)
    ![image](https://hackmd.io/_uploads/SkQnlbEIgl.png)
    ![image](https://hackmd.io/_uploads/ryW7ZWVUel.png)
    ![image](https://hackmd.io/_uploads/r11v-bN8xl.png)
    
## CodePipeline

### Introduction
    
1. CodePipeline
    ![image](https://hackmd.io/_uploads/HJs8TDSLll.png)
    ![image](https://hackmd.io/_uploads/HJ1rRwB8lx.png)
    ![image](https://hackmd.io/_uploads/HkkPldrIge.png)
    * Artifacts
    ![image](https://hackmd.io/_uploads/B1-BJ_HIlx.png)
    
2. CodeBuild
    ![image](https://hackmd.io/_uploads/r1anavr8gl.png)

3. CodeDeploy
    ![image](https://hackmd.io/_uploads/HkwR0PB8xe.png)
    ![image](https://hackmd.io/_uploads/S1oCBHHPeg.png)
    * **Run order of hooks in a deployment**: An  **hook** is one Lambda function specified with a string on a new line after the name of the lifecycle event. Each hook is executed once per deployment. Following are the **lifecycle events** where you can run a hook during an Auto Scaling launch deployment.
    ![image](https://hackmd.io/_uploads/HyEpVu2Uxg.png)

### Build a CI/CD Pipeline with CodePipeline
[**CodePipeline Tutorial**](https://www.youtube.com/watch?v=E-YanBx38Cs)
[**CodeBuild Tutorial**](https://www.youtube.com/watch?v=qGgNyOkZEb0&t=335s)
[**codepipeline Repository**](https://github.com/eva81829/AWS/tree/main/codepipeline)
![image](https://hackmd.io/_uploads/BJ6X3DSIxg.png)

1. Steps
    a. Deploy sample web app using **EB**
    ![image](https://hackmd.io/_uploads/HyQ5juELeg.png)
    ![image](https://hackmd.io/_uploads/rJljjdNUxl.png)
    ![image](https://hackmd.io/_uploads/S1ZBnO4Lex.png)
    ![image](https://hackmd.io/_uploads/B15whO4Uge.png)
    ![image](https://hackmd.io/_uploads/rkbjhdVUgg.png)
    ![image](https://hackmd.io/_uploads/HJWAndVIeg.png)
    ![image](https://hackmd.io/_uploads/SJZya_E8gg.png)
    ![image](https://hackmd.io/_uploads/BkmxaO48le.png)
    ![image](https://hackmd.io/_uploads/By4i6_N8xg.png)
    ![image](https://hackmd.io/_uploads/ByE2pu4Ixl.png)
    
    b. Create a **connection** with GitHub
    ![image](https://hackmd.io/_uploads/ryF0tKVLxx.png)
    ![image](https://hackmd.io/_uploads/rJ6DdY4Uge.png)
    ![image](https://hackmd.io/_uploads/rJxG-xcN8lg.png)
    ![image](https://hackmd.io/_uploads/BJwml5VIee.png)
    ![image](https://hackmd.io/_uploads/ByU775V8ee.png)
    ![image](https://hackmd.io/_uploads/SyMjXqEUxx.png)

    c. Create **build project**
    ![image](https://hackmd.io/_uploads/r1OVM7BUgx.png)
    ![image](https://hackmd.io/_uploads/S1cNmmHUll.png)
     * Insert build commands to switch to **codepipeline** folder
        ```
        version: 0.2

        phases:
          install:
            runtime-versions:
              nodejs: 18
            commands:
              - cd codepipeline
              - npm install
        artifacts:
          files:
            - '**/*'
          base-directory: codepipeline
        ```
    ![image](https://hackmd.io/_uploads/H1XKQvrUgx.png)
    ![image](https://hackmd.io/_uploads/B1a8BQrIlg.png)
    
    d. Create **IAM role**(CodePipelineServiceRole)
    * Attach following policies to the role
    ![image](https://hackmd.io/_uploads/BJ7VD7r8ee.png)
    
    e. Create **pipeline**
    ![image](https://hackmd.io/_uploads/H1XeoFEIgg.png)
    ![image](https://hackmd.io/_uploads/Sys1PmH8ll.png)
    ![image](https://hackmd.io/_uploads/BJPkLqN8gl.png)
    ![image](https://hackmd.io/_uploads/ryxAvQBIlg.png)
    ![image](https://hackmd.io/_uploads/BkdZ_XH8xl.png)
    ![image](https://hackmd.io/_uploads/r1iB8c48xl.png)
    ![image](https://hackmd.io/_uploads/rk46EwrUge.png)
    ![image](https://hackmd.io/_uploads/HJRhUqNLge.png)
    
    f. Successfully deployed a new version of the web app
    ![image](https://hackmd.io/_uploads/HJscrvBIxg.png)
    ![image](https://hackmd.io/_uploads/SJofHPSUll.png)
    
## Step Functions
[**Tutorial**](https://www.youtube.com/watch?v=zCIpWFYDJ8s)
[**Tutorial**](https://www.youtube.com/watch?v=s0XFX3WHg0w)
![image](https://hackmd.io/_uploads/rkCXzQ28ll.png)
![image](https://hackmd.io/_uploads/rJY_zQnUlx.png)
![image](https://hackmd.io/_uploads/HkISXX2Leg.png)

## ElasticCache & MemoryDB

### Introduction

1. Caching
    ![image](https://hackmd.io/_uploads/ByVdvc8Lgx.png)

2. ElasticCache
    ![image](https://hackmd.io/_uploads/H1Njw9LIle.png)

3. Deployment Options
    ![image](https://hackmd.io/_uploads/r1GAO98Ule.png)

4. Caching Comparison
    ![image](https://hackmd.io/_uploads/BJ87FcI8lx.png)
    * Memcached
    ![image](https://hackmd.io/_uploads/rkC5t9L8lx.png)
    * Redis
    ![image](https://hackmd.io/_uploads/Hkg6t5U8ee.png)
    
5. MemoryDB
    ![image](https://hackmd.io/_uploads/S1ywGaULeg.png)

## KMS(Key Management Service) & Secrets Manager

### KMS

1. **Data Key**: Is used to encrypt and decrypt your **actual data** (e.g., files, database records, or secrets)

2. **AWS KMS key（Customer Master Key）**: Is used to encrypt and decrypt **data keys**
    ![image](https://hackmd.io/_uploads/SylkhfuUee.png)
    ![image](https://hackmd.io/_uploads/SJTL2fOIgl.png)
    ![image](https://hackmd.io/_uploads/By1s3GOLxl.png)

3. **AWS**-managed AWS KMS key/ **Customer**-managed AWS KMS key
    * AWS Secrets Manager with a **customer-managed KMS key** is the recommended solution for **cross-account** access and security.

### Secrets Manager
[**Tutorial**](https://www.youtube.com/watch?v=ItzzgWe7elE&list=PLwyXYwu8kL0wg9R_VMeXy0JiK5_c70IrV&index=94)
![image](https://hackmd.io/_uploads/r1N5RQd8eg.png)
![image](https://hackmd.io/_uploads/Hk2geNOLle.png)

1. AWS Secrets Manager integrates with AWS Key Management Service (KMS) to securely encrypt and decrypt secrets, such as database credentials, API keys, and tokens

2. When you store a **secret** (e.g., a password):
    * **Secrets Manager** calls AWS **KMS** using the configured **KMS key (CMK)**
    * AWS **KMS** returns a **data key**(in both plaintext and encrypted with the CMK)
    * **Secrets Manager** uses the **plaintext data key** to encrypt your **secret value**
    * **Secrets Manager** stores the **encrypted secret** and the **encrypted data key**

## CodeGuru

### Introduction
[**Tutorial**](https://www.youtube.com/watch?v=oUeSW1STqKY)

1. **CodeGuru**: Is a developer tool powered by **machine learning** that helps improve code quality and application performance. It consists of two main components:
    * **CodeGuru Reviewer**: Analyzes your code using machine learning to identify:
        - Code **quality** issues
        - Security vulnerabilities
        - Inefficient code patterns
    * **CodeGuru Profiler**: Helps you analyze and optimize the runtime **performance** of your applications by:
        - Identifying hot paths in your code
        - Highlighting methods with high CPU usage or memory inefficiency
        - Recommending improvements
