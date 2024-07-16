# Recommendation
Recommendation is a cost optimization feature offered by Octo that helps users effectively manage expenses. Designed for multi-vendor environments, including AWS, GCP, and Azure, it currently supports AWS, with plans to extend to other platforms in the future. This feature also consolidates recommendations from AWS Cost Explorer, Cost Optimization Hub, and Trusted Advisor, providing comprehensive insights into cost-saving opportunities. It empowers users to make informed decisions and optimize their cloud expenditures efficiently.

## Apply Recommended Action
!!! warning "This is not included in the current version."
In addition to providing users with recommendations for optimizing their cloud costs, Octo enables users to execute or apply these recommendations directly within its interface, eliminating the need to access their AWS console. This streamlined approach empowers users to take immediate action on cost-saving suggestions, enhancing efficiency and simplifying the management of AWS resources. By integrating actionable insights and execution capabilities, Octo ensures a seamless experience for users, facilitating quicker responses to optimize their cloud expenditure.

## List of Recommendations
Currently, we rely on two primary sources for these recommendation data: AWS and Octo-generated recommendations. AWS-generated recommendations originate from various AWS features or services such as Cost Explorer, Cost Optimization Hub, and Trusted Advisor. In contrast, Octo generates additional recommendations that encompass insights not covered by these AWS sources, providing users with a more comprehensive view of potential optimizations for their cloud environment. This dual-source approach ensures that Octo users have access to a wide range of actionable insights to enhance their cost management strategies.
### Amazon Web Services Generated Recommendations

=== "Cost Explorer"
    !!! failure "Not Available yet."
