# @nuxtjs/gtm

[![npm version][npm-version-src]][npm-version-href]
[![npm downloads][npm-downloads-src]][npm-downloads-href]
[![Circle CI][circle-ci-src]][circle-ci-href]
[![Codecov][codecov-src]][codecov-href]
[![License][license-src]][license-href]

> Google Tag Manager Module for Nuxt.js

[📖 **Release Notes**](./CHANGELOG.md)

ℹ️ If coming from v1 (`@nuxtjs/google-tag-manager`) please read v2 [release notes](https://github.com/nuxt-community/gtm-module/releases/tag/v2.0.0).

## Setup

1. Add `@nuxtjs/gtm` dependency to your project

```bash
yarn add @nuxtjs/gtm # or npm install @nuxtjs/gtm
```

2. Add `@nuxtjs/gtm` to the `buildModules` section of `nuxt.config.js`

```js
{
  buildModules: [
    '@nuxtjs/gtm',
  ],
  gtm: {
    id: 'GTM-XXXXXXX'
  }
}
```

## Options

```js
{
  // Set to false to disable module in development mode
  dev: true,

  id: null, /* REQUIRED */
  layer: 'dataLayer',
  variables: {},

  pageTracking: false,
  pageViewEventName: 'nuxtRoute',

  autoInit: true,
  respectDoNotTrack: true,

  scriptId: 'gtm-script',
  scriptDefer: false,
  scriptURL: 'https://www.googletagmanager.com/gtm.js',

  noscript: false,
  noscriptId: 'gtm-noscript',
  noscriptURL: 'https://www.googletagmanager.com/ns.html'
}
```

### GTM Initialisation

If you want to block Google Tag Manager before user directly allows (GDPR realisation or other), you can set `autoInit` option to `false` and then manually enable using `$gtm.init()`.

**Note:** All events will be still buffered in data layer but won't send until `init()` method getting called.

### Router Integration

You can optionally set `pageTracking` option to `true` to track page views.

**Note:** This is disabled by default to prevent double events when using alongside with Google Analytics so take care before enabling this option.

The default event name for page views is `nuxtRoute`, you can change it by setting the `pageViewEventName` option.

## Usage

### Pushing events

You can push events into the configured layer:

```js
this.$gtm.push({ event: 'myEvent', ...someAttributes })
```

## Development

1. Clone this repository
2. Install dependencies using `yarn install` or `npm install`
3. Start development server using `npm run dev`

## License

[MIT License](./LICENSE)

Copyright (c) Nuxt.js Community

<!-- Badges -->
[npm-version-src]: https://img.shields.io/npm/v/@nuxtjs/gtm/latest.svg?style=flat-square
[npm-version-href]: https://npmjs.com/package/@nuxtjs/gtm

[npm-downloads-src]: https://img.shields.io/npm/dt/@nuxtjs/gtm.svg?style=flat-square
[npm-downloads-href]: https://npmjs.com/package/@nuxtjs/gtm

[circle-ci-src]: https://img.shields.io/circleci/project/github/nuxt-community/gtm-module.svg?style=flat-square
[circle-ci-href]: https://circleci.com/gh/nuxt-community/gtm-module

[codecov-src]: https://img.shields.io/codecov/c/github/nuxt-community/gtm-module.svg?style=flat-square
[codecov-href]: https://codecov.io/gh/nuxt-community/gtm-module

[license-src]: https://img.shields.io/npm/l/@nuxtjs/gtm.svg?style=flat-square
[license-href]: https://npmjs.com/package/@nuxtjs/gtm
