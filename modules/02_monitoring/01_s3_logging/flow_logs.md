# Flow logs

Flow logs create a record of all traffic in and out of a VPC or subnet.

1. Select the VPC created for the Yelb ECS cluster.
2. Select `Flow logs / Create flow log`.
3. Create `Athena integration`.
4. Create Athena table manually.
```SQL
CREATE EXTERNAL TABLE IF NOT EXISTS vpcflowlogs (
  version int,
  account_id string,
  interface_id string,
  srcaddr string,
  dstaddr string,
  srcport int,
  dstport int,
  protocol bigint,
  packets bigint,
  bytes bigint,
  start bigint,
  `end` bigint,
  action string,
  log_status string,
  vpc_id string,
  subnet_id string,
  instance_id string,
  tcp_flags int,
  type string,
  pkt_srcaddr string,
  pkt_dstaddr string,
  az_id string,
  sublocation_type string,
  sublocation_id string,
  pkt_src_aws_service string,
  pkt_dst_aws_service string,
  flow_direction string,
  traffic_path int
)
PARTITIONED BY (region string, day string)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ' '
LOCATION 's3://DOC-EXAMPLE-BUCKET/prefix/AWSLogs/{account_id}/vpcflowlogs/'
TBLPROPERTIES
(
    "skip.header.line.count"="1",
    "projection.enabled" = "true",
    "projection.region.type" = "enum",
    "projection.region.values" = "us-east-1,us-west-2,ap-south-1,eu-west-1",
    "projection.day.type" = "date",
    "projection.day.range" = "2021/01/01,NOW",
    "projection.day.format" = "yyyy/MM/dd",
    "storage.location.template" = "s3://DOC-EXAMPLE-BUCKET/prefix/AWSLogs/${account_id}/vpcflowlogs/${region}/${day}"
)
```

https://docs.amazonaws.cn/en_us/vpc/latest/userguide/flow-logs-athena.html