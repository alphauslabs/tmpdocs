# Cost Explorer
AWS Cost Explorer is a powerful tool that provides comprehensive insights into their AWS spending and usage. It allows users to visualize, understand, and manage their AWS costs and usage over time through customizable reports and interactive graphs. This helps organizations optimize their cloud spending by identifying cost drivers, trends, and opportunities for savings.<br>

AWS offers several cost optimization recommendations through tools like AWS Cost Explorer:

<b>Reserved Instance (RI) Recommendations</b>: These provide guidance on purchasing Reserved Instances, which offer significant discounts on EC2, RDS, Opensearch, Elasticache, Redshift and MemoryDB instances usage compared to On-Demand pricing. RI recommendations analyze usage patterns to suggest optimal RI purchases, helping users maximize cost efficiency.<br>

<b>Savings Plan (SP) Recommendations</b>: Similar to RIs, Savings Plans offer flexibility and savings on EC2, Sagemaker isntance and Compute services including AWSFargate. SP recommendations help users choose the right Savings Plan based on their historical usage patterns, optimizing cost savings.<br>

<i>==When purchasing RI and SP, users need to specify several key inputs to tailor the reservation to their needs:==</i><br><br>
<b>Payment Option</b>

| Payment Option      | Description                          |
| --------------------| ------------------------------------ |
| ALL UPFRONT         | Pay the entire cost upfront, typically yielding the highest savings. |
| PARTIAL UPFRONT     | Pay a portion upfront and the rest monthly, balancing savings and cash flow.|
| NO UPFRONT          | Pay nothing upfront and the entire cost is spread over the reservation term with monthly payments, providing the least savings but the most flexibility.|

<b>Term</b>

| Term    | Description                                                                  |
| --------------------| ---------------------------------------------------------------------------- |
| ONE-YEAR            | Shorter commitment period with less savings compared to the three-year term. |
| THREE-YEAR          | Longer commitment period with greater savings.                               |


<b>Rightsize EC2 Instance Recommendations</b>: These recommendations analyze the EC2 instance usage and suggest resizing or modifying instance types to better match their workload requirements. By rightsizing instances, users can eliminate unnecessary costs and improve performance efficiency.<br>

<b>Terminate EC2 Instance Recommendations</b>: AWS Cost Explorer also provides recommendations to terminate underutilized or unnecessary EC2 instances. This helps in reducing costs by eliminating instances that are not actively contributing to workload requirements or are no longer needed.


## Integration with Octo

In Octo, we fetch and display these AWS Cost Explorer recommendations, including RI, SP, Rightsize and Terminate EC2 instance recommendations, providing actionable insights to optimize cloud spending and enhance operational efficiency across multi-vendor environments. This integration ensures that organizations can effectively manage their AWS costs while maintaining performance and scalability in their cloud infrastructure.<br>

Below is the list of recommendations offered by cost explorer.


## Reserved Instance

??? info "Purchase EC2 Reserved Instance"
    ### Purchase EC2 Reserved Instance
    <p>
        <b>AWS Resource Type</b><br>
        EC2 Instance<br><br>
        <b>Optimization Type</b><br>
        Rate<br><br>
        <b>Category</b><br>
        Reserved Instance<br><br>
        <b>Description</b><br>
        An EC2 Reserved Instance recommendation provides guidance on optimizing AWS EC2 instance usage by leveraging Reserved Instances (RIs). These recommendations are tailored to help reduce costs by matching instance usage patterns with appropriate RI purchases. They analyze historical usage data and suggest Reserved Instances based on instance type, region, and utilization patterns. By committing to Reserved Instances, users can potentially achieve significant cost savings compared to On-Demand instance pricing, making it a valuable tool for cost optimization strategies in AWS environments<br><br>
        <b>Potential Savings</b><br>
        The exact savings depend on factors like instance type, region, payment option, and usage commitment. In general, savings can range from 30% to 75% compared to On-Demand pricing, making RIs a cost-effective choice for sustained usage of EC2 instances.<br><br>
        <b>Recommended Action</b><br>
        • Purchase EC2 Reserved Instance<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not Applicable. Users can purchase RI using AWS Console/AWS CLI<br><br>
        <b>Is rollback possible?</b><br>
        Yes. AWS provides flexibility with ==Convertible Reserved Instances==, allowing modifications to instance type, operating system, or tenancy throughout the term, ensuring adaptation to changing business needs while maintaining RI discounts. For ==Standard Reserved Instances==, they can be sold on the AWS Reserved Instance Marketplace if no longer needed, enabling users to recover upfront costs. Additionally, AWS permits ==cancellation== of Standard RIs within 30 days of purchase, with a prorated refund for the remaining term, minus any charges.
    </p>
