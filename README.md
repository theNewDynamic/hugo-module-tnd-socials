# Hugo Module TND Socials

## Requirements

Requirements:
- Go 1.14
- Hugo 0.61.0


## Installation

If not already, [init](https://gohugo.io/hugo-modules/use-modules/#initialize-a-new-module) your project as Hugo Module:

```
$: hugo mod init {repo_url}
```

Configure your project's module to import this module:

```yaml
# config.yaml
module:
  imports:
  - path: github.com/theNewDynamic/hugo-module-tnd-socials
```

## Usage

### GetSocials

The partial will return a slice of maps containing everything you need to build your social links:
  - String (.Name)
  - String (.Handle)
  - String (.URL)
  - SVG (String of safe HTML)

```
{{ range partialCached "tnd-socials/GetSocials" "GetSocials" }}
  <a href="{{ .URL }}" title="Follow {{ .Handle }} on {{ .Service }}">
    {{ .SVG }}
  <a>
{{ end }}
```
By default, the partial will return all the services set though the module's configuration in their original order. 
To limit or reorder services, the partial can take a `slice` as context:
```
{{ range partial "tnd-socials/GetSocials" (slice "facebook "twitter") }}
[...]
{{ end }}
```

### Icons

Icons are pulled from a default [set](https://github.com/theNewDynamic/hugo-module-tnd-icons/tree/master/svgs) but can easily be overwritten by adding svg files to your projects using the following naming convention:

`assets/tnd-socials/{service|icon}.svg`

## Configure

The module can read Hugo's default `Social` settings but we recommand using the module's own `.Params.tnd_socials` reserved key for more control:

### Services
The `services` key takes a slice of Maps with the following keys:
  - __service*__: The name of the service
  - __handle*__: The username or handle of the service's profile
  - __url__: If the profile URL does not follow the conventional `https://www.{service}.com/{handle}` it should be set here.
  - __icon__: Available icons are [here](https://github.com/theNewDynamic/hugo-module-tnd-icons/tree/master/svgs)  

```yaml
# config.yaml
params:
  tnd_socials:
    services:
    - name: github
      handle: theNewDynamic
    - name: twitter
      handle: John Doe
      url: https://www.twitter.com/john67898
      icon: twitter-alt
```