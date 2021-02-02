# djp-httpd

A [ddb](https://inetum-orleans.github.io/docker-devbox-ddb) jsonnet package (**djp**).

## Description

Apache Http Server **djp** package.

## Snippet

- `ddb.yml`

```yaml
cookiecutter:
  templates:
    - template: gh:inetum-orleans/djp-httpd
      extra_context:
        httpd_version: "2.4"
```

- `docker-compose.yml.jsonnet`

```jsonnet
ddb.Compose(
  ddb.with(
    import '.docker/httpd/djp.libjsonnet',
    params={domain: ddb.domain, vhost: ['/.docker/httpd/vhost.conf']}
  )
)
```

## Parameters

| name  | type | description |
| ------------- | ------------- | ------------- |
| domain  | string  | Description of first parameter
| vhost  | string[]  | Path to VirtualHost configuration files

## Tips

### Enable additional modules

You can enable additional modules inside `Dockerfile.jinja`.

```Dockerfile
RUN sed -i '/LoadModule proxy_module/s/^#//g' /usr/local/apache2/conf/httpd.conf
RUN sed -i '/LoadModule proxy_http_module/s/^#//g' /usr/local/apache2/conf/httpd.conf
RUN sed -i '/LoadModule rewrite_module/s/^#//g' /usr/local/apache2/conf/httpd.conf
```

## Usage

Please check [jsonnet feature](https://inetum-orleans.github.io/docker-devbox-ddb/features/jsonnet/#ddb-jsonnet-packages-djp)
to understand how to include a **djp** package inside a [ddb](https://inetum-orleans.github.io/docker-devbox-ddb) project.

Looking for other [djp packages](https://github.com/inetum-orleans?q=djp-) ? Check github repositories starting with `djp-`.
