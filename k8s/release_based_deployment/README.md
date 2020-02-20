# K8s: Release Based Deployment Example

The main purpose of this example is to show how FBL can control `kubectl` and `helm` tools to manage Kubernetes deployments in a release based manner.

It shows how each individual release can contain more that just helm install command, particularly it shows how to (inside `releases/1.0.0`):
- Create new namespace
- Install cert-manager custom resource definitions and wait for them to become available
- Install cert-manager with helm
- Register Let's Encrypt ClusterIssuer abstraction

It also has a rollback scripts that can revert the changes.

In our existing production deployments we generally do a way more steps in every release, like:
- Run DB backups
- Run DB migrations if any
- Update IDP configuration (e.g. Keycloak can be managed with our other plugin [@fbl-plguins/keycloak-admin-client](https://www.npmjs.com/package/@fbl-plugins/keycloak-admin-client))
- Manage Blue/Green deployments
- Run synthetic transaction testing across newly deployed stack to make sure everything operates as expected
- And much more

This example is using following plugins:
- [@fbl-plugins/crypto](https://www.npmjs.com/package/@fbl-plugins/crypto) to manage vault folder encryption/decryption in every release
- [@fbl-plugins/k8s-helm](https://www.npmjs.com/package/@fbl-plugins/k8s-helm) to operate `helm` release installation/removal
- [@fbl-plugins/k8s-kubectl](https://www.npmjs.com/package/@fbl-plugins/k8s-kubectl) to create/apply and remove different abstractions (e.g. create namespace, ClusterIssuer)

## Preparation

- Install Node.js (LTS version is preferred) if not yet installed
- Run `npm i -g fbl` to install the `fbl` CLI
- Run `npm i -g @fbl-plugins/crypto @fbl-plugins/k8s-helm @fbl-plugins/k8s-kubectl` to install all the plugins used in this example.

## Usage

Simply invoke one of the following commands and answer the prompts.

```bash
# run the deployment
fbl deploy.yml

# rollback deployment
fbl rollback.yml

# create new release based on the "template" folder
fbl scaffold.yml

# encrypt vault folder inside given release
# Note: vault is not included in release/1.0.0, but you can try to create a new release with previous command and play around with how secrets work
fbl encrypt.yml

# decrypt vault folder inside given release
fbl decrypt.yml
```

## Environment Variables

You can skip prompts by providing following envs:

```bash
# Password to encrypt/decrypt vault, can be unique for each individual release if you want
export PASSWORD=XXXXXX

# Release name
export RELEASE=1.0.0

# Environment to target
export ENVIRONMENT=prod
```
