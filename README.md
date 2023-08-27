# Guidance towards Amanzon Managed Opensearch (AOS) Operation

## AOS Ops Scope
<img width="2122" alt="image" src="https://github.com/symeta/amazon-managed-opensearch/assets/97269758/b8f1ceb1-b2d5-4290-a8f8-6fd79b66cd81">

## AOS Deployment Architecture
<img width="2226" alt="Screenshot 2023-08-27 at 09 52 28" src="https://github.com/symeta/amazon-managed-opensearch/assets/97269758/c98ed4d6-0f25-41af-8d6f-0176f2a81229">
- [standard to ultrawarm]([https://docs.aws.amazon.com/opensearch-service/latest/developerguide/ism.html](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/ultrawarm.html))
- [ultrawarm to cold](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/cold-storage.html)
- [automatic migration](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/ism.html)

- [1. General Configuration Guidance](https://aws.amazon.com/blogs/big-data/best-practices-for-configuring-your-amazon-opensearch-service-domain/) 
- [2. AOS VPC settings](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/vpc.html)
- [3. Developer Guide on leveraging SAML to integrate AOS with existing ADFS](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/saml.html)
- [4. AOS Integration with Existing ADFS Implementation Guide](https://aws.amazon.com/blogs/security/configure-saml-single-sign-on-for-kibana-with-ad-fs-on-amazon-elasticsearch-service/)
- [5. AOS IAM management](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/ac.html)
- [6. AOS cross region DR leveraging on Snapshots](https://github.com/symeta/opensearch/blob/cross-region-dr/README.md)



