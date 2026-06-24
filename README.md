Insight UI (Zero)
=================

A Zero (ZER) blockchain explorer web application. `insight-ui-zero` is the
AngularJS frontend of the Zero Insight stack; it runs as a service of
`bitcore-node-zero` and reads its data from `insight-api-zero`.

> Source-of-record copy. This README is the corrected version staged under
> `error/insight-ui-zero/` in the Insight docs repo: Zero-accurate framing, the
> correct landing path, Node v8.17.0, and only links that still resolve.

Lineage: this is the Zero rename-fork of the Zcash Insight UI
([str4d/insight-ui-zcash](https://github.com/str4d/insight-ui-zcash)), itself
derived from BitPay's [bitcore-node](https://github.com/bitpay/bitcore-node)
ecosystem.

## Install

Insight UI is a Bitcore Node service. It is installed alongside the rest of the
stack and enabled in the `bitcore-node-zero` configuration; you do not normally
run it standalone. Once the node is running, the explorer is served at:

```
http://localhost:3001/insight/
```

(behind the production nginx it is served under `/insight/` on the public host.)

## Configuration

Insight UI is configured as a service entry in the Bitcore Node config
(`bitcore-node.json`), pointing at the running `insight-api-zero` service for its
data. The API base path and the node it talks to are set there; the UI itself has
no separate runtime config beyond what the service block provides.

## Development

To build and run from source:

```sh
git clone https://github.com/zerocurrencycoin/insight-ui-zero
cd insight-ui-zero
npm install
bower install
grunt
```

`grunt` compiles the Angular templates, styles, and the translation bundles, then
watches for changes. Use the standard Bitcore Node dev flow to serve the built UI
through a local node.

> Built under **Node.js v8.17.0** with the frozen 2021-era `bower`/`grunt`
> toolchain that the rest of the Zero Insight stack uses. Newer Node is not
> supported.

## Multilanguage

Translations use [angular-gettext](https://angular-gettext.rocketeer.be/).
Translatable strings are extracted into `po/template.pot`; per-language `.po`
files live under `po/`. Edit them with [Poedit](https://poedit.com/) or any
gettext editor, then rebuild (`grunt`) to regenerate the compiled
`js/translations.js` the app loads at runtime.

To add a language: copy `po/template.pot` to `po/<lang>.po`, translate, and
rebuild.

## License

Code released under the MIT license.

Copyright 2013-2015 BitPay, Inc.