??? info "Purchase RDS Reserved Instance"
    ### Purchase RDS Reserved Instance
    <p>
        <b>AWS Resource Type</b><br>
        RDS DB Instance<br><br>
        <b>Optimization Type</b><br>
        Rate<br><br>
        <b>Category</b><br>
        Reserved Instance<br><br>
        <b>Description</b><br>
        The RDS Reserved Instance (RI) Recommendation provides insights and suggestions to optimize Amazon Relational Database Service (RDS) costs. By analyzing the RDS usage patterns, AWS identifies opportunities where purchasing Reserved Instances can lead to significant savings compared to On-Demand instances. It evaluates the potential cost benefits of different reservation options, including instance types, regions, and reservation terms (one-year or three-year). This recommendation helps the user make informed decisions to reduce costs while maintaining the performance and availability of your RDS instances.<br><br>
        <b>Potential Savings</b><br>
        The potential savings from purchasing RDS Reserved Instances (RIs) can be substantial, typically ranging from 30% to 75% compared to using On-Demand instances. The exact savings depend on several factors, including the instance type, region, reservation term (one-year or three-year), and payment option (all upfront, partial upfront, or no upfront). By committing to using RDS instances over a specified term, users can take advantage of these discounted rates, leading to significant cost reductions for their database workloads.<br><br>
        <b>Recommended Action</b><br>
        • Purchase RDS Reserved Instance<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not Applicable. Users can purchase RI using AWS Console/AWS CLI<br><br>
        <b>Is rollback possible?</b><br>
        No
    </p>
??? info "Purchase ElastiCache Reserved Node"
    ### Purchase ElastiCache Reserved Instance
    <p>
        <b>AWS Resource Type</b><br>
        ElastiCache Cache Nodes<br><br>
        <b>Optimization Type</b><br>
        Rate<br><br>
        <b>Category</b><br>
        Reserved Instance<br><br>
        <b>Description</b><br>
        The ElastiCache Reserved Instance (RI) Recommendation provides insights and suggestions to optimize users Amazon ElastiCache costs. By analyzing the ElastiCache node usage patterns, this feature identifies opportunities where purchasing Reserved Instances can lead to significant savings compared to On-Demand instances. It evaluates the potential cost benefits of different reservation options, including node/instance types, regions, and reservation terms (one-year or three-year). This recommendation helps users make informed decisions to reduce costs while maintaining the performance and availability of their ElastiCache clusters.<br><br>
        <b>Potential Savings</b><br>
        The potential savings from purchasing ElastiCache Reserved Instances (RIs) can be substantial, typically ranging from 30% to 75% compared to using On-Demand instances. The exact savings depend on several factors, including the node type, region, reservation term, and payment option<br><br>
        <b>Recommended Action</b><br>
        • Purchase ElastiCache Reserved Instance<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not Applicable. Users can purchase RI using AWS Console/AWS CLI<br><br>
        <b>Is rollback possible?</b><br>
        No
    </p>
??? info "Purchase Redshift Reserved Node"
    ### Purchase Redshift Reserved Instance
    <p>
        <b>AWS Resource Type</b><br>
        Redshift Nodes<br><br>
        <b>Optimization Type</b><br>
        Rate<br><br>
        <b>Category</b><br>
        Reserved Instance<br><br>
        <b>Description</b><br>
        The Redshift Reserved Instance (RI) Recommendation provides tailored insights to help optimize Amazon Redshift costs. By examining the Redshift cluster usage patterns, AWS identifies opportunities to achieve significant cost savings through Reserved Instances compared to On-Demand instances. <br><br>
        <b>Potential Savings</b><br>
        Purchasing Redshift Reserved Instances (RIs) can result in considerable savings, often ranging from 30% to 75% compared to On-Demand pricing. The exact savings depend on the node type, region, reservation term (one-year or three-year), and payment option (all upfront, partial upfront, or no upfront). Committing to a reserved term allows users to benefit from discounted rates, leading to substantial cost reductions for their data warehousing operations.<br><br>
        <b>Recommended Action</b><br>
        • Purchase Redshift Reserved Instance<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not Applicable. Users can purchase RI using AWS Console/AWS CLI<br><br>
        <b>Is rollback possible?</b><br>
        No
    </p>
