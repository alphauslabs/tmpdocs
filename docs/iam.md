# Identity & Access Management (IAM)

## Users
There are two types of Alphaus users; root users and subusers. Root users are account owners and super admins. These are the accounts you register to Alphaus and are in email address form. Subusers are users that are created by root users and are typically given minimal access to perform specific roles although subusers can also be admins.

## RBAC
Alphaus RBAC is a organization-wide role-based access control system that provides fine-grained access management to Alphaus features and resources. In using Alphaus RBAC, you can grant only the amount of access to users that they need to perform their jobs.

RBAC is defined around users, namespaces, roles, and permissions. Users can be actual users in your organization, or a virtual user used in scripts or automation codes. Roles are job functions or groups that have a certain level of authority, or a list of permissions attached to it. Examples are `Admin`, `Developers`, etc. You can assign up to five (5) roles to a user per namespace.

RBAC roles and permissions are isolated based on namespaces. What this means is that a role can only be created under a specific namespace, with namespace-specific permissions attached to it.

Root users are always super admins, or have unrestricted access across namespaces. Typically, root users should create subusers and assign specific roles to them.

## Namespaces
Below is the list of supported namespaces under Alphaus RBAC:
* `ripple` - for Ripple;
* `wave` - for Wave(Pro);
* `users` - for user management; and
* `rbac` - for RBAC management

## Permissions
For the latest permissions, check out [here](https://github.com/mobingi/rbac-permissions).
