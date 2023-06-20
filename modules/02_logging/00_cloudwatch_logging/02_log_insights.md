# Log insights.

1. From the `logjam` log stream select `Actions/Open in Logs Insights`.
2. Click `Run query` to see the unfiltered results.

## Filter, parse and aggregate.

1. From the `Logs Insights` editor examine the `Queries` menu on the right hand side.
2. Browse the examples for `Common queries`.
3. Note that the `message` field in the `logjam` logs is json structured data with several fields.
4. Get some simple stats.

```
fields @timestamp, @message
| filter @message like /level/
| parse @message "level: *" as @level
| stats count(*) by level
```
