# AWS
Octo offers a powerful cost optimization recommendation feature designed to help AWS users reduce cloud spending. Our proprietary logic and criteria analyze your AWS resources to identify optimization opportunities, such as rightsizing, migrating, and eliminating underutilized resources. Unlike standard tools, Octo provides tailored recommendations based on your unique usage patterns and business needs. The feature supports a wide range of AWS services, ensuring comprehensive cost-saving insights. With Octo, users can easily take actionable steps to maximize their cloud cost efficiency.

!!! info ""
    There are more recommendations to come, enhancing Octo’s ability to help users optimize their AWS costs effectively.

## AmazonEC2
??? info "Change EC2 instance type from Intel to AMD"
    ### Change EC2 Instance Type from Intel to AMD
    <p>
        <b>AWS Resource Type</b><br>
        EC2 instance<br><br>
        <b>Optimization Type</b><br>
        Usage<br><br>
        <b>Category</b><br>
        Migrate<br><br>
        <b>Description</b><br>
        Migrating an EC2 instance from Intel to AMD processors can help reduce costs without compromising performance. AMD-based instances offer a cost-effective alternative, typically providing similar compute power at a lower price compared to Intel-based instances. This migration is suitable for workloads that do not have processor-specific dependencies. By switching to AMD instances, users can optimize their cloud expenditure while maintaining workload efficiency, making it an effective strategy for overall cost reduction.<br><br>
        <b>Criterias</b><br>
        •	Instance families deemed safe for migration from Intel to AMD include: T3, C5, M5, R5, C6i, M6i, and R6i.<br>
        •   Instance types that have reservations are excluded.<br>
        •   Instance types that are not long-lived are excluded (e.g., part of Auto Scaling Group or EMR).<br>
        •   Instances with measured peak EBS throughput in the last 30 days that exceed the EBS bandwidth of the AMD counterpart are excluded.<br>
        •   Instances for which we do not have at least 30 days of CPU and IO throughput data are excluded.<br>
        •   For instance, types T3, C5, M5, and R5 make sure CPU utilization in the last 30 days was less than 80% (due to a lower clock frequency of the AMD counterpart).<br><br>
        <b>Potential Savings</b><br>
        The AMD-based EC2 instances that AWS offers are typically about 10% cheaper than the equivalent Intel EC2 instances.<br><br>
        <b>Recommended Action</b><br>
        Change EC2 Intel instance type to AMD<br><br>
        <b>How will Octo implement the recommended action?</b><br>
        Not implemented yet.<br><br>
        <b>Is rollback possible?</b><br>
        Not implemented yet.
    </p>
