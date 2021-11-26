# Roles

Portainer Business Edition comes with Role-Based Access Control (RBAC) features that refine the access privileges available natively within Portainer. The RBAC feature allows you to create granular user access across all resources and all environments defined within Portainer.

## The basics

* A _role_ is a predefined set of privileges.
* _Privileges_ define the rights to perform actions.
* Users are assigned roles, and each role has specific privileges.
* To assign privileges, pair a user or team with a role then associate that pairing with an environment or environment group.
* A single user or team can have different roles for different environments in the Portainer inventory.

## Built-in roles

There are several types of roles:

* **Environment administrator** has full access within a given environment, but cannot make any changes to the infrastructure that underpins an environment (i.e. no host management), nor are they able to make changes to Portainer internal settings. Environment administrators are also unable to change ownership of resources.
* **Operator** has operational control over the resources deployed within a given environment. Operator can update, re-deploy, start and stop containers/services, check logs and console into containers, but cannot create or delete any resources.
* **Helpdesk** has read-only access to the resources deployed within a given environment but cannot make changes to any resource, nor can they open a console to a container or make changes to a container’s volumes.
* **Standard User** has complete control over the resources that a user deploys, or if the user is a member of a team, has complete control over the resources that users of that team deploy.
* **Read-Only User** has read-only access to the resources they are entitled to see (resources created by members of their team, and public resources).

![](../../.gitbook/assets/2.10-users-roles-1.png)

The **Administrator** role sits outside of the other roles and effectively acts as a 'Global Admin'. A user assigned to this role has complete control over Portainer settings, and all resources on every environment under Portainer's control.

## Viewing user access

Portainer's **Effective access viewer** lets you see what access a user has. From the menu select **Users** then select **Roles**.

![](../../.gitbook/assets/2.10-users-roles-2.gif)

Select a user from the **User** dropdown. The user's roles and their access on your environments will display. Select **Manage access** on any row to be taken to the [environment's access configuration](../environments/access.md).

![](../../.gitbook/assets/2.10-users-roles-3.png)

## Docker vs Kubernetes

Because Docker does not natively provide role-based access control, we implement our own role management in order to provide this functionality. On a Kubernetes environment, we leverage the RBAC functionality built into Kubernetes alongside our own role management to provide security and flexibility to roles and access.

For more information about how we map Portainer roles to Kubernetes roles, see our [roles and bindings documentation](../../advanced/kubernetes-roles-and-bindings.md).