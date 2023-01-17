# Adding cost modifiers to the AWS calculator using bluectl

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
For this example, will use a different rate of $0.005. Let's modify the description as well by enclosing it with an asterisk `*` so we will know later on what items where modified.

``` sh
# Let's use a file as our input:
$ cat /tmp/qualifier.json
{
  "awsOptions":{
    "groupId":"xWOGCzNy6GlK",
    "qualifiers":[
      {
        "and":{
          "productCode":"awskms",
          "region":"re:^ap.*-1$",
          "operation":"DescribeKeys"
        }
      }
    ],
    "modifier":{
      "formula":"usage * 0.005",
      "descriptionModifier":{
        "prefix":"*",
        "suffix":"*"
      }
    }
  }
}

# Create the modifier:
$ bluectl cost aws calculator mods create \
  --raw-input "$(cat /tmp/qualifier.json)"

# Query our current modifiers:
$ bluectl cost aws calculator mods list
```

## Modifying the cost

TBD

## Modifying both usage and cost

TBD