??? info "Purchase Opensearch Reserved Instance"
    ### Purchase Opensearch Reserved Instance
    <p>
        <b>AWS Resource Type</b><br>
        OpenSearch Instance<br><br>
        <b>Optimization Type</b><br>
        Rate<br><br>
        <b>Category</b><br>
        Reserved Instance<br><br>
        <b>Description</b><br>
        The OpenSearch Reserved Instance (RI) Recommendation feature is designed to help users manage and reduce their Amazon OpenSearch Service expenses effectively. By analyzing the usage metrics and patterns, AWS identifies opportunities to transition from On-Demand instances to Reserved Instances, which can result in substantial cost savings. It evaluates various reservation configurations, including instance types, regions, and reservation terms (one-year or three-year), and recommends the most advantageous options tailored to your specific needs. This recommendation supports cost optimization while ensuring that OpenSearch clusters maintain optimal performance and availability.<br><br>
        <b>Potential Savings</b><br>
        Purchasing OpenSearch Reserved Instances (RIs) can lead to significant savings, typically ranging from 30% to 75% compared to On-Demand instance pricing, with the exact amount depending on factors such as instance type, region, reservation term (one-year or three-year), and payment option (all upfront, partial upfront, or no upfront).<br><br>
        <b>Recommended Action</b><br>
        • Purchase OpenSearch Reserved Instance<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not Applicable. Users can purchase RI using AWS Console/AWS CLI<br><br>
        <b>Is rollback possible?</b><br>
        No
    </p>
??? info "Purchase MemoryDB Reserved Instance"
    ### Purchase MemoryDB Reserved Instance
    !!! failure "Not available yet."
## Savings Plan
??? info "Purchase Compute Savings Plan"
    ### Purchase Compute Savings Plan
    <p>
        <b>AWS Resource Type</b><br>
        Compute Services (EC2, Fargate, etc.)<br><br>
        <b>Optimization Type</b><br>
        Rate<br><br>
        <b>Category</b><br>
        Savings Plan<br><br>
        <b>Description</b><br>
        The Compute Savings Plan Recommendation assists users in optimizing their AWS compute costs by offering tailored advice on transitioning to Compute Savings Plans. By analyzing their usage patterns across various AWS services, AWS identifies opportunities to reduce expenses through Compute Savings Plans compared to On-Demand pricing. It evaluates different plan options, including instance class, regions, and commitment durations, to recommend the most cost-effective solutions. This recommendation helps users achieve significant savings while maintaining the flexibility to utilize a broad range of AWS compute resources.<br><br>
        <b>Potential Savings</b><br>
        Adopting Compute Savings Plans can lead to substantial savings, typically ranging from 30% to 66% compared to On-Demand pricing. The specific savings depend on factors such as the instance types used, AWS regions, and the duration of the commitment (one year or three years). Compute Savings Plans provide flexible pricing across different instance types and families, enabling users to benefit from lower rates while retaining the flexibility to switch between various compute resources as needed.
        <br><br>
        <b>Recommended Action</b><br>
        • Purchase Compute Savings Plan<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not Applicable. Users can purchase RI using AWS Console/AWS CLI<br><br>
        <b>Is rollback possible?</b><br>
        No
    </p>
??? info "Purchase EC2 Instance Savings Plan"
    ### Purchase EC2 Instance Savings Plan
    <p>
        <b>AWS Resource Type</b><br>
        EC2 Instance<br><br>
        <b>Optimization Type</b><br>
        Rate<br><br>
        <b>Category</b><br>
        Savings Plan<br><br>
        <b>Description</b><br>
        The EC2 Instance Savings Plan Recommendation helps users optimize their Amazon EC2 costs by providing tailored advice on transitioning to EC2 Instance Savings Plans. By analyzing their EC2 usage patterns, AWS identifies opportunities to achieve cost reductions through Savings Plans compared to On-Demand pricing. It assesses various options based on instance types, regions, and commitment durations (one year or three years) to recommend the most cost-effective plans. This recommendation enables users to secure significant savings while ensuring the flexibility to use a wide range of EC2 instances.<br><br>
        <b>Potential Savings</b><br>
        Adopting EC2 Instance Savings Plans can result in significant cost reductions, typically ranging from 37% to 69% compared to On-Demand pricing. The exact savings depend on factors such as the instance types used, AWS regions, and the duration of the commitment (one year or three years). EC2 Instance Savings Plans offer lower rates while providing flexibility to change instance types within the same family and region, allowing users to adjust their resources according to evolving needs while enjoying substantial cost savings.
        <br><br>
        <b>Recommended Action</b><br>
        • Purchase EC2 Instance Savings Plan<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not Applicable. Users can purchase RI using AWS Console/AWS CLI<br><br>
        <b>Is rollback possible?</b><br>
        No
    </p>
