# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Sandbox](#sandbox)
  - [npm](#npm)
  - [npm private registry](#npm-private-registry)

Not bad tutorial website at [Link](http://javascript.ru)

Checking how your script works at http://jsfiddle.net/XssCG/244/

## Sandbox

[Link](https://www.w3schools.com/jquery/tryit.asp?filename=tryjquery_eff_slideup_slidedown)

## npm

Install developer version of chromium:

```bash
npm install --save-dev chromium
```

Install production version of chromium:

```bash
npm install --save chromium
```

Uninstall chromium:

```bash
npm uninstall --save chromium
```

Chromium will be installed in

~/node_modules/chromium/lib/chromium/chrome-linux

tips [Link](https://habr.com/ru/articles/133363/)

## npm private registry

Verdaccio, s. https://verdaccio.org/ and https://blog.bitsrc.io/how-to-set-up-a-private-npm-registry-locally-1065e6790796

Unset registry:

```bash
npm config delete registry
```

```bash
npm configs
npm config list
```
