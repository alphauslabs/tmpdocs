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