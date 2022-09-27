# postgraphile-plugin-apollo-federation

[![CI/CD](https://github.com/brooklyn-labs/postgraphile-plugin-apollo-federation/actions/workflows/npm-publish.yml/badge.svg)](https://github.com/brooklyn-labs/postgraphile-plugin-apollo-federation)
[![npm version](https://img.shields.io/npm/v/@brooklyn-labs/postgraphile-plugin-apollo-federation)](https://www.npmjs.com/package/@brookly-labs/postgraphile-plugin-apollo-federation)

Apollo federation support for PostGraphile (or any Graphile Engine schema).

## Installation

```shell
npm install postgraphile-plugin-apollo-federation
```

## CLI usage

```shell
postgraphile --append-plugins postgraphile-plugin-apollo-federation
```

## Library usage

```js
const express = require("express");
const { postgraphile } = require("postgraphile");
const { default: postgraphile-plugin-apollo-federation } = require("postgraphile-plugin-apollo-federation");

const app = express();

app.use(
  postgraphile(process.env.DATABASE_URL, "public", {
    appendPlugins: [postgraphile-plugin-apollo-federation],
  })
);

app.listen(process.env.PORT || 3000);
```

## How?

This plugin exposes the [Global Object Identification
Specification](https://facebook.github.io/relay/graphql/objectidentification.htm)
(i.e. `Node` interface) in a way that's compatible with Apollo Federation.

Requires PostGraphile v4.4.2-rc.0+

## Testing

Docker can be used to spin up a test instance for running Jest tests. The instance will be exposed at port `5432`. See `.env.example` for the exported Postgre connection.

```sh
docker compose up -d
./scripts/test
```

## Do you need this?

Only use this if you're planning to have your API consumed by Apollo
Federation; exposing these redundant interfaces to regular users may be
confusing.

## Status

Proof of concept. No tests, use at your own risk! Pull requests very welcome.
