# Guidance towards Amanzon Managed Opensearch (AOS) Operation

## AOS Ops Scope
<img width="2122" alt="image" src="https://github.com/symeta/amazon-managed-opensearch/assets/97269758/b8f1ceb1-b2d5-4290-a8f8-6fd79b66cd81">

## AOS Deployment Architecture
<img width="2226" alt="Screenshot 2023-08-27 at 09 52 28" src="https://github.com/symeta/amazon-managed-opensearch/assets/97269758/c98ed4d6-0f25-41af-8d6f-0176f2a81229">

- [standard to ultrawarm](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/ultrawarm.html)
- [ultrawarm to cold](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/cold-storage.html)
- [automatic migration](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/ism.html)

## AOS Configuration Best Practice

- [General Configuration Guidance](https://aws.amazon.com/blogs/big-data/best-practices-for-configuring-your-amazon-opensearch-service-domain/)
- [Sizing Guidance](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/sizing-domains.html)
- [AOS VPC settings](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/vpc.html)

## AOS ADFS Integration
**SAML Mechanism Diagram**
<img width="1209" alt="Screenshot 2023-08-27 at 10 09 52" src="https://github.com/symeta/amazon-managed-opensearch/assets/97269758/ef5b1bfe-1aaa-4ab5-97ad-3719b8c685ba">

- [Developer Guide on leveraging SAML to integrate AOS with existing ADFS](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/saml.html)
- [AOS Integration with Existing ADFS Implementation Guide](https://aws.amazon.com/blogs/security/configure-saml-single-sign-on-for-kibana-with-ad-fs-on-amazon-elasticsearch-service/)

Comment: The 'AOS Integration with Existing ADFS Implementation Guide' is for local AD authentication integration with ES Kibana, not straightforwardly for AAD with Opensearch Dashboard. As a result, the blog could be considered as an implementation guidance, however, cannot guarantee 100% same.
'Developer Guide on leveraging SAML to integrate AOS with existing ADFS' is the official product documentation, the content of this doc is fully authorized. 
If in case to implement an AAD integration with Opensearch via SAML is essential, I will contact Opensearch Specialist to help make a test on this.

## AOS Permission Management

- [AOS IAM management](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/ac.html)
- [AOS Fine-grained Access Control](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/fgac.html)

### Application Scenario Handling
#### 1. Platform maintenance persona to operate AOS cluster, e.g. create, delete, upgrade cluster, how to manage permission
- 1.1 Via aws console
    - step1: create role with Trusted entity type as AWS account, attach the role with AmazonOpenSearchServiceFullAccess policy (for other operation, could attach different Opensearch related policies according to specific requirement, [amazon managed opensearch IAM policy](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/ac-managed.html));
    - step2: attach the role to the IAM user who is the maintenance persona
    
- 1.2 Via CLI deployed on aws EC2
    - pre-requisite: aws java sdk installed on ec2
    - step1: create role with Trusted entity type as AWS service, and choose ec2 in Use Case section, attach the role with AmazonOpenSearchServiceFullAccess policy (for other operation, could attach different Opensearch related policies according to specific requirement, [amazon managed opensearch IAM policy](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/ac-managed.html));
    - step2: attach the role to the ec2 instance, on which the CLI as well as java application is deployed

- 1.3 Via CLI deployed on virtual machines outside aws, e.g. on-prem virtual machines, azure virtual machines.
    - step1: admin IAM user to create a new IAM user (e.g. named aos-ops) without any permissions;
    - step2: admin IAM user to create the aos-ops IAM user its AK/SK in aos-ops IAM console, Security Credentials tab;
    - step3: admin IAM user to create role with Trusted entity type as AWS service, and choose ec2 in Use Case section, attach the role with AmazonOpenSearchServiceFullAccess policy (for other operation, could attach different Opensearch related policies according to specific requirement, [amazon managed opensearch IAM policy](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/ac-managed.html));
    - step4: admin IAM user to let aos-ops IAM user to assume the service role by amending the service role's Trust relationships Tab to below:

    ```json
    {
        "Version": "2012-10-17",
        "Statement": [
          {
              "Effect": "Allow",
              "Principal": {
                  "AWS": "arn:aws:iam::<account id>:user/<aos-ops IAM user>"
              },
              "Action": "sts:AssumeRole"
          }
        ]
    }
    ```
    
    - step5: install aws cli package on the virtual machine:
  
    ```sh
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
    unzip awscliv2.zip
    sudo ./aws/install
    ```

    - step6: run aws configure on the virtual machine and input aos-ops IAM user's AK/SK credentials
    

#### 2. Java application deployed on EC2/azure virtual machine/on-prem virtual machine to manipulate AOS index, how to manage permission
  - pre-requisite1: the AOS cluster must enable fine-grained access control;
  - pre-requisite2: the AOS cluster must use username/password way to create master user, given that Opensearch Dashboard access is essential and is achieved via browser signing requests.
  - pre-requisite3: aws java sdk installed on EC2/azure virtual machine/on-prem virtual machine
  - step1: master user login to Opensearch Dashboard to create internal users;
  - step2: one java application running on EC2/azure virtual machine/on-prem virtual machine can manipulate AOS index by creating Opensearch Client with one specific internal user's credentials, click the [sample code](https://opensearch.org/docs/latest/clients/java/) to get more details.

## AOS Cross Region DR
- [Cross Cluster Replication](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/replication.html)
- [AOS cross region DR leveraging on Snapshots](https://github.com/symeta/opensearch/blob/cross-region-dr/README.md)





