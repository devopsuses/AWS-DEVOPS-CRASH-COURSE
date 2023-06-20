# Metric filter

Metrics can be synthesized by aggregating logs.

1. From the `logjam` log group select `Actions / Create metrics filter`.
2. From the `Filter patten` pull down examine the sample values.
3. Select `ERROR` and click `Test pattern`.
4. Remember that these logs are JSON formatted.
5. Change the `Filter pattern` to use the structured fields:
```json
{ $.level = "ERROR"}
```
6. Click `Next`.
7. Fill out the `Assign metric` form:
```text
Filter name      = logjam-errors
Metric namespace = logjam
Metric name      = Error count
Metric value     = 1
Unit             = Count
```
8. From the `Metric filters` console click `logjam/Error count`.
9. Select `Graphed metric` and change the `Statistic` to `Sum`.
