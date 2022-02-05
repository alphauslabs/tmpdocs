# Querying AWS costs using bluectl

Here are some examples on how to query your cost details using the [`bluectl`](https://alphauslabs.github.io/docs/blueapi/bluectl/) tool.

Download current month's usage costs and save as CSV file:
```sh
# Here, 'all' could mean MSP-level or billing group level.
$ bluectl awscost get --type all --out /tmp/out.csv
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