=== "Cost Optimization Hub"
    #### Cost Optimization Hub
    <p>
    Cost Optimization Hub is a feature within AWS Billing and Cost Management that assists users in identifying and prioritizing ways to reduce their AWS expenses. It consolidates recommendations from various AWS services, such as Compute Optimizer, into a single dashboard. Octo retrieves all the data from the Cost Optimization Hub using an AWS API and displays it within Octo to eliminate the need for users to access their AWS console.<br><br>
    Below are the recommendations offered by cost optimization hub.
    </p>
    AmazonRDS
    ??? info "Stop Amazon RDS Idle DB Instances"
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
=== "Trusted Advisor"
    #### Trusted Advisor
    <p>
    AWS Trusted Advisor, a service from Amazon Web Services (AWS), offers real-time guidance to assist users in provisioning their resources according to AWS best practices. It provides recommendations across categories like cost optimization, performance, security, and fault tolerance. Octo leverages its API to fetch and display recommendations specifically from the cost optimization category.
    !!! note "Trusted Advisor Recommendations are accessible exclusively to users subscribed to the ==Business==, ==Enterprise On-Ramp==, or ==Enterprise Support plans==."
    Below is the list of recommendations under cost optimization category that are supported by octo.
    </p>

    AmazonEBS
    ??? info "Underutilized Amazon EBS Volumes"
        <p>
            <b>AWS Resource Type</b><br>
            EBS Volume<br><br>
            <b>Optimization Type</b><br>
            Usage<br><br>
            <b>Category</b><br>
            Delete<br><br>
            <b>Description</b><br>
            Checks Amazon Elastic Block Store (Amazon EBS) volume configurations and warns when volumes appear to be underutilized.<br><br>
            Charges begin when a volume is created. If a volume remains unattached or has very low write activity (excluding boot volumes) for a period of time, the volume is underutilized. We recommend that you remove underutilized volumes to reduce costs.<br><br>
            <b>Criteria</b><br>
            •   A volume is unattached or had less than 1 IOPS per day for the past 7 days.<br><br>
            <b>Potential Savings</b><br>
            Deleting detached EBS volumes results in savings, calculated by subtracting the volume's cost from the snapshot's overall cost<br><br>
            <b>Recommended Action</b><br>
            Create snapshot and delete the volume<br><br>
            <b>How will Octo implement the recommended action?</b><br>
            Octo uses [CreateSnapshot](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_CreateSnapshot.html){target="_blank"} API to create a snapshot of the volume.
            If the EBS volume is currently attached to an EC2 instance, Octo invokes [DetachVolume](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DetachVolume.html){target="_blank"} API to detach it. Following detachment, Octo proceeds to use [DeleteVolume](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DeleteVolume.html){target="_blank"} to delete the volume.<br><br>
            <b>Is rollback possible?</b><br>
            Yes. Use the snapshot created to restore the volume using AWS Console/AWS CLI
        </p>
    AmazonEC2
    ??? info "Low Utilization Amazon EC2 Instances"
        <p>
            <b>AWS Resource Type</b><br>
            EC2 Instance<br><br>
            <b>Optimization Type</b><br>
            Usage<br><br>
            <b>Category</b><br>
            Stop<br><br>
            <b>Description</b><br>
            Checks the Amazon Elastic Compute Cloud (Amazon EC2) instances that were running at any time during the last 14 days. This check alerts if the daily CPU utilization was 10% or less and network I/O was 5 MB or less for at least 4 days.<br><br>
            Running instances generate hourly usage charges. Although some scenarios can result in low utilization by design, you can often lower your costs by managing the number and size of your instances.<br><br>
            <b>Criteria</b><br>
            •   An instance had 10% or less daily average CPU utilization and 5 MB or less network I/O on at least 4 of the previous 14 days. <br><br>
            <b>Potential Savings</b><br>
            Estimated monthly savings are calculated by using the current usage rate for On-Demand Instances and the estimated number of days the instance might be underutilized. Actual savings will vary if you are using Reserved Instances or Spot Instances, or if the instance is not running for a full day. <br><br>
            <b>Recommended Action</b><br>
            Stop EC2 instance<br><br>
            <b>How will Octo implement the recommended action?</b><br>
            Octo uses [StopInstances](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_StopInstances.html){target="_blank"} API to stop the EC2 instance.<br><br>
            <b>Is rollback possible?</b><br>
            Yes. You can manually start the instance again through AWS console or AWS CLI.
        </p>
    ??? info "Unassociated Elastic IP Addresses"
        <p>
            <b>AWS Resource Type</b><br>
            Elastic IP Address<br><br>
            <b>Optimization Type</b><br>
            Usage<br><br>
            <b>Category</b><br>
            Delete<br><br>
            <b>Description</b><br>
            Checks for Elastic IP addresses (EIPs) that are not associated with a running Amazon Elastic Compute Cloud (Amazon EC2) instance.<br><br>
            EIPs are static IP addresses designed for dynamic cloud computing. Unlike traditional static IP addresses, EIPs mask the failure of an instance or Availability Zone by remapping a public IP address to another instance in your account. A nominal charge is imposed for an EIP that is not associated with a running instance.<br><br>
            <b>Criteria</b><br>
            •	An allocated Elastic IP address (EIP) is not associated with a running Amazon EC2 instance.<br><br>
            <b>Recommended Action</b><br>
            •	Release/Delete Elastic IP Address<br>
            •	Associate EIP to EC2 instance<br><br>
            <b>How will Octo implement the recommended action?</b><br>
            Octo only supports releasing the Elastic IP Address. You can associate EIP to instance using AWS Console/AWS CLI.<br><br>
            For Releasing EIP:<br>
            Octo uses [ReleaseAddress](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_ReleaseAddress.html){target="_blank"} API.<br><br>
            <b>Is rollback possible?</b><br>
            No
        </p>
    AWSELB
    ??? info "Idle Load Balancers"
        <p>
            <b>AWS Resource Type</b><br>
            Elastic Load Balancer<br><br>
            <b>Optimization Type</b><br>
            Usage<br><br>
            <b>Category</b><br>
            Delete<br><br>
            <b>Description</b><br>
            Checks your Elastic Load Balancing configuration for load balancers that are idle.<br><br>
            Any load balancer that is configured accrues charges. If a load balancer has no associated back-end instances, or if network traffic is severely limited, the load balancer is not being used effectively. This check currently only checks for Classic Load Balancer type within ELB service. It does not include other ELB types (Application Load Balancer, Network Load Balancer).<br><br>
            <b>Criterias</b><br>
            •	A load balancer has no active back-end instances.<br>
            •	A load balancer has no healthy back-end instances.<br>
            •	A load balancer has had less than 100 requests per day for the last 7 days.<br><br>
            <b>Potential Savings</b><br>
            Keeping an idle ELB costs around $200 per year. Removing the ELB avoids incurring this expense.<br><br>
            <b>Recommended Action</b><br>
            If load balancer has had a low request count, consider deleting the load balancer.<br><br>
            <b>How will Octo implement the recommended action?</b><br>
            Octo uses [DeleteLoadBalancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/APIReference/API_DeleteLoadBalancer.html){target="_blank"} API to delete the load balancer.<br><br>
            <b>Is rollback possible?</b><br>
            No
        </p>
    AmazonRDS
    ??? info "Amazon RDS Idle DB Instances"
        <p>
            <b>AWS Resource Type</b><br>
            RDS DB Instance<br><br>
            <b>Optimization Type</b><br>
            Usage<br><br>
            <b>Category</b><br>
            Delete<br><br>
            <b>Description</b><br>
            Checks the configuration of your Amazon Relational Database Service (Amazon RDS) for any database (DB) instances that appear to be idle.<br><br>
            <b>Criteria</b><br>
            •	An active DB instance has not had a connection in the last 7 days.<br><br>
            <b>Potential Savings</b><br>
            Savings are calculated as [Cost of RDS running hours] + [Cost of storage] - [Cost of snapshot]<br><br>
            <b>Recommended Action</b><br>
            Delete RDS DB Instance with Final Snapshot<br><br>
            <b>How will Octo implement the recommended action?</b><br>
            Octo uses [DeleteDBInstance](https://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_DeleteDBInstance.html){target="_blank"} API. A snapshot is taken first before deleting the RDS Instance.<br><br>
            <b>Is rollback possible?</b><br>
            Yes. Use the snapshot taken during the deletion process to restore the instance with its original configuration through AWS Console/AWS CLI.
        </p>
    AmazonS3
    ??? info "Amazon S3 Incomplete Multipart Upload Abort Configuration"
        <p>
            <b>AWS Resource Type</b><br>
            S3 Object<br><br>
            <b>Optimization Type</b><br>
            Usage<br><br>
            <b>Category</b><br>
            Others<br><br>
            <b>Description</b><br>
            Checks that each Amazon S3 bucket is configured with a lifecycle rule to abort multipart uploads that remain incomplete after 7 days. Using a lifecycle rule to abort these incomplete uploads and delete the associated storage is recommended.<br><br>
            <b>Criteria</b><br>
            •	The lifecycle configuration bucket does not contain a lifecycle rule to abort all multipart uploads that remain incomplete after 7 days.<br><br>
            <b>Recommended Action</b><br>
            Configure Lifecycle Rule that would cleanup all incomplete multipart uploads.<br><br>
            <b>How will Octo implement the recommended action?</b><br>
            Octo uses [PutBucketLifecycleConfiguration](https://docs.aws.amazon.com/AmazonS3/latest/API/API_PutBucketLifecycleConfiguration.html){target="_blank"} to create lifecycle configuration named `Amazon S3 Incomplete Multipart Upload Abort Configuration`<br><br>
            <b>Is rollback possible?</b><br>
            Yes. Delete `Amazon S3 Incomplete Multipart Upload Abort Configuration` lifecycle configuration.
        </p>
    AWSLambda
    ??? info "AWS Lambda Functions with High Error Rates"
        <p>
            <b>AWS Resource Type</b><br>
            Lambda Function<br><br>
            <b>Optimization Type</b><br>
            Usage<br><br>
            <b>Category</b><br>
            Others<br><br>
            <b>Description</b><br>
            Checks for Lambda functions with high error rates that might result in higher costs.
            Lambda charges are based on the number of requests and aggregate run time for your function. Function errors may cause retries that incur additional charges.<br><br>
            <b>Criteria</b><br>
            •	Functions where > 10% of invocations end in error on any given day within the last 7 days.<br><br>
            <b>Recommended Action</b><br>
            Integrate Lambda functions with Amazon CloudWatch and AWS X-Ray to leverage logs, metrics, alarms, and X-Ray tracing for rapid issue detection and identification. <br><br>
            <b>How will Octo implement the recommended action?</b><br>
            Not applicable<br><br>
            <b>Is rollback possible?</b><br>
            Not applicable
        </p>

### OCTO Generated Recommendations
!!! failure "Not Available yet."
