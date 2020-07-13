# Module 2: Getting Started with Google Cloud Platform

- All the GCP resources whether they're virtual machines, cloud storage buckets, tables and big query or anything else in GCP are organized into ***projects***. Optionally, these projects may be organized into ***folders***. Folders can contain other folders. All the folders and projects used by your organization can be brought together under an ***organization*** node. Policies are *inherited downwards* in the hierarchy.
- Each project is a separate compartment and each resource belongs to exactly one. Projects can have different owners and users - they're built separately and they're managed separately.
- Each GCP project has a ***name*** and a **project ID** that we choose. The project ID is *a permanent, unchangeable identifier* and it has to be unique across GCP. On the other hand, project names are for our convenience and we can assign and update them.
- The policies implemented at a higher level in the hierarchy can't take away access that's granted at a lower level.
- ***IAM*** lets administrators authorize who can take action on specific resources. An IAM policy has a ***who*** part, a ***can do what*** part, and an ***on which resource*** part.
- The ***who*** part names the user or users you're talking about. The "who" part of an IAM policy can be defined either by a *Google account*, a *Google group*, a *Service account*, an *entire G Suite*, or a *Cloud Identity domain*.
- The ***can do what*** part is defined by an IAM role. An IAM role is a collection of *permissions*. Permissions are grouped together into a role that makes them easier to manage
- There are three kinds of roles in Cloud IAM:
  - ***Primitive roles*** are broad. We apply them to a GCP project and they affect all resources in that project. These are the **owner**, ***editor***, and **viewer** roles.
    - A *viewer* of a given resource, *can examine it but not change its state*.
    - An *editor* of a given resource, can do everything a viewer can do, plus *change its state*.
    - An *owner* of a given resource, can do everything an editor can do, plus *manage roles and permissions on the resource*. The owner role on a project also lets you do one more thing: *set up billing*.
    - A *billing administrator* can *control the billing* for a project without the right to change the resources in the project.
  - ***Predefined roles***, GCP services offer their own sets of predefined roles and they define where those roles can be applied.
  - ***Custom roles***, they can only be used at the *project or organization* levels and they can't be used at the folder level.
- ***Service accounts*** control ***server-to-server*** interactions. Service accounts are named with an email address. But instead of passwords, they *use cryptographic keys to access resources*.
- Service accounts can be used to *authenticate from one service to another*. And they can also be used to *control privileges used by resources*. A service account *is a resource*, so it can have IAM policies on its own attached to it.