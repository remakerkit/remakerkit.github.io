# Write template

Writing templates is very simple, you will assemble the structure of your standard project and then place the variables where you want, using gotemplate.
In remaker, we use gotemplate to rewrite files, so you can simply use all the native gotemplate functions. The only difference is that instead of using `{{` `}}` as delimiters, we use `{%` `%}`
Remaker will read all the project files and identify where there are variables to be replaced and thus replace them.

## Replacing values in my project

To replace variables just use `{% .VARIABLE %}`

In the example:
```yaml
# remaker.template.yaml
parameters:
  - name: age
    type: string
    title: Set your age
```

`main.go:`
```go
package main

import "fmt"

func main() {
    fmt.Println("Your age is {% .age %}")
}
```

## Conditions

It's very simple to work with conditions in the project template

```yaml
# remaker.template.yaml
parameters:
    - name: country
      type: select
      options:
        - title: Brazil
          value: brazil
        - title: France
          value: france
```

`App.tsx`:

```javascript
export const App = () => {
    {%- if eq .country "brazil" %}
    return (<>Olá! Bem vindo ao Brasil</>)
    {%- else %}
    return (<>Bonjour ! Bienvenue en France</>)
    {%- end %}
}
```

## True or False

There's a small caveat to using Remaker: 

```yaml
# remaker.template.yaml
parameters:
    - name: isWebServer
      type: boolean
```

`README.md`

```markup
{%- if .isWebServer }
This is a webserver
{% end %}
```
