# Querying AWS costs using bluectl

[`bluectl`](https://alphauslabs.github.io/docs/blueapi/bluectl/) is a flexible tool that you can use to query your cost data in Ripple/Wave(Pro). It uses the same [API](https://alphauslabs.github.io/blueapidocs/) that powers our Ripple/Wave(Pro) UI consoles. Since it also supports most, if not all of the possible API parameters, in some cases, you can even query data combinations that are not yet available in our UI.

!!! info "--raw-input"
    [Blue API](https://alphauslabs.github.io/blueapidocs/) and [`bluectl`](https://alphauslabs.github.io/docs/blueapi/bluectl/) are still in beta. For `bluectl` to be able to support most Blue API parameter combinations, it provides a `--raw-input` flag which accepts the same JSON input required in Blue API for most of its commands. Refer to the examples using the `--raw-input` flag below.
    
    As Blue API becomes more stable, we will provide more easy-to-use parameters to `bluectl` so you don't have to use the `--raw-input` flag. Stay tuned.

## Query a billing group's daily costs for the current month
```sh
# Replace 'abcdef' with your billing internal id.
$ bluectl awscost get --raw-input '{"groupId":"abcdef"}'
```

## Query an account's daily costs for the current month
```sh
# Replace '012345678901' with your account id.
$ bluectl awscost get --raw-input '{"accountId":"012345678901"}'
```

## Using date ranges in your query
```sh
# Query costs for the month of December, 2021.
$ bluectl awscost get --raw-input \
  '{"accountId":"012345678901","startTime":"20211201","endTime":"20211231"}'
```

## Exporting your queries to CSV
You can use the `--out {location}` flag to export your queries to a CSV file. For example:
```sh
$ bluectl awscost get --raw-input '{"groupId":"abcdef"}' --out /tmp/out.csv
```

Download current month's adjustment costs and save as CSV file:
```sh
# Here, 'all' could mean MSP-level or billing group level.
$ bluectl awscost get-adjustments --type all --out /tmp/out.csv
```

You can also provide the `--start yyyymmdd` and `--end yyyymmdd` flags for date ranges.

Download current month's usage costs for a specific account and save as CSV file:
```sh
$ bluectl awscost get --id 1234567890 --type account --out /tmp/out.csv
```

Download current month's adjustment costs for a specific billing group and save as CSV file:
```sh
# Here, 'bill001' is your billing group id.
$ bluectl awscost get-adjustments \
  --id bill001 \
  --type billinggroup \
  --out /tmp/out.csv
```

You can also provide the `--include-tags` and/or `--include-costcategories` flag(s) to include the tags and/or cost category information in the streaming data. At the moment, only the usage-based data supports tags and cost categories.

Although these APIs are designed to be streamed due to potentially large amounts of data, you can still use the JSON/REST API like so:

```sh
# Output is a newline-delimited rows of JSON data.
$ curl -X POST -H "Authorization: Bearer $(bluectl access-token)" \
  https://api.alphaus.cloud/m/blue/cost/v1/aws/costs:read \
  -d '{"accountId":"1234567890"}'
```
