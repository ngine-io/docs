# Apache CloudStack

## Prometheus

Add the following scrape config to your Prometheus server:

```yaml

scrape_configs:
  - job_name: cloudstack nodes
    http_sd_configs:
      - url: "https://api.ngine.cloud/cloud-sd/v1/cloudstack?endpiont=https%3A%2F%2Fexample.com%2Fclient%2Fapi"
        authorization:
          credentials: <api_key>:<api_secret>
          type: Bearer
```

## Tests

To test the results, you can use the following `curl` command:

```
curl --get \
  --data-urlencode 'endpoint=https://cloudstack.example.com/client/api' \
  'https://api.ngine.cloud/cloud-sd/v1/cloudstack' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer <api_key>:<api_secret>'
```
