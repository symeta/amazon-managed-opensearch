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

## AOS Permission Management

- [AOS IAM management](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/ac.html)
- [AOS Fine-grained Access Control](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/fgac.html)

## AOS Cross Region DR
- [Cross Cluster Replication](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/replication.html)
- [AOS cross region DR leveraging on Snapshots](https://github.com/symeta/opensearch/blob/cross-region-dr/README.md)



