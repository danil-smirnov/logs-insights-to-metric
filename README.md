logs-insights-to-metric
=======================

This project is to publish data from CloudWatch Logs Insights to Custom Metrics.

Please read this blog post for more details:  
https://blog.smirnov.la/cloudwatch-logs-insights-to-metrics-a2d197aac379

Project page in AWS Serverless Application Repository:  
https://serverlessrepo.aws.amazon.com/applications/arn:aws:serverlessrepo:us-east-1:085576722239:applications~logs-insights-to-metric

Deployment parameters
---------------------

Must set:
- _AWSSDKLayerArn_ - AWS SDK layer supporting CloudWatch Logs Insights methods
- _LogGroupNames_ - Comma separated names of CloudWatch log groups to query
- _MetricName_ - A name of CloudWatch metric to put data into
- _MetricNamespace_ - A namespace of CloudWatch metric to put data into
- _QueryString_ - replace the default by something meaningful for you

Reasonable defaults:

- _Dimensions_ - Optional metric dimensions definition in JSON
- _GroupingDimensionName_ - A name of metric dimension used for grouping (default: 'Log group')
- _QueryDelay_ - Time to wait before data available to query in minutes (default: 3 min)
- _QueryGroupBy_ -  CloudWatch Logs Insights field name used for grouping (default: '@log')
- _QueryPeriod_ - Time window size in minutes (default: 5 min)
- _QueryRetry_ - Delay between getQueryResults retries in ms (default: 1000 ms)
- _QueryString_ - CloudWatch Logs Insights query to run  
(default: 'fields @log, @timestamp, @message | stats count() by @log' - log entries number per log group)
- _SkipEmpty_ - Wether to skip empty query results or post them as zeros (default: 'true')
- _Unit_ - Optional unit name (default: 'Count')
