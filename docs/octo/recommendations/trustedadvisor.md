# Trusted Advisor

<p>
AWS Trusted Advisor, a service from Amazon Web Services (AWS), offers real-time guidance to assist users in provisioning their resources according to AWS best practices. It provides recommendations across categories like cost optimization, performance, security, and fault tolerance. Octo leverages its API to fetch and display recommendations specifically from the cost optimization category.</p>

!!! note "Trusted Advisor Recommendations are accessible exclusively to users subscribed to the ==Business==, ==Enterprise On-Ramp==, or ==Enterprise Support plans==."

<p>Below is the list of recommendations under cost optimization category that are supported by octo.
</p>
## AmazonEBS
??? info "Underutilized Amazon EBS Volumes"
    ### Underutilized Amazon EBS Volumes
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
## AmazonEC2
??? info "Amazon EC2 Instances Stopped"
    ### Amazon EC2 Instances Stopped
    <p>
        <b>AWS Resource Type</b><br>
        EC2 Instance<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Delete<br><br>
        <b>Description</b><br>
        Checks if there are Amazon EC2 instances that have been stopped for more than 30 days.<br><br>
        <b>Criteria</b><br>
        •  There are Amazon EC2 instances stopped for more than the allowed number of days. <br><br>
        <b>Potential Savings</b><br>
        It can lead to savings by eliminating storage costs for associated EBS volumes and avoiding unnecessary charges if the instance is covered by a Reserved Instance or Savings Plan. <br><br>
        <b>Recommended Action</b><br>
        Terminate EC2 instance<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Octo uses [TerminateInstances](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_TerminateInstances.html){target="_blank"} API to terminate the EC2 instance.<br><br>
        <b>Is rollback possible?</b><br>
        No
    </p>
??? info "Low Utilization Amazon EC2 Instances"
    ### Low Utilization Amazon EC2 Instances
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
    ### Unassociated Elastic IP Addresses
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
??? info "Amazon EC2 Reserved Instance Lease Expiration"
    ### Amazon EC2 Reserved Instance Lease Expiration
    <p>
        <b>AWS Resource Type</b><br>
        EC2 Reserved Instances<br><br>
        <b>Optimization Type</b><br>
        Rate<br><br>
        <b>Category</b><br>
        Reserved Instance<br><br>
        <b>Description</b><br>
        Checks for Amazon EC2 Reserved Instances that are scheduled to expire within the next 30 days, or have expired in the preceding 30 days.
        Reserved Instances don't renew automatically. You can continue using an Amazon EC2 instance covered by the reservation without interruption, but you will be charged On-Demand rates. New Reserved Instances can have the same parameters as the expired ones, or you can purchase Reserved Instances with different parameters.<br><br>
        <b>Criteria</b><br>
        •	The Reserved Instance lease expires in less than 30 days.<br>
        •   The Reserved Instance lease expired in the preceding 30 days.<br><br>
        <b>Recommended Action</b><br>
        Consider purchasing a new Reserved Instance to replace the one that is nearing the end of its term.<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not applicable
        <br><br>
        <b>Is rollback possible?</b><br>
        Not applicable
    </p>
## AmazonComprehend
??? info "Amazon Comprehend Underutilized Endpoints"
    ### Amazon Comprehend Underutilized Endpoints
    <p>
        <b>AWS Resource Type</b><br>
        Comprehend Endpoints<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Delete<br><br>
        <b>Description</b><br>
        Checks the throughput configuration of your endpoints. This check alerts you when endpoints are not actively used for real-time inference requests. An endpoint that isn’t used for more than 15 consecutive days is considered underutilized. All endpoints accrue charges based on both the throughput set, and the length of time that the endpoint is active.<br><br>
        <b>Criteria</b><br>
        •	The endpoint is active, but hasn’t been used for real-time inference requests in the past 15 days.
        <br><br>
        <b>Recommended Action</b><br>
        If the endpoint has a scaling policy defined and hasn’t been used in the past 30 days, consider deleting the endpoint and using asynchronous inference. <br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not implemented yet.<br><br>
        <b>Is rollback possible?</b><br>
        Not implemented yet.
    </p>
## AWSELB
??? info "Idle Load Balancers"
    ### Idle Load Balancers
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
## AmazonRDS
??? info "Amazon RDS Idle DB Instances"
    ### Amazon RDS Idle DB Instances
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
## AmazonS3
??? info "Amazon S3 Incomplete Multipart Upload Abort Configuration"
    ### Amazon S3 Incomplete Multipart Upload Abort Configuration
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
??? info "Amazon S3 Bucket Lifecycle Policy Configured"
    ### Amazon S3 Bucket Lifecycle Policy Configured
    <p>
        <b>AWS Resource Type</b><br>
        S3 Bucket<br><br>
        <b>Optimization Type</b><br>
        Others<br><br>
        <b>Category</b><br>
        Others<br><br>
        <b>Description</b><br>
        Checks if an Amazon S3 bucket has a lifecycle policy configured. An Amazon S3 lifecycle policy ensures that Amazon S3 objects inside the bucket are stored cost-effectively throughout their lifecycle. This is important for meeting regulatory requirements for data retention and storage. The policy configuration is a set of rules that define actions applied by the Amazon S3 service to a group of objects. A lifecycle policy allows you to automate transitioning objects to lower-cost storage classes or deleting them as they age. For example, you can transition an object to Amazon S3 Standard-IA storage 30 days after creation, or to Amazon S3 Glacier after 1 year.<br><br>
        <b>Criteria</b><br>
        • Amazon S3 bucket has no lifecycle policy configured.
        <br><br>
        <b>Recommended Action</b><br>
        Make sure that you have a lifecycle policy configured in your Amazon S3 bucket.<br>
        If your organization does not have a retention policy in place, consider using Amazon S3 Intelligent-Tiering to optimize cost.<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not applicable.<br><br>
        <b>Is rollback possible?</b><br>
        Not applicable.
    </p>
