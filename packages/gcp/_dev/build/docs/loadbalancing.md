# Loadbalancing

## Metrics

The `loadbalancing` dataset fetches metrics from [Loadbalancing](https://cloud.google.com/load-balancing) in Google Cloud Platform. It contains all metrics exported from the [GCP Loadbalancing Monitoring API](https://cloud.google.com/monitoring/api/metrics_gcp#gcp-loadbalancing).

You can specify a single region to fetch metrics like `us-central1`. Be aware that GCP Storage does not use zones so `us-central1-a` will return nothing. If no region is specified, it will return metrics from all buckets.

## Sample Event
    
{{event "loadbalancing"}}

## Exported fields

{{fields "loadbalancing"}}