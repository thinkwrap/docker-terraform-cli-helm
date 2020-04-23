# Terraform && Helm Docker Container

This is a *containerized* Terraform & Helm CLI based on `thinkwrap/docker-terraform-cli` that also sets up for use with Terraform Cloud (via `.terraformrc`).

> This container includes the AWS CLI.

[![DockerHub Badge](http://dockeri.co/image/thinkwrap/docker-terraform-cli)](https://hub.docker.com/r/thinkwrap/docker-terraform-cli/)

## Example build

```
docker build -t thinkwrap/docker-terraform-cli-helm .
```

## Example usage

> The example below (keys) assumes an existing AWS account.


**Ensure the following are set**

```
export AWS_ACCESS_KEY_ID="<aws_access_key_id>"
export AWS_SECRET_ACCESS_KEY="<aws_secret_access_key>"
export AWS_DEFAULT_REGION="<aws_default_region>"
```

**Run the container detatched**
```
docker run --name docker-terraform-cli \
    --rm \
    --detach \
    --tty \
    --env "AWS_ACCESS_KEY_ID=${AWS_ACCESS_KEY_ID}" \
    --env "AWS_SECRET_ACCESS_KEY=${AWS_SECRET_ACCESS_KEY}" \
    --env "AWS_DEFAULT_REGION=${AWS_DEFAULT_REGION}" \
    thinkwrap/docker-terraform-cli
```

**Run a command**

> While this is obviously a very simple example, more complex usage, particularly in a CI/CD pipeline, is possible.

```
docker exec -it docker-terraform-cli-helm terraform --version 
docker exec -it docker-terraform-cli-helm helm version 
```

## References

[Terraform Documentation](https://www.terraform.io/docs/cli-index.html)
[Terraform CLI Credentials Configuration Documentation](https://www.terraform.io/docs/commands/cli-config.html#credentials)
[Helm Documentation](https://helm.sh/docs/)

# License

Licensed under the Apache License, Version 2.0 (the "License").

This repository and its contents are licensed under the terms detailed in the [LICENSE file](./LICENSE).