??? info "Purchase SageMaker Savings Plan"
    ### Purchase SageMaker Savings Plan
    <p>
        <b>AWS Resource Type</b><br>
        SageMaker Instances<br><br>
        <b>Optimization Type</b><br>
        Rate<br><br>
        <b>Category</b><br>
        Savings Plan<br><br>
        <b>Description</b><br>
        The SageMaker Savings Plan Recommendation provides users with tailored guidance on optimizing their Amazon SageMaker costs by leveraging Savings Plans. By analyzing SageMaker usage patterns, AWS identifies opportunities to reduce expenses compared to On-Demand pricing. It evaluates various plan options, including instance types, regions, and commitment durations (one year or three years), to recommend the most cost-effective solutions. This recommendation helps users achieve significant savings while maintaining flexibility in their machine learning workflows.<br><br>
        <b>Potential Savings</b><br>
        Opting for SageMaker Savings Plans can lead to substantial cost reductions, typically ranging from 30% to 65% compared to On-Demand pricing. The exact savings depend on factors such as the instance types used, AWS regions, and the duration of the commitment (one year or three years). SageMaker Savings Plans offer lower rates while providing flexibility to use a variety of instance types, allowing users to benefit from reduced costs while adapting their resources to meet changing demands.
        <br><br>
        <b>Recommended Action</b><br>
        • Purchase SageMaker Savings Plan<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not Applicable. Users can purchase RI using AWS Console/AWS CLI<br><br>
        <b>Is rollback possible?</b><br>
        No
    </p>
## Others
??? info "Rightsize EC2 Instance"
    ### Rightsize EC2
    <p>
        <b>AWS Resource Type</b><br>
        EC2 Instance<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Rightsize<br><br>
        <b>Description</b><br>
        EC2 Rightsizing recommendations in AWS Cost Explorer help users optimize their EC2 fleet by identifying instances that are over-provisioned relative to their actual usage. The system analyzes historical usage data, including CPU, memory, and network metrics, to identify underutilized instances. It then suggests more cost-effective instance types or sizes that better match current performance needs and provides cost comparisons to highlight potential savings.<br><br>
        <b>Potential Savings</b><br>
        By implementing EC2 Rightsizing recommendations, users can achieve cost reductions of 20-50% by resizing over-provisioned instances to smaller, more efficient types. For large EC2 deployments, this can lead to significant annual savings, as aligning instance types with actual usage reduces waste and avoids paying for unused capacity, resulting in more efficient spending and better cost management.
        <br><br>
        <b>Recommended Action</b><br>
        • Rightsize EC2 Instance<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        To modify the instance type of an EC2 instance, it must first be stopped. Octo handles this process as follows: it begins by calling the [StopInstances](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_StopInstances.html){target=_blank} API to stop the instance and waits until the instance status is updated to "Stopped." Once the instance is in the "Stopped" state, Octo uses the [ModifyInstanceAttribute](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_ModifyInstanceAttribute.html){target=_blank} API to update the instance type. After the type modification is complete, Octo then uses the [StartInstances](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_StopInstances.html){target=_blank} API to restart the instance.<br><br>
        <b>Is rollback possible?</b><br>
        Yes.
    </p>
??? info "Terminate EC2 Instance"
    ### Terminate EC2
    <p>
        <b>AWS Resource Type</b><br>
        EC2 Instance<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Delete<br><br>
        <b>Description</b><br>
        The Terminate EC2 Instance recommendation in AWS Cost Explorer identifies EC2 instances that are candidates for termination based on factors such as low utilization or inactivity. This recommendation helps users reduce unnecessary costs by pinpointing instances that are either no longer needed or are not being used effectively. By terminating these instances, users can stop incurring charges for idle or underutilized resources, optimizing overall cloud expenditure.<br><br>
        <b>Potential Savings</b><br>
        Following the Terminate EC2 Instance recommendation can lead to significant cost savings. By removing instances that are not providing value or are underutilized, users can reduce their EC2 expenses by up to 100% for those specific instances. This can result in substantial savings, especially for organizations with many instances running without a clear purpose. Termination of these instances ensures that users are only paying for resources that are actively contributing to their operations, leading to a more efficient and cost-effective cloud environment.
        <br><br>
        <b>Recommended Action</b><br>
        • Terminate EC2 Instance<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Octo uses [TerminateInstances](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_TerminateInstances.html){target=_blank} API to terminate instance.<br><br>
        <b>Is rollback possible?</b><br>
        Yes.
    </p>