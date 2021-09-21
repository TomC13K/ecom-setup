# Vue Storefront project

## Pre-requisities
- nodeJS 14  12 & 16  dont work

## Build Setup

``` bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).


## config

- in file `middleware.config.js`

``` js
const projectKey = process.env.VUE_APP_CTP_PROJECT_KEY
const clientSecret = process.env.VUE_APP_CTP_CLIENT_SECRET
const clientId = process.env.VUE_APP_CTP_CLIENT_ID
const uri = process.env.VUE_APP_CTP_API_URL
const scopes = process.env.VUE_APP_CTP_SCOPES




module.exports = {
  integrations: {
    ct: {
      location: '@vue-storefront/commercetools-api/server',
      configuration: {
        api: {
          uri: `${uri}/${projectKey}/graphql`,
          authHost: 'https://auth.sphere.io',
          projectKey,
          clientId,
          clientSecret,
          scopes: [
            scopes
          ]
        },
        currency: 'USD',
        country: 'US'
      }
    }
  }
};
```
