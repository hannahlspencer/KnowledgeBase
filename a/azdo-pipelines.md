# Azdo Pipelines

Azdo pipelines are generally written in YAML.



You can use variable groups with them under Pipelines -> Library. This is how you specify what group to use in the yaml:

```yaml
variables:
- group: "group_one"
- name: location
  value: uksouth
```

You can edit the pipeline within Azdo, and use their bespoke tasks to make things easier.

## ![](<../.gitbook/assets/image (1).png>)

For example, selecting Azure CLI from the tasks means you don't need to add an az login as you just use the service connection (under azureSubscription in the yaml).
