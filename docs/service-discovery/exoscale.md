# Exoscale

## Prometheus

Add the following scrape config to your Prometheus server:

!!! note "Adding Zone"

    Append one of the following zones (`?zone=`) to the query via :
    `ch-gva-2`, `ch-dk-2`, `de-fra-1`, `de-muc-1`, `at-vie-1`, `bg-sof-1`

```yaml

scrape_configs:
  - job_name: cloudscale.ch nodes
    http_sd_configs:
      - url: "https://api.ngine.cloud/cloud-sd/v1/exoscale?zone=ch-gva-2"
        authorization:
          credentials: <api_key>:<api_secret>
          type: Bearer
```

## Tests

To test the results, you can use the following `curl` command:

```
curl -X 'GET' \
  'https://api.ngine.cloud/cloud-sd/v1/exoscale?zone=ch-gva-2' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer <api_key>:<api_secret>'
```
