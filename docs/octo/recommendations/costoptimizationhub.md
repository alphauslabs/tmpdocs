# Cost Optimization Hub

<p>
Cost Optimization Hub is a feature within AWS Billing and Cost Management that assists users in identifying and prioritizing ways to reduce their AWS expenses. It consolidates recommendations from various AWS services, such as Compute Optimizer, into a single dashboard. Octo retrieves all the data from the Cost Optimization Hub using an AWS API and displays it within Octo to eliminate the need for users to access their AWS console.<br><br>
Below are the recommendations offered by cost optimization hub.
</p>
## AmazonRDS
??? info "Stop Amazon RDS Idle DB Instances"
    ### Stop Amazon RDS Idle DB Instances
    <p>
        <b>AWS Resource Type</b><br>
        RDS DB Instance<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Stop<br><br>
        <b>Description</b><br>
        Identifies Amazon RDS DB instances that are potentially idle.<br><br>
        <b>Potential Savings</b><br>
        100% savings based on the db instance cost.<br><br>
        <b>Recommended Action</b><br>
        •   Stop RDS DB Instance<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Octo uses [StopDBInstance](https://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_StopDBInstance.html){target="_blank"} API in stopping the db instance.<br><br>
        <b>Is rollback possible?</b><br>
        Yes. You can restart the instance through AWS Console/AWS CLI
    </p>

??? info "Rightsize RDS DB Instance"
    ### Rightsize RDS DB Instance
    <p>
        <b>AWS Resource Type</b><br>
        RDS DB Instance<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Rightsize<br><br>
        <b>Description</b><br>
        Adjust the size of the RDS DB instance to better match your workload requirements. This recommendation involves analyzing the past usage patterns, CPU utilization, memory usage, and I/O operations to determine if the instance is over-provisioned or under-provisioned.<br><br>
        <b>Potential Savings</b><br>
        Rightsizing RDS DB instance can lead to savings ranging from 20% to 50% of the current RDS costs, depending on how significantly over-provisioned the current instance is.<br><br>
        <b>Recommended Action</b><br>
        •   Rightsize RDS DB Instance<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not implemented yet.<br><br>
        <b>Is rollback possible?</b><br>
        Not implemented yet.
    </p>

??? info "Rightsize RDS DB Instance Storage"
    ### Rightsize RDS DB Instance Storage
    <p>
        <b>AWS Resource Type</b><br>
        RDS DB Instance Storage<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Rightsize<br><br>
        <b>Description</b><br>
        Rightsizing RDS DB instance storage involves adjusting the storage capacity to match the actual needs of the workload. This process ensures that the allocated storage is neither underutilized nor overprovisioned, optimizing the cost and performance balance. By carefully analyzing storage usage patterns and adjusting the storage size accordingly, businesses can achieve efficient resource utilization and maintain optimal database performance.<br><br>
        <b>Potential Savings</b><br>
        Rightsizing RDS DB instance storage can lead to significant cost savings by eliminating unnecessary storage overhead and reducing the expenses associated with overprovisioned resources. Depending on the initial storage configuration and the extent of optimization, potential savings can range from 10% to 30%. These savings stem from better-aligned storage capacity with actual usage, leading to more efficient and cost-effective database operations.<br><br>
        <b>Recommended Action</b><br>
        •   Rightsize RDS DB Instance storage<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not implemented yet.<br><br>
        <b>Is rollback possible?</b><br>
        Not implemented yet.
    </p>
??? info "Upgrade RDS DB Instance"
    ### Upgrade RDS DB Instance
    <p>
        <b>AWS Resource Type</b><br>
        RDS DB Instance<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Upgrade<br><br>
        <b>Description</b><br>
        Upgrading the generation of RDS DB instances involves transitioning from older to newer instance types within Amazon's Relational Database Service (RDS). Newer generation instances typically offer improved performance, increased storage efficiency, and enhanced network capabilities at a lower cost. This process optimizes the database environment, leading to better resource utilization and reliability.<br><br>
        <b>Potential Savings</b><br>
        By upgrading to the latest generation of RDS DB instances, organizations can achieve cost savings ranging from 10% to 30%, depending on the specific instance types and workload requirements. The improved performance and efficiency of newer instances also contribute to indirect savings by reducing the need for additional resources and minimizing downtime..<br><br>
        <b>Recommended Action</b><br>
        •   Upgrade RDS DB Instance to newer generation<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not implemented yet.<br><br>
        <b>Is rollback possible?</b><br>
        Not implemented yet.
    </p>
    
??? info "Upgrade RDS DB Instance Storage"
    ### Upgrade RDS DB Instance Storage
    <p>
        <b>AWS Resource Type</b><br>
        RDS DB Instance Storage<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Upgrade<br><br>
        <b>Description</b><br>
        Upgrading the storage for RDS DB instances involves increasing the storage capacity or transitioning to a more performant storage type. This enhancement addresses issues related to insufficient storage space, improving read/write performance, and ensuring database operations remain smooth and uninterrupted. Enhanced storage options, such as General Purpose SSD (gp3) or Provisioned IOPS SSD (io2), provide increased throughput and lower latency, leading to better overall database performance and reliability.<br><br>
        <b>Potential Savings</b><br>
        While upgrading RDS DB instance storage might involve an initial cost increase, it can lead to significant long-term savings by preventing costly downtime, reducing the need for frequent manual interventions, and improving application performance. Depending on the specific upgrade and workload characteristics, potential savings can range from 10% to 30%. This range reflects improved storage efficiency, better resource utilization, and cost-effective scaling options, which contribute to more efficient and economical database operations.<br><br>
        <b>Recommended Action</b><br>
        •   Upgrade RDS DB Instance storage<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not implemented yet.<br><br>
        <b>Is rollback possible?</b><br>
        Not implemented yet.
    </p>
??? info "Migrate RDS DB Instance to Graviton"
    ### Migrate RDS DB Instance to Graviton
    <p>
        <b>AWS Resource Type</b><br>
        RDS DB Instance<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Migrate<br><br>
        <b>Description</b><br>
        Migrating RDS DB instances to Graviton processors can significantly enhance the performance and cost-efficiency of database operations. Graviton processors, designed by AWS, deliver superior price-performance compared to traditional x86-based instances. By leveraging Graviton-based instances, businesses can achieve better throughput, reduced latency, and overall improved database performance.<br><br>
        <b>Potential Savings</b><br>
        Switching to Graviton processors can result in substantial cost savings, typically ranging from 20% to 30% compared to comparable x86-based instances. The exact savings will vary depending on the instance type and workload characteristics, but businesses can expect a notable reduction in their RDS costs while maintaining or even enhancing database performance.ts<br><br>
        <b>Recommended Action</b><br>
        •   Rightsize RDS DB Instance storage<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not implemented yet.<br><br>
        <b>Is rollback possible?</b><br>
        Not implemented yet.
    </p>

## AmazonEC2
??? info "Stop EC2 Instance"
    ### Stop EC2 Instance
    <p>
        <b>AWS Resource Type</b><br>
        EC2 Instance<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Stop<br><br>
        <b>Description</b><br>
        This recommendation advises users to stop EC2 instances that are either underutilized or not in use to optimize cloud costs. Instances that are running but not actively contributing to business processes can incur unnecessary expenses. By stopping these instances, users can avoid charges for compute resources that are not being fully utilized.<br><br>
        <b>Potential Savings</b><br>
        Stopping an EC2 instance can result in savings of up to 100% of the instance's total cost. However, additional costs may still apply for associated resources such as EBS volumes.<br><br>
        <b>Recommended Action</b><br>
        •   Stop EC2 Instance<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Octo uses [StopInstances](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_StopInstances.html){target=_blank} API to temporarily stop the instance.<br><br>
        <b>Is rollback possible?</b><br>
        Yes, users can restart the instance.
    </p>
??? info "Rightsize EC2 Auto Scaling Group"
    ### Rightsize EC2 Auto Scaling Group
    <p>
        <b>AWS Resource Type</b><br>
        EC2 Auto Scaling Group<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Rightsize<br><br>
        <b>Description</b><br>
        The Rightsize EC2 Auto Scaling Group recommendation advises adjusting the instance types and sizes within an Auto Scaling Group to better match the application's resource requirements. By analyzing current usage patterns and performance metrics, this recommendation suggests more appropriate instance types that could lead to better performance or lower costs.<br><br>
        <b>Potential Savings</b><br>
        Implementing this recommendation can lead to significant cost savings by ensuring that resources are optimized for the application's needs. Users can expect reductions in monthly EC2 costs ranging from 20% to 50%, depending on the degree of over-provisioning.<br><br>
        <b>Recommended Action</b><br>
        •   Rightsize EC2 Auto Scaling Group<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not implemented yet.<br><br>
        <b>Is rollback possible?</b><br>
        Not implemented yet.
    </p>
??? info "Upgrade EC2 Auto Scaling Group"
    ### Upgrade EC2 Auto Scaling Group
    <p>
        <b>AWS Resource Type</b><br>
        EC2 Auto Scaling Group<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Upgrade<br><br>
        <b>Description</b><br>
        The Upgrade EC2 Auto Scaling Group recommendation suggests moving to newer generation EC2 instances within the Auto Scaling Group. Newer instance types often offer better performance, enhanced features, and cost-efficiency compared to older generations.<br><br>
        <b>Potential Savings</b><br>
        Upgrading to more recent instance types can lead to improved performance and cost savings. Users may see reductions in monthly EC2 costs of up to 30%, alongside gains in computational power and efficiency.<br><br>
        <b>Recommended Action</b><br>
        •  Upgrade EC2 Auto Scaling Group<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not implemented yet.<br><br>
        <b>Is rollback possible?</b><br>
        Not implemented yet.
    </p>
??? info "Migrate EC2 Auto Scaling Group to Graviton"
    ### Migrate EC2 Auto Scaling Group to Graviton
    <p>
        <b>AWS Resource Type</b><br>
        EC2 Auto Scaling Group<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Migrate<br><br>
        <b>Description</b><br>
        The Migrate EC2 Auto Scaling Group to Graviton recommendation encourages transitioning from traditional x86-based EC2 instances to ARM-based Graviton instances. Graviton instances are designed to deliver significant cost savings and performance improvements for certain workloads.<br><br>
        <b>Potential Savings</b><br>
        Migrating to Graviton instances can result in cost reductions of up to 40% compared to traditional x86 instances, while also providing enhanced performance for specific applications optimized for ARM architecture.<br><br>
        <b>Recommended Action</b><br>
        •  Migrate EC2 Auto Scaling Group to Graviton<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not implemented yet.<br><br>
        <b>Is rollback possible?</b><br>
        Not implemented yet.
    </p>
??? info "Upgrade EC2 Instance"
    ### Upgrade EC2 Instance
    <p>
        <b>AWS Resource Type</b><br>
        EC2 Instance<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Upgrade<br><br>
        <b>Description</b><br>
        This recommendation involves upgrading existing Amazon EC2 instances to newer, more efficient instance types to better match the performance needs of applications. It identifies instances that could benefit from transitioning to newer generations or different instance families, which can offer enhanced performance, better resource utilization, and improved cost-efficiency.<br><br>
        <b>Potential Savings</b><br>
        Upgrading EC2 instances can result in cost savings ranging from 10% to 25% of total instance costs. The savings depend on the extent to which performance and resource utilization are optimized through the upgrade. Newer instance types often provide better price-performance ratios, leading to reduced overall costs.<br><br>
        <b>Recommended Action</b><br>
        •   Upgrade EC2 Instance<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not implemented yet.<br><br>
        <b>Is rollback possible?</b><br>
        Not implemented yet.
    </p>
??? info "Migrate EC2 Instance to Graviton"
    ### Migrate EC2 Instance to Graviton
    <p>
        <b>AWS Resource Type</b><br>
        EC2 Instance<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Migrate<br><br>
        <b>Description</b><br>
        This recommendation focuses on migrating existing EC2 instances to AWS Graviton processors. AWS identifies instances that could benefit from a transition to Graviton-based instances to leverage their cost-efficiency and performance advantages. Graviton processors offer improved price-performance ratios and can provide significant cost savings while maintaining or enhancing application performance.<br><br>
        <b>Potential Savings</b><br>
        Migrating to Graviton instances can lead to cost savings ranging from 20% to 40% compared to instances using Intel or AMD processors. The exact savings depend on the specific instance types being replaced and the workload requirements. Graviton instances provide a more cost-effective option without compromising performance.<br><br>
        <b>Recommended Action</b><br>
        •   Migrate EC2 Instance to Graviton<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not implemented yet.<br><br>
        <b>Is rollback possible?</b><br>
        Not implemented yet.
    </p>
## AmazonEBS
??? info "Upgrade EBS Volume"
    ### Upgrade EBS Volume
    <p>
        <b>AWS Resource Type</b><br>
        EBS Volume<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Upgrade<br><br>
        <b>Description</b><br>
        This recommendation suggests upgrading the type of Amazon Elastic Block Store (EBS) volumes to better align with the performance requirements of applications. It identifies volumes that could benefit from a transition to a higher-performance volume type, such as moving from standard SSD to provisioned IOPS SSD. Upgrading the volume type can enhance I/O performance and throughput, leading to more efficient application operations.<br><br>
        <b>Potential Savings</b><br>
        Upgrading EBS volume types can lead to cost savings by improving performance and efficiency, which can reduce the need for additional resources or mitigate performance-related issues. Potential savings typically range from 5% to 20% of total storage costs, depending on the performance improvements achieved and the volume types being compared.<br><br>
        <b>Recommended Action</b><br>
        •   Upgrade EBS Volume<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Octo begins by using the [CreateSnapshot](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_CreateSnapshot.html){target=_blank} API to create a backup snapshot. Subsequently, it calls the [ModifyVolume](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_ModifyVolume.html){target=_blank} API to adjust the volume configuration.<br><br>
        <b>Is rollback possible?</b><br>
        Yes, users can revert to the previous state of the volume by restoring it from the snapshot created during the rightsizing operation.
    </p>
??? info "Rightsize EBS Volume"
    ### Rightsize EBS Volume
    <p>
        <b>AWS Resource Type</b><br>
        EBS Volume<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Rightsize<br><br>
        <b>Description</b><br>
        This recommendation focuses on optimizing the size of Amazon Elastic Block Store (EBS) volumes to better match the actual storage needs of applications. It identifies volumes that are either underutilized or over-provisioned, suggesting adjustments to their size to improve cost-efficiency. By rightsizing EBS volumes, users can enhance storage performance and reduce unnecessary costs associated with unused capacity.<br><br>
        <b>Potential Savings</b><br>
        Rightsizing EBS volumes can result in cost savings ranging from 10% to 30% of the total storage costs. The exact savings depend on the extent of over-provisioning and the adjustment in volume size.<br><br>
        <b>Recommended Action</b><br>
        •   Rightsize EBS Volume<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not implemented yet.<br><br>
        <b>Is rollback possible?</b><br>
        Not implemented yet.
    </p>
## AWSLambda
??? info "Rightsize Lambda Function"
    ### Rightsize Lambda Function
    <p>
        <b>AWS Resource Type</b><br>
        Lambda Function<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Rightsize<br><br>
        <b>Description</b><br>
        This recommendation aims to optimize the configuration of AWS Lambda functions to ensure they are appropriately sized for their workload. It identifies functions that could benefit from adjustments to their memory allocation or timeout settings to enhance performance and reduce costs. By implementing Lambda rightsizing, organizations can achieve more efficient execution and potentially lower operational expenses.<br><br>
        <b>Potential Savings</b><br>
        Rightsizing AWS Lambda functions can lead to potential savings ranging from 20% to 50% by adjusting memory and timeout settings to match actual usage, thereby reducing over-provisioning and optimizing cost efficiency.<br><br>
        <b>Recommended Action</b><br>
        •   Rightsize Lambda Function<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Octo uses [UpdatetFunctionConfiguration](https://docs.aws.amazon.com/lambda/latest/api/API_UpdateFunctionConfiguration.html){target=_blank} to modify the version-specific settings of a Lambda function<br><br>
        <b>Is rollback possible?</b><br>
        Yes, rollback is possible after updating an AWS Lambda function configuration. AWS Lambda maintains a version history of the function code and configuration. Users can use this version history to roll back to a previous configuration or code version if the update does not work as intended. Rollback is done through AWSConsole/AWSCLI.
    </p>
## AmazonECS
??? info "Rightsize ECS Service"
    ### Rightsize ECS Service
    <p>
        <b>AWS Resource Type</b><br>
        ECS Service<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Rightsize<br><br>
        <b>Description</b><br>
        AWS recommends rightsizing the ECS service to optimize resource usage and cost efficiency. By analyzing the current task definitions and their resource allocations, AWS identifies opportunities to adjust CPU and memory settings to better match the actual usage patterns of your services. This ensures that users are not over-provisioning or under-provisioning resources, leading to more efficient operations and potential cost savings.<br><br>
        <b>Potential Savings</b><br>
        Rightsizing Amazon ECS services can lead to potential savings ranging from 10% to 40% by aligning resource allocation more closely with actual usage, reducing over-provisioning, and minimizing unnecessary costs.
        <br><br>
        <b>Recommended Action</b><br>
        •   Rightsize ECS Service<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Octo utilizes the [DescribeServices](https://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DescribeServices.html){target=_blank} API to retrieve task definitions linked to the ECS service. It then invokes the [DescribeTaskDefinition](https://docs.aws.amazon.com/AmazonECS/latest/APIReferenc/API_DescribeTaskDefinition.html){target=_blank} API to obtain detailed information about the task definitions. Subsequently, the [RegisterTaskDefinition](https://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_RegisterTaskDefinition.html){target=_blank} API is called to create a new version with the recommended data. Finally, the [UpdateService](https://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_UpdateService.html){target=_blank} API is used to update the ECS service with the newly created task definition..<br><br>
        <b>Is rollback possible?</b><br>
        Yes, after rightsizing an ECS service, a rollback is possible. If the new resource configuration does not perform as expected, users can revert to the previous configuration by updating the service with the previous task definition using AWSConsole/AWSCLI.
    </p>