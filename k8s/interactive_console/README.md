# K8s: Simple CLI Interactive Tool

This example shows how reach interaction CLI interface can be build on top of other tools, in this particular example on top of `kubectl` and related fbl [plugin](https://www.npmjs.com/package/@fbl-plugins/k8s-kubectl).

This example also shows how [virtual](https://fbl.fireblink.com/plugins/flow#action-handler-virtual) (check [.utils](./utils) folder) action handlers can help to execute repeatable actions in the flow.

This example is using [@fbl-plugins/k8s-kubectl](https://www.npmjs.com/package/@fbl-plugins/k8s-kubectl) plugin to interact with `kubectl` tool.

## Demo

![Demo](./demo.gif)

## Preparation

- Install Node.js (LTS version is preferred) if not yet installed
- Run `npm i -g fbl` to install the `fbl` CLI
- Run `npm i -g @fbl-plugins/k8s-kubectl` to install required plugin.

## Usage

```bash
cd <fbl-examples/k8s/interactive_console>
fbl .

# or simply:
fbl <fbl-examples/k8s/interactive_console>
```
