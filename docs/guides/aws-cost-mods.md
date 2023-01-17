# Adding cost modifiers to the AWS cost calculator using bluectl

!!! note
    This guide is only applicable to Ripple users.

Ripple allows the modification of both `usage` and `cost` values in its AWS cost calculations through [cost modifiers](https://alphauslabs.github.io/blueapidocs/#/Cost/Cost_CreateCalculatorCostModifier). Since the modifier formula supports simple arithmetic, logical, and comparison operators, it is actually quite flexible.

In this guide, we will try and create cost modifiers to our AWS calculations. At the time of writing, there is no UI available yet for these APIs so we will use `bluectl` for the time being.

Make sure to install [`bluectl`](https://alphauslabs.github.io/docs/blueapi/bluectl/) first.

You might want to query the daily cost details first to know what kind of qualifiers (or filters) to use to further filter down your modifiers' targets. You can check out this [guide](https://alphauslabs.github.io/docs/guides/aws-query-costs/) for more information. For this guide though, we will use `productCode:awskms` and `operation:DescribeKey` under Tokyo region for our qualifiers.

!!! warning
    Note that Ripple's trueunblended calculation uses a different logic than just referencing the lineitem's usage and cost. Be careful when applying modifiers to lineitems that are affected by trueunblended such as parts of AmazonEC2, AmazonRDS, AmazonElastiCache, AmazonES, and AmazonRedShift that are utilizing their respective RIs and/or SPs.
    
    If you must include these lineitems, you can only manipulate the `cost` part, not the `usage`. In this case, the `cost` variable refers to the final trueunblended cost.

## Modifying the usage

TBD

## Modifying the cost

TBD

## Modifying both usage and cost

TBD
