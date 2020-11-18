## Push To Docker Registry Workflow
Workflow builds docker image with name `"${System.env.DOCKER_REGISTRY}/starter-test:@project.version"` and pushes the image
into configured docker registry.

The GitHub secrets in table below needs to be configured:

| Name | Description |
| ---- | ----------- |
| DOCKER_USERNAME | Docker registry username. |
| DOCKER_PASSWORD | Docker registry password. |
| DOCKER_ORGANIZATION | Docker image organisation, for image `foo/bar:latest` it is `foo`. |
| DOCKER_REGISTRY_URL | Docker registry url. In case of using DockerHub this secret is not needed. |
### Examples of configuration
> Specifics on how to configure public cloud docker registries like DockerHub, Google Container Registry (GCR), AWS Container Registry (ECR),
> Oracle Cloud Infrastructure Registry (OCIR) and many more can be found in [docker/login-action](https://github.com/docker/login-action)
> documentation.

#### DockerHub

- `DOCKER_USERNAME` - DockerHub username.
- `DOCKER_PASSWORD` - DockerHub password or personal access token.
- `DOCKER_ORGANIZATION` - DockerHub organization or the username in case of private registry.
- `DOCKER_REGISTRY_URL` - Not needed to configure.

> See [docker/login-action for GCR](https://github.com/docker/login-action#dockerhub)

#### Google Container Registry (GCR)
- `DOCKER_USERNAME` - set exactly to `_json_key`.
- `DOCKER_PASSWORD` - content of the service account json key with permission to edit GCR (or use Storage Admin role).
- `DOCKER_ORGANIZATION` - project id.
- `DOCKER_REGISTRY_URL` - `gcr.io`

> See [docker/login-action for GCR](https://github.com/docker/login-action#google-container-registry-gcr)

#### AWS Elastic Container Registry (ECR)
Create IAM user with permission to push to ECR (or use AmazonEC2ContainerRegistryFullAccess role).

- DOCKER_USERNAME - secret key ID
- DOCKER_PASSWORD - secret access key
- DOCKER_ORGANIZATION - no need to set
- DOCKER_REGISTRY_URL - set to `<aws-account-number>.dkr.ecr.<region>.amazonaws.com`

> See [docker/login-action for ECR](https://github.com/docker/login-action#google-container-registry-gcr)

#### Oracle Infrastructure Cloud Registry (OCIR)

- DOCKER_USERNAME - username in format `<tenancy>/<username>`
- DOCKER_PASSWORD - account auth token
- DOCKER_ORGANIZATION - `<tenancy>/<registry>`
- DOCKER_REGISTRY_URL - set to `<aws-account-number>.dkr.ecr.<region>.amazonaws.com`


## Feature http-client documentation

- [Micronaut Micronaut HTTP Client documentation](https://docs.micronaut.io/latest/guide/index.html#httpClient)

## Feature github-workflow-docker-registry documentation

- [https://docs.github.com/en/free-pro-team@latest/actions](https://docs.github.com/en/free-pro-team@latest/actions)

