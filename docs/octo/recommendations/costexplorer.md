# Cost Explorer
AWS Cost Explorer is a powerful tool that provides comprehensive insights into your AWS spending and usage. It allows users to visualize, understand, and manage their AWS costs and usage over time through customizable reports and interactive graphs. This helps organizations optimize their cloud spending by identifying cost drivers, trends, and opportunities for savings.<br>

AWS offers several cost optimization recommendations through tools like AWS Cost Explorer:

<b>Reserved Instance (RI) Recommendations</b>: These provide guidance on purchasing Reserved Instances, which offer significant discounts on EC2, RDS, Opensearch, Elasticache, Redshift and MemoryDB instances usage compared to On-Demand pricing. RI recommendations analyze usage patterns to suggest optimal RI purchases, helping users maximize cost efficiency.<br>

<b>Savings Plan (SP) Recommendations</b>: Similar to RIs, Savings Plans offer flexibility and savings on EC2, Sagemaker isntance and Compute services including AWSFargate. SP recommendations help users choose the right Savings Plan based on their historical usage patterns, optimizing cost savings.<br>

<b>Rightsize EC2 Instance Recommendations</b>: These recommendations analyze the EC2 instance usage and suggest resizing or modifying instance types to better match your workload requirements. By rightsizing instances, users can eliminate unnecessary costs and improve performance efficiency.<br>

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
        Not Applicable. Users can purchase RI in their AWS Console/AWS CLI<br><br>
        <b>Is rollback possible?</b><br>
        Yes. AWS provides flexibility with ==Convertible Reserved Instances==, allowing modifications to instance type, operating system, or tenancy throughout the term, ensuring adaptation to changing business needs while maintaining RI discounts. For ==Standard Reserved Instances==, they can be sold on the AWS Reserved Instance Marketplace if no longer needed, enabling users to recover upfront costs. Additionally, AWS permits ==cancellation of Standard RIs within 30 days of purchase, with a prorated refund for the remaining term, minus any charges.
    </p>
??? info "Purchase RDS Reserved Instance"
    ### Purchase RDS Reserved Instance
    !!! failure "Not available yet."
??? info "Purchase ElastiCache Reserved Instance"
    ### Purchase ElastiCache Reserved Instance
    !!! failure "Not available yet."
??? info "Purchase Redshift Reserved Instance"
    ### Purchase Redshift Reserved Instance
    !!! failure "Not available yet."
??? info "Purchase Opensearch Reserved Instance"
    ### Purchase Opensearch Reserved Instance
    !!! failure "Not available yet."
??? info "Purchase MemoryDB Reserved Instance"
    ### Purchase MemoryDB Reserved Instance
    !!! failure "Not available yet."
## Savings Plan
??? info "Purchase Compute Savings Plan"
    ### Purchase Compute Savings Plan
    !!! failure "Not available yet."
??? info "Purchase EC2 Instance Savings Plan"
    ### Purchase EC2 Instance Savings Plan
    !!! failure "Not available yet."
??? info "Purchase SageMaker Savings Plan"
    ### Purchase SageMaker Savings Plan
    !!! failure "Not available yet."
## Others
??? info "Rightsize EC2 Instance"
    ### Rightsize EC2
    !!! failure "Not available yet."
??? info "Terminate EC2 Instance"
    ### Terminate EC2
    !!! failure "Not available yet."