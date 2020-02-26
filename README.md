# FBL Examples

Current repository is created to show how fbl can help with different real life scenarios and how flexible it is. If you don't see something here it doesn't mean FBL can not handle that. Most likely we just have no time left to cover that.

## Kubernetes

### Release Based Deployments

One of the ways how deployments can be managed - via individual releases, where every release has it's own set of scripts to run (backup, deploy, notify, etc) and rollback strategy to help in cases when something goes wrong. 

[k8s/release_based_deployment](./k8s/release_based_deployment)

### Interactive CLI 

Interactive console build on top of the `kubectl` command to showcase how reach command line interfaces can be used with common tools.

[k8s/interactive_console](./k8s/interactive_console)

