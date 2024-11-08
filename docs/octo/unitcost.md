# Unit Cost Documentation

## Introduction

Unit cost is a critical concept in cost management, particularly in cloud environments. It refers to the cost associated with a single unit, which could be a product, a customer, an environment, or any other entity that consumes resources. Understanding unit costs helps organizations allocate expenses more accurately, identify cost-saving opportunities, and improve financial transparency.

## Purpose

The purpose of this documentation is to provide a comprehensive guide on unit cost, its components, and methodologies for calculating and managing unit costs in cloud environments. This will address common challenges faced by organizations in breaking down costs, especially when multiple units share services.

## Components of Unit Cost

In unit cost analysis, there are two fundamental concepts: **Unit Types** and **Unit Items**.

### Unit Types

Unit Types represent the different categories or entities for which you want to break down costs. These could include:

- **Products**: The various products offered by the organization.
- **Customers**: The different customers or customer segments served.
- **Environments**: Distinct operational environments, such as development, testing, and production.

**Naming Conventions**
- Only alphanumeric characters, spaces and special characters such as  . : + = @ _ / are allowed.
- Consecutive special characters or spaces are not allowed.
- Name should be unique from other units.

### Unit Items

Under each Unit Type, there are specific Unit Items. These are the individual entities within the Unit Type for which costs need to be divided and tracked. For example:

- **Products**: Individual products like "Octo," "Wave," and "Ripple."
- **Customers**: Specific customers or groups of customers.
- **Environments**: Different operational environments such as "Development Environment," "Testing Environment," and "Production Environment."

**Naming Conventions**
- Only alphanumeric characters, spaces and special characters such as  . : + = @ _ / are allowed.
- Consecutive special characters or spaces are not allowed.
- Name should be unique from other units.

#### Dedicated Resources

Users can select multiple resources as **Dedicated Resources**. The cost of these resources is assigned solely to the specific unit item. This enables precise cost tracking and ensures that the full cost of a dedicated resource is attributed to the unit item that uses it exclusively.

#### Shared Resources

Any resources not explicitly mentioned in the **Dedicated Resources** section are considered **Shared Resources**. Shared resources are distributed across multiple unit items. In this version, shared resources are allocated by default, assuming they are not dedicated to any single unit item.

By defining Unit Types and Unit Items, organizations can more accurately allocate and track costs, ensuring a clear understanding of where resources are being utilized and how expenses are being incurred.

## Process of Calculating Unit Cost

### Version 1: Manual Input and Processing

Currently, this concept is in version 1 and involves a manual process. The Unit Types and Unit Items, along with their corresponding percentages, are manually input by the user. Additionally, users have the option to specify **Dedicated Resources** and **Shared Resources** for each unit item. 

- **Dedicated Resources**: Users can manually select resources (at the account and service level) that are exclusive to a specific unit item. The cost of these resources is dedicated solely to that unit item.
  
- **Shared Resources**: Any resources not explicitly designated as dedicated are considered **Shared Resources**. These resources are automatically distributed across multiple unit items. 

An automated identification system for these elements, including the classification of dedicated and shared resources, is under ongoing investigation.


### Data Storage

Once the user manually inputs the Unit Types and Unit Items, this data is stored in a GCP Spanner table called `cover_unitcost`. 

#### Sample Data

| Column Name    | Sample Value |
|----------------|--------------|
| id             | 35022b5d-91bb-4cd4-8fdd-5577a017f9cc |
| orgId          | MSP-5aa311904d5d6 |
| date           | 2024-08-02 |
| unitType       | Product |
| description    | Cost per product |
| unitItems      | [{"itemName":"octo","distribution":0.2,"dedicatedResourcesCombinati...}] |
| hasMetrics     | false |
| createdBy      | Christian |
| createTime     | 2024-08-01T23:17:56.92991733Z |
| lastUpdatedAt  | 2024-08-01T23:17:56.9299174Z |

##### Full `unitItems` Value

```json
[
  {"itemName":"octo","distribution":0.2,"dedicatedResourcesCombination":[{"andFilters":{"account":"re:(?:^131920598436$)","productCode":"re:(?:^AmazonEC2$)|(?:^AmazonS3$)"}}]},
  {"itemName":"ripple","distribution":0.4,"dedicatedResourcesCombination":[{"andFilters":{"account":"re:(?:^131920598436$)","productCode":"re:(?:^AmazonDynamoDB$)"}}]},
  {"itemName":"wave","distribution":0.3,"dedicatedResourcesCombination":[{"andFilters":{"account":"388157217682","productCode":"AmazonRDS"}}]}
]

### Batch Processing

A daily batch process reads the entries from `cover_unitcost`, processes each one, and stores the results in another GCP Spanner table called `cover_tag_management`.

#### Sample Data

| Column Name    | Sample Value |
|----------------|--------------|
| id             | 00bb3f07-eeb3-4cbd-9a92-963a791c7bca |
| orgId          | MSP-5aa311904d5d6 |
| date           | 2024-06-03 |
| filter         | [{"and":{"account":"000001000001"}}, ...] |
| tags           | {"alphaus:Product":["octo","ripple","wave"]} |
| unitItems      | [{"itemName":"octo","distribution":0.2,"dedicatedResourcesCombinati...}] |
| createTime     | 2024-08-01T23:19:17.551506Z |
| updateTime     | 2024-08-01T23:19:17.551506Z |
| category       | Product |

### Tag Generation

The batch process generates tags based on the unit items in a JSON format. The `unitType` is used as a key, but first, `alphaus:` is concatenated to the unit type. This results in a format like `alphaus:<unitType>`. The unit items are included as the values associated with the key.

For example, for the unit type "Product" with items "octo", "ripple", and "wave", the tag would look like this:

```json
{"alphaus:Product":["octo","ripple","wave"]}

```

### Applying Filters

Filters are applied to specify where the tags will be reflected. In the current version, the filter covers all accounts in AWS and GCP for the organization. 

### Special Computation for Customers

For the "Customer" unit type, our organization has a unique process to calculate the cost percentage. This process is exclusive to our organization and is based on the size of the Cost and Usage Reports (CUR) for each customer.

#### Steps for Customer Cost Calculation

1. **Collect CUR Sizes**:
   - Collect the size of the CUR for each customer from tables in BigQuery.

2. **Calculate Percentages**:
   - Calculate each customer's percentage based on the size of their CUR relative to the total size of all customers' CURs.

3. **Generate Tags**:
   - Generate tags in the format `{"alphaus:customer":["customer1","customer2","customer3"]}` based on these percentages.

4. **Store in `cover_tag_management`**:
   - Store the generated tags in the `cover_tag_management` table using the same structure and process as other unit types.

### Summary

Every day, the batch process reads all items in `cover_unitcost`, processes each, and stores the results in `cover_tag_management`. The tags are used to attribute costs accurately to the defined unit items, facilitating detailed cost tracking and management. For customers, the process involves a unique calculation based on CUR sizes, ensuring precise cost distribution among different customers.
