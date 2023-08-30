# Cloudscale.ch

## Prometheus

Add the following scrape config to your Prometheus server:

!!! tip "Optional: Filter by Tag"

    By adding a `filter_tag` you could filter instances by this tag. Possible options are `?tag:<tag-name>` of `?tag:<tag-name>=<tag-value>`

```yaml

scrape_configs:
  - job_name: cloudscale.ch nodes
    http_sd_configs:
      - url: "https://api.ngine.cloud/cloud-sd/v1/cloudscale-ch"
        authorization:
          credentials: <cloudscale api token>
          type: Bearer
```

## Tests

To test the results, you can use the following `curl` command:

```
curl -X 'GET' \
  'https://api.ngine.cloud/cloud-sd/v1/cloudscale-ch' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer <cloudscale api token>'
```

## Labels

The labels returned are:

```
__meta_cloudscale_name: "example-app1"
__meta_cloudscale_image: "debian-12"
__meta_cloudscale_flavor: "flex-4-1"
__meta_cloudscale_vcpu_count: "1"
__meta_cloudscale_memory_gb: "4"
__meta_cloudscale_zone": "rma1"
__meta_cloudscale_status: "running"
__meta_cloudscale_uuid: "0ca6d476-23d1-4812-9581-d02fc21d0e.."
__meta_cloudscale_tag_<name>: "<value>"
__meta_cloudscale_public_ip_1: "5.102.149.xy"
__meta_cloudscale_public_ip_2: "2a06:c01:1000:1166::xy"
__meta_cloudscale_private_ip_1: "172.16.146.159"
```
