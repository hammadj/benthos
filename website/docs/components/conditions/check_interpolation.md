---
title: check_interpolation
type: condition
---

<!--
     THIS FILE IS AUTOGENERATED!

     To make changes please edit the contents of:
     lib/condition/check_interpolation.go
-->


Resolves a string containing
[function interpolations](/docs/configuration/interpolation#functions) and then tests
the result against a child condition.

```yaml
check_interpolation:
  value: ""
  condition: {}
```

For example, you could use this to test against the size of a message batch:

``` yaml
check_interpolation:
  value: ${!batch_size}
  condition:
    number:
      operator: greater_than
      arg: 1
```

## Fields

### `value`

`string` The value to check against the child condition.

This field supports [interpolation functions](/docs/configuration/interpolation#functions) that are resolved batch wide.

```yaml
# Examples

value: ${!json_field:doc.title}

value: ${!metadata:kafka_topic}

value: ${!json_field:doc.id}-${!metadata:kafka_key}
```

### `condition`

`object` A child condition to test the field contents against.

