# Hugo Module for everything Social

## Follow

One partial to print all your social "follows" links to according to your project's config.

## Icons

Icons are pulled from our default set but can be easily overwritten by adding svg files to:

`assets/tnd-socials/svgs/` following this name convention: `assets/tnd-socials/svgs/{service}.svg`

## Configure

The module reads Hugo's own Social reserved config. 

Most socials services profile url uses the following pattern:`https://www.{service}.com/{username}`
If a service does not (looking at you LinkedIn!), you can simply add the full url in the config.

```yaml
baseURL: myurl.com
social:
  twitter: theNewDynamic
  linkedin: https://www.linkedin.com/in/johndoe
  
```