# Configuration

To configure Remaker, you need to create a settings file. This file will contain your template and provider configurations.

```yaml
# This is the list of your providers.
# You can add more providers here.
providers:
    gitlab:
        token: ${GITLAB_TOKEN} # using environment variable, but you can use a plain text token
    github:
        token: ${GITHUB_TOKEN}
# Here is the list of your templates
templates:
    # this is an example template local
    example:
        provider: local
        path: example-template
    # this is a remote template from gitlab
    remote-gitlab:
        provider: gitlab
        url: https://gitlab.com/lbernardo/my-template-golang
    # this is a remote template from github
    remote-github:
        provider: github
        url: https://github.com/lbernardo/my-template-typescript
```

## Providers

Providers are the sources where your templates are stored. Remaker supports `GitLab` and `GitHub` as providers.

## Templates

In templates, you'll configure the source of your template project. It can be local or remote (using Gitlab or Github). You'll define the name of your template, and then its configuration as the object.

### Local

You can set your template to be on your machine. This will allow the remake to retrieve the template's information locally.

```yaml
templates:
    myFirstTemplate:
        provider: local
        path: /path/to/my/template
```

### Remote

You can set your template to be on a remote repository. This will allow the remake to retrieve the template's information from the remote repository. To use the template remotely you need to have previously configured your provider

```yaml
templates:
    myFirstTemplate:
        provider: gitlab
        url: https://gitlab.com/lbernardo/my-template-golang
```