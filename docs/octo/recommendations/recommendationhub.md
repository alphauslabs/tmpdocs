# Recommendation Hub

Google Cloud Platform also offers a recommendation system that provides actionable insights to help users optimize their cloud infrastructure.  Leveraging analyses of resource utilization, configurations, and established best practices, it generates personalized recommendations tailored to each environment. Like AWS Trusted Advisor, GCP’s recommendations are categorized into cost optimization, performance, reliability, security, and sustainability, giving users a comprehensive view of potential improvements.

In Octo, all cost optimization recommendations from GCP Recommendation Hub will be collected and displayed in a centralized view. This allows users to quickly identify opportunities for savings and more efficient resource allocation, aligning with their financial and operational goals.

## Compute Engine
??? info "Idle Virtual Machine" 
    ### Idle Virtual Machine
    <b>GCP Resource Type</b><br>
    Virtual Machine<br><br>
    <b>Optimization Type</b><br>
    Usage<br><br>
    <b>Category</b><br>
    Stop<br><br>
    <b>Description</b><br>
    Compute Engine provides idle VM recommendations to help users identify virtual machine (VM) instances that have not been used over the previous 1 to 14 days. Users can use idle VM recommendations to find and stop idle VM instances to reduce wasting resources and reduce your compute bill.<br><br>
    <b>Criteria</b><br>
    •   Compute Engine generates recommendations about idle VM instances based on historical usage metrics. By default, the historical observation period is 14 days, or, for new VMs, starting one day after VM creation. By changing the default observation period, users can customize the recommendations that they receive. For more information, see [Configure idle VM recommendations](https://cloud.google.com/compute/docs/instances/configuring-idle-vm-recommendations){target=_blank}
    <br><br>
    <b>Potential savings</b><br>
    Save 100% of the cost of that vm. For more information, see [VM pricing](https://cloud.google.com/compute/vm-instance-pricing){target=_blank}.<br><br>
    <b>Recommended Action</b><br>
    Stop Vitrual Machine<br><br>
    <b>How will Octo implement the recommended action?</b><br>
    Not implemented yet.<br><br>
    </p>
??? info "Idle IP Address" 
    ### Idle IP Address
    <p>
    <b>GCP Resource Type</b><br>
    Compute Engine IP Address<br><br>
    <b>Optimization Type</b><br>
    Usage<br><br>
    <b>Category</b><br>
    Delete<br><br>
    <b>Description</b><br>
    This recommendation identifies IP addresses that are allocated but not actively in use within your Google Cloud environment. Idle IP addresses can incur unnecessary costs without providing any value to your infrastructure. Releasing or deleting these addresses can help reduce expenses and optimize resource allocation.<br><br>
    <b>Criterias</b><br>
    The IP address hasn't been attached to any resource for at least 15 days.<br><br>
    <b>Potential savings</b><br>
    Save 100% of the cost of that IP address. For more information, see [External IP address pricing](https://cloud.google.com/vpc/network-pricing#ipaddress){target=_blank}.<br><br>
    <b>Recommended Action</b><br>
    Release or delete IP Address.<br><br>
    <b>How will Octo implement the recommended action?</b><br>
    Not implemented yet.<br><br>
    </p>
??? info "Idle Persistent Disk" 
    ### Idle Persistent Disk
    <p>
    <b>GCP Resource Type</b><br>
    Compute Engine Disk<br><br>
    <b>Optimization Type</b><br>
    Usage<br><br>
    <b>Category</b><br>
    Delete<br><br>
    <b>Description</b><br>
    This recommendation highlights persistent disks in Google Cloud that are provisioned but not currently attached to any virtual machine. Unused disks continue to incur storage charges, adding to overall costs without delivering value.<br><br>
    <b>Criterias</b><br>
    There are two approaches to address this recommendation effectively.<br><br>
    First criteria: <br>
    •   The Persistent Disk was created at least 15 days ago.<br>
    •   The Persistent Disk was never attached to a VM.<br>
    •   The Persistent Disk is blank.<br>
    •   The Persistent Disk isn't bound to GKE Pods.<br><br>
    Second criteria:<br>
    •   The Persistent Disk was detached for at least 15 days.<br>
    •   The Persistent Disk isn't bound to GKE Pods.
    <br><br>
    <b>Potential savings</b><br>
    If the first criteria are met, users can save 100% of the cost of that disk. If the second criteria are met, maintenance costs can be reduced by 35% to 92%.<br><br>
    <b>Recommended Action</b><br>
    For the first option, users should proceed with the permanent deletion of the disk. For the second criteria, users are advised to create a snapshot of the persistent disk before deleting it. This approach allows users to incur a lower cost, as they will be charged for the snapshot rather than the disk itself.<br><br>
    <b>How will Octo implement the recommended action?</b><br>
    Not yet implemented.<br><br>
    <b>Is rollback possible?</b><br>
    Users cannot restore the disk for the first option, as it is permanently deleted. However, for the second option, users can restore it using the snapshot created.
    </p>
??? info "Idle Custom Image" 
    ### Idle Custom Image
    <p>
    <b>GCP Resource Type</b><br>
    Compute Engine Custom Image<br><br>
    <b>Optimization Type</b><br>
    Usage<br><br>
    <b>Category</b><br>
    Delete<br><br>
    <b>Description</b><br>
    This recommendation identifies custom images stored in Google Cloud that are not actively in use. Retaining unused images can lead to unnecessary storage costs over time. Removing idle custom images helps reduce storage expenses and ensures that only relevant resources are maintained.<br><br>
    <b>Criteria</b><br>
    •   The image wasn't used to create a disk for at least 15 days.<br>
    •   The image isn't used in any instance template.
    <br><br>
    <b>Potential savings</b><br>
    Save 100% of the cost of that image. For more information, see [Disk and image pricing](https://cloud.google.com/compute/disks-image-pricing){target=_blank}.<br><br>
    <b>Recommended Action</b><br>
    Release or delete IP Address.<br><br>
    <b>How will Octo implement the recommended action?</b><br>
    Not implemented yet.<br><br>
    </p>

## Kubernetes Engine
??? info "Idle GKE Cluter" 
    ### Idle GKE Cluster
    <p>
    <b>GCP Resource Type</b><br>
    GKE Cluster<br><br>
    <b>Optimization Type</b><br>
    Usage<br><br>
    <b>Category</b><br>
    Delete<br><br>
    <b>Description</b><br>
    This recommendation identifies Google Kubernetes Engine (GKE) clusters that are currently not being utilized. Idle GKE clusters can lead to unnecessary operational costs, as they incur charges even when no workloads are running.<br><br>
    <b>Criterias</b><br>
    •   There are zero Pods in the Running state outside of the kube-system and gmp-system namespace in the cluster metrics events logs for the cluster during the last 30 days.<br>
    •   There are zero nodes or zero node pools in the cluster metrics events logs for the cluster during the last 30 days<br>
    •   CPU utilization (averaged over 1 hour) is below 7% and there has been no change in object count during the last 30 days.
    <br><br>
    <b>Potential savings</b><br>
    Save 100% of the cost of that cluster. For more information, see [Kubernetes Engine pricing](https://cloud.google.com/kubernetes-engine/pricing#google-kubernetes-engine-pricing){target=_blank}.<br><br>
    <b>Recommended Action</b><br>
    Delete GKE Cluster
    !!! warning "Considerations when deleting idle clusters"
        Before you delete an idle cluster recommended by the Idle Cluster Recommender, consider the following possibilities:<br><br>
        1. Does anyone use the cluster? For example, a cluster might be intentionally idle if its purpose is to maintain failover capacity.<br>
        2. Should the cluster be scaled down instead of deleted? For example, a cluster running a useful workload might have low utilization and be identified as idle because more resources were provisioned than necessary.
    <b>How will Octo implement the recommended action?</b><br>
    Not implemented yet.<br><br>
    </p>
