# local-script-node-step
Example rundeck node step plugin that executes inline script on rundeck server

## Example job

```
- description: 'run a local script'
  executionEnabled: true
  loglevel: INFO
  name: run-local-script
  nodeFilterEditable: false
  nodefilters:
    dispatch:
      excludePrecedence: true
      keepgoing: false
      rankOrder: ascending
      successOnEmptyNodeFilter: false
      threadcount: 1
    filter: 'tags: app'
  nodesSelectedByDefault: true
  scheduleEnabled: true
  sequence:
    commands:
    - configuration:
        arguments: one two three
        script: |2-

          echo "args are: $@"

          echo "Local script executing on $(uname -n) on behalf of node: ${node.name}"
      nodeStep: true
      type: nixy-local-script-step
    keepgoing: false
    strategy: node-first
```
