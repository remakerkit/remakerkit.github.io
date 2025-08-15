# Template definition

To write templates you need to create a file called `remaker.template.yaml`. This file must be in the root of your template project, both locally and remotely.

```yaml
name: example-template
parameters: []
register: {}
```

- `parameters` 
- `register` 

## Parameters

These is the list of variable parameters that you will use to fill in data in your template.

The parameters can be:

- string
- select
- boolean

### String

The string parameter is a simple text parameter.

```yaml
parameters:
  - name: <param variable name>
    type: string
    title: <title to fill param>
```

### Select

The select parameter is a parameter that allows you to choose between multiple options.

```yaml
parameters:
  - name: visibility
    type: select
    options:
      - public
      - private
```

### Boolean

The boolean parameter is a parameter that allows you to choose between two options: true or false.

```yaml
parameters:
  - name: isPublicEndpoint
    type: boolean
```


## Register

This is the configuration that will be used to register the project in the provider.

```yaml
register:
  provider: "{% .gitProvider %}"
  repoGroup: "{% .group %}"
  repoName: "{% .name %}"
  visibility: private
  description: "{% .description %}"
  branch: main
```

| Key | Required | Default | Description |
|-----|----------|---------|-------------|
| `provider` | `true` | "" |  Define the provider use to register the project |
| `repoGroup` | `true` | "" | Define the group repo to reigster the project. If you want to log directly to your gitlab or github user, use / as the value |
| `repoName` | `true` | "" | Define the `repoName` to register the project |
| `visibility` | `false` | `private` | Define the project visibility in provider |
| `description` | `false` | "" | Project description at the provider |
| `branch` | `false` | "main" | Default git branch |

> Note that here you can use the variables defined in the parameters to fill in the values. Use the delimiters `{%` `%}` to use the variables. Remember to always use `"` `"`