??? info "Amazon S3 version-enabled buckets without lifecycle policies configured"
    ### Amazon S3 version-enabled buckets without lifecycle policies configured
    <p>
        <b>AWS Resource Type</b><br>
        S3 Bucket<br><br>
        <b>Optimization Type</b><br>
        Others<br><br>
        <b>Category</b><br>
        Others<br><br>
        <b>Description</b><br>
        Checks if Amazon S3 version-enabled buckets have a lifecycle policy configured.<br><br>
        <b>Criteria</b><br>
        • An Amazon S3 version-enabled bucket with doesn't have a lifecycle policy configured.
        <br><br>
        <b>Recommended Action</b><br>
        Configure lifecycle policies for your Amazon S3 buckets to manage your objects so that they are stored cost effectively throughout their lifecycle. <br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not applicable.<br><br>
        <b>Is rollback possible?</b><br>
        Not applicable.
    </p>

## AWSLambda
??? info "AWS Lambda Functions with High Error Rates"
    ### AWS Lambda Functions with High Error Rates
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
??? info "AWS Lambda Functions with Excessive Timeouts"
    ### AWS Lambda Functions with Excessive Timeouts
    <p>
        <b>AWS Resource Type</b><br>
        Lambda Function<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Others<br><br>
        <b>Description</b><br>
        Checks for Lambda functions with high timeout rates that might result in high cost.
        Lambda charges based on run time and number of requests for your function. Function timeouts result in errors that may cause retries. Retrying functions will incur additionally request and run time charges.<br><br>
        <b>Criteria</b><br>
        •	Functions where > 10% of invocations end in an error due to a timeout on any given day within the last 7 days.<br><br>
        <b>Recommended Action</b><br>
        Inspect function logging and X-ray traces to determine the contributor to the high function duration. Implement logging in your code at relevant parts, such as before or after API calls or database connections. By default, AWS SDK clients timeouts may be longer than the configured function duration. Adjust API and SDK connection clients to retry or fail within the function timeout. If the expected duration is longer than the configured timeout, you can increase the timeout setting for the function. <br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not applicable<br><br>
        <b>Is rollback possible?</b><br>
        Not applicable
    </p>
## AmazonRedshift
??? info "Underutilized Amazon Redshift Clusters"
    ### Underutilized Amazon Redshift Clusters
    <p>
        <b>AWS Resource Type</b><br>
        Redshift Cluster<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Delete<br><br>
        <b>Description</b><br>
        Checks your Amazon Redshift configuration for clusters that appear to be underutilized.
        If an Amazon Redshift cluster has not had a connection for a prolonged period of time, or is using a low amount of CPU, you can use lower-cost options such as downsizing the cluster, or shutting down the cluster and taking a final snapshot. Final snapshots are retained even after you delete your cluster.<br><br>
        <b>Criteria</b><br>
        •	A running cluster has not had a connection in the last 7 days.<br>
        •   A running cluster had less than 5% cluster-wide average CPU utilization for 99% of the last 7 days.
        <br><br>
        <b>Recommended Action</b><br>
        Consider shutting down the cluster and taking a final snapshot. <br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not implemented yet.<br><br>
        <b>Is rollback possible?</b><br>
        Not implemented yet.
    </p>
## Others
??? info "AWS Account Not Part of AWS Organizations"
    ### AWS Account Not Part of AWS Organizations
    <p>
        <b>AWS Resource Type</b><br>
        AWS Accounts<br><br>
        <b>Optimization Type</b><br>
        Others<br><br>
        <b>Category</b><br>
        Others<br><br>
        <b>Description</b><br>
        Checks if an AWS account is part of AWS Organizations under the appropriate management account.<br><br>
        AWS Organizations is an account management service for consolidating multiple AWS accounts into a centrally-managed organization. This enables you to centrally structure accounts for billing consolidation and implement ownership and security policies as your workloads scale on AWS.<br><br>
        You can specify the management account id using the MasterAccountId parameter of the AWS Config rules.<br><br>
        <b>Criteria</b><br>
        • This AWS account is not part of AWS Organizations.
        <br><br>
        <b>Recommended Action</b><br>
        Add this AWS account as part of AWS Organizations. <br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not applicable.<br><br>
        <b>Is rollback possible?</b><br>
        Not applicable.
    </p>
??? info annotate "AWS Well-Architected high risk issues for cost optimization"
    ### AWS Well-Architected high risk issues for cost optimization
    <p>
        <b>Optimization Type</b><br>
        Others<br><br>
        <b>Category</b><br>
        Others<br><br>
        <b>Description</b><br>
        Checks for high risk issues (HRIs) for your workloads in the cost optimization pillar. This check is based on your AWS-Well Architected reviews. Your check results depend on whether you completed the workload evaluation with AWS Well-Architected.<br><br>
        <b>Criteria</b><br>
        • At least one active high risk issue was identified in the cost optimization pillar for AWS Well-Architected.
        <br><br>
        <b>Recommended Action</b><br>
        AWS Well-Architected detected high risk issues during your workload evaluation. These issues present opportunities to reduce risk and save money. Sign in to the [AWS Well-Architected](https://console.aws.amazon.com/wellarchitected){target=_blank} tool to review your answers and take action to resolve your active issues. <br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not applicable.<br><br>
        <b>Is rollback possible?</b><br>
        Not applicable.
    </p>
