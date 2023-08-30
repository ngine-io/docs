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
