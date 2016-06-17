# nginx-s3-proxy

## Motivation

This image was created to securely proxy requests to S3. It uses
[confd](http://github.com/kelseyhightower/confd) to update the nginx
configuration and then starts nginx. You'll need to run your container with the
following environment variables:

```
SERVER_NAME
S3_BUCKET
REGION
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
```


## Usage

You can run it using a docker-compose like this:

```yaml
version: '2'
services:
  s3proxy:
    cpu: 512
    memory: 128m
    build: ./
    environment:
      SERVER_NAME: "s3proxy.example.com"
      S3_BUCKET: "your-conf-data"
      REGION: "us-west-2"
      AWS_ACCESS_KEY_ID: "<some-access-key>"
      AWS_SECRET_ACCESS_KEY: "<some-secret-key>"
    ports:
      - "8080:80"
```

## License

MIT
