---
title: Cloud Naming Convention | stepan.wtf
menu_order: 1
post_status: publish
post_excerpt: ''
slug: cloud-naming-convention-or-stepanwtf
taxonomy:
  category:
    - hacker-news
  post_tag:
    - HN
custom_fields:
  ttr: 363
  source: stepan.wtf
  url: 'https://stepan.wtf/cloud-naming-convention/'
---
Thu, Oct 10, 2019 [cloud](https://stepan.wtf/tags/cloud) / [gcp](https://stepan.wtf/tags/gcp) / [architecture](https://stepan.wtf/tags/architecture) / [terraform](https://stepan.wtf/tags/terraform)

Cloud Naming Convention
=======================

Consistent naming strategy is important and should be an essential part of any cloud effort. Sadly it’s often overlooked. It might seem like a luxury when you run a few “pet” servers, but it quickly becomes critical as the number of managed resources grows. It is the first step in achieving even basic levels of consistency and prerequisite to establishing any sort of cloud governance.

After reading this article, you’ll hopefully know how to get from:

    1
    2
    3
    4
    5
    6
    

    $ gcloud container clusters list \
        --format 'value(name)'
    k8s-cluster
    k8s-cluster
    k8s-cluster
    k8s-cluster
    

to something like:

    1
    2
    3
    4
    5
    6
    

    $ gcloud container clusters list \
        --format 'value(name)'
    ste-blog-p-kcl-euwe4-primary
    ste-webshop-d-kcl-euwe4-primary
    ste-webshop-p-kcl-euwe4-primary
    ste-webshop-p-kcl-usce1-primary
    

The latter will quickly tell us what type of resources are we dealing with, to which project and environment they belong, where are they located and whether they’re functionally equivalent to each other.

Benefits
--------

Consistent and descriptive naming of resources has many benefits:

*   Indicates the role and ownership of a resource.
*   Helps formalize expectations and promote consistency within an infrastructure.
*   Prevents name clashes when resource names must be unique.
*   Makes resources easier to locate.
*   Reduces effort to understand code and allows developers to focus on more important aspects than arguing over naming standards.
*   Allows to sort and filter resources quickly.
*   Is a prerequisite for establishing any successful cloud governance and automated policy evaluation or enforcement.

  
I’m not quite sure when I first came across this quote, but it since became one of my favourites. Martin Fowler [attributes it to Phil Karlton](https://martinfowler.com/bliki/TwoHardThings.html).

> There are only two hard things in Computer Science: cache invalidation and naming things.Phil Karlton

Main Properties
---------------

Good naming convention must provide clarity and work in both directions:

*   Clearly define how newly created resources should be named.
*   Identify and indicate the purpose and ownership of existing resources.

We’ll focus on how a naming convention for cloud-level resources should look like. GCP is used in our examples, but the concepts and strategies are generic and can be easily adapted to other cloud providers.

Naming Restrictions
-------------------

When designing your naming convention, you should take into account limitations imposed by the cloud provider. Each resource comes with a set of naming restrictions. The rule of thumb is to keep it short and simple (use only letters and numbers for individual components, keep `-` as separator).

GCP limits name length for most of the resources to 62 or 63 characters, Project IDs are limited to 30. Resources must have unique names, either globally or within a given scope. Some resources have additional constraints to take into consideration (e.g. GCP Projects can’t be immediately deleted).

Global Naming Pattern
---------------------

First we establish naming pattern that all directly managed resources should follow - Global Naming Pattern.

**`[prefix]-[project]-[env]-[resource]-[location]-[description]-[suffix]`**

Component

Description

Req.

Constraints

**`prefix`**

Fixed prefix

✔

len 3, fixed

**`project`**

Project name

✔

len 4-10, a-z0-9

**`env`** .

Environment

✔

len 1, a-z, enum

**`resource`**

Resource type

✔

len 3, a-z, enum

**`location`**

Resource location

✗

len 1-6, a-z0-9

**`description`**

Additional description

✗

len 1-20, a-z0-9

**`suffix`**

Random suffix

✗

len 4, a-z0-9

Let’s go over the individual components more in detail.

### Fixed Prefix

This is a fixed value prefix used for all resources. Typically some form of abbreviation for your organization name.

*   `ste` for Stepan
*   `ggl` for Google

### Project Name

This is different from a GCP Project. Typically one Project will have multiple GCP Projects. We’re using flat hierarchy and Project serves as the main mechanism of organizing resources into groups. I like using flat hierarchy as it’s very universal and flexible to fit pretty much any organizational structure. You might consider replacing this with some other form of group (e.g. team, product), but in my experience it never quite works in the long term.

*   `blog` for blog project
*   `webshop` for web shop project

### Environment

Resources belong to deployment environments. It’s beneficial to establish a common set of names used across your organization.

*   `d` for development
*   `s` for staging
*   `p` for production

### Resource Type

I’ve tried various mechanisms over the time to construct the abbreviation for resources - most consistent results are achieved if the names are based on the API resource names. Abbreviation of the given resource type. In GCP I tend to use three letters.

For larger and more frequently used APIs (e.g. Compute, Kubernetes) first letter stands for the API and the remaining two for the resource type. For APIs with fewer resources, it’s the other way around. I know this is not a completely deterministic rule, but this will always be a compromise to it short and usable.

*   `cin` - Compute Engine VM Instance
*   `cig` - Compute Engine VM Instance Group
*   `kcl` - Kubernetes Engine Cluster
*   `bqd` - BigQuery Dataset

### Resource Location

Location is required when there’s a possibility to create a given resource in different locations.

*   **Regional** - five letter acronym (two letters for the continent, two for cardinal directions, 1 digit)
*   **Zonal** - six letters - Regional + zone
*   **Global** - `g`
*   **Multi- and Dual-regional** - follow GCP’s own naming (two letters for multi and 4 letters for dual-regional)

*   `euwe1` - europe-west1 region
*   `nane1` - northamerica-northeast1 region
*   `euwe1a` - europe-west1 region, zone a
*   `eu` - Europe multi-region
*   `eur4` - europe-north1 and europe-west4 dual-region

### Additional Description

A description used to distinguish between resources of the same type but different roles. For example a group of servers with a different purpose - `frontend` and `backend`. This should not be used to differentiate between multiple instances of the same purpose resource, use `suffix` instead.

It’s also beneficial to agree on generic keywords used for description, when there is no better, more specific, term available. This avoids many different names like `main`, `core`, `common`, `this` and similar. Often good strategy is to use the Latin ordinal sequence, i.e. `primary`, `secondary`, `tertiary`, etc.

*   `frontend`
*   `backend`
*   `kafka`

### Random Suffix

I typically use a 2-byte number represented in hexadecimal form

*   good for readability and easily generated with Terraform `random_id` resource. Use Suffix to differentiate resource from its peers when there are multiple instances, or when there’s a requirement for uniqueness.

*   `a49f`

### Examples

Let’s go over several full examples of how resources should be named based on the above established pattern.

All the examples use prefix `ste` and belong to Production (`p`) environment of project `blog`.

*   Set of functionally equivalent Compute Instances
    *   `ste-blog-p-cin-euwe1a-nginx-408f`
    *   `ste-blog-p-cin-euwe1a-nginx-c338`
    *   `ste-blog-p-cin-euwe1a-nginx-d7aa`
*   VPC (Network) and Subnet
    *   `ste-blog-p-cne-primary`
    *   `ste-blog-p-csn-euwe1-primary`
*   GKE Regional Cluster and Node Pool
    *   `ste-blog-p-kcl-usce1-primary`
    *   `ste-blog-p-knp-usce1-primary-cbe7`

GCP Projects
------------

Projects (and Folders) are considered resource containers for the purpose of this naming convention and therefore omit the `resource` part of the name.

You can notice GCP does this by default for projects created via console - e.g. `rapid-depot-253717`. Project IDs in GCP have to be globally unique and cannot be deleted immediately. This is unfortunate for automation, as you can’t create a project with the same name right after it has been deleted. And that’s why we include the unique random suffix part.

_Folders_: We don’t use GCP folders to organize projects. I generally believe that keeping it simple and flat is beneficial more often than not. However, if you want to further structure your resources, consider adding an additional component to your naming pattern, such as `[org_group]`. Folders can then follow `[prefix]-[org-group]` pattern. GCP also allows configuring Project Name. I recommend to set this to the same value as Project ID and forget about it. For all the practical purposes you’ll reference the Projects by their IDs.

GCP Projects will therefore be named following the `[prefix]-[project]-[env]-[suffix]` pattern.

*   `ste-blog-p-a8d6`
*   `abc-research-d-ab45`

[xkcd - Permanence](https://xkcd.com/910/) by Randall Munroe [![](https://stepan.wtf/imgs/cloud-naming-convention-xkcd.png)](https://stepan.wtf/#66ec467cfa84e7c7ceea8e9bd57df35b-lightbox)[![](https://stepan.wtf/imgs/cloud-naming-convention-xkcd.png)](https://stepan.wtf/#_)

Exceptions
----------

There will always be exceptions where it’s not possible to follow the Global Naming Pattern (for example resource does not allow `-` in the name) or when it simply doesn’t make sense. A subset of the full pattern should be used if possible and all exceptions documented.

### Service Accounts

Service accounts follow the `[resource]-[description]` pattern only, as the project is already included in the part after `@` and therefore there’s no need to repeat that bit,

*   `svc-frontend@ste-blog-p-a8d6.iam.gserviceaccount.com`

### IAM and Groups

This is a complex topic, perhaps for another article, but you should establish a naming convention for groups and a strategy on how to assign permissions. As a rule of thumb, never assign permissions directly to individuals, but to groups only.

Labelling Resources
-------------------

You should also cover the use of labels (or tags). A good one is to add information to further categorize your resources, such as `cost-center`. Labels are also helpful in situations when you can’t manage resource names directly, but you can manage a set of labels that is propagated to the child resources (e.g. GKE Cluster labels or Instance Groups).

Do not duplicate information already contained in your naming convention (such as `project`) or create large numbers of unique labels with information that can be obtained from the objects themselves (such as `creationTimestamp`).

DNS
---

DNS naming convention across your infrastructure is again a larger topic, but you should definitely have one. A simple strategy can be creating a subdomain for each GCP project in the `[project]-[env].<common_dns_domain>` form. DNS records created for given resources should then follow the `[resource]-[resource_location]-[description]-[suffix]` part of the Global Naming pattern and therefore mirror the resource name.

This allows for easy subdomain delegation to individual GCP projects.

*   DNS record for VM with name `ste-blog-p-cin-euwe1b-frontend-a6bc` would be `cin-euwe1b-frontend-a6bc.blog-p.stepan.wtf`

Summary
-------

You should establish a consistent naming convention as one of the first things when you start using cloud or on a new project. It’s one of those things that are really easy to do in the beginning, but much more difficult to fix later on. And you’ll benefit from it every day.

The key to success with naming conventions is establishing them early on and ruthlessly following across your entire infrastructure. Automation helps a lot.

As usual, there’s no silver bullet and the actual naming convention should always be tailored to your environment. The main point is having one! And I hope this post gives you a head start.

Thanks for making it all the way till here. I wouldn’t blame you if you think by now that I have a serious OCD (and I probably do), but try to work in an environment with 120 Kubernetes clusters and every single one of them named simply just `cluster`!

Good luck on your cloud journey and I would love to hear about your experience with naming things. You can follow me on [@stepanstipl](https://twitter.com/stepanstipl).

References
----------

1.  GCP - Creating and Managing Projects: [https://cloud.google.com/resource-manager/docs/creating-managing-projects#identifying\_projects](https://cloud.google.com/resource-manager/docs/creating-managing-projects#identifying_projects)
2.  GCP - Best practices for enterprise organizations: [https://cloud.google.com/docs/enterprise/best-practices-for-enterprise-organizations](https://cloud.google.com/docs/enterprise/best-practices-for-enterprise-organizations)
3.  GCE API - REST reference: [https://cloud.google.com/compute/docs/reference/rest/v1/](https://cloud.google.com/compute/docs/reference/rest/v1/)
4.  GKE API - REST reference: [https://cloud.google.com/kubernetes-engine/docs/reference/rest/](https://cloud.google.com/kubernetes-engine/docs/reference/rest/)
5.  GKE - Creating and managing labels: [https://cloud.google.com/kubernetes-engine/docs/how-to/creating-managing-labels](https://cloud.google.com/kubernetes-engine/docs/how-to/creating-managing-labels)
6.  Azure - Recommended naming and tagging conventions: [https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/considerations/naming-and-tagging](https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/considerations/naming-and-tagging)
7.  AWS - Tagging Strategies: [https://aws.amazon.com/answers/account-management/aws-tagging-strategies/](https://aws.amazon.com/answers/account-management/aws-tagging-strategies/)
