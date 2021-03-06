# Workflows

## `npm run` scripts execute common development workflows against an `.arc` file.

- [`create`](#arc-create) creates code and corresponding cloud infrastructure
- [`deploy`](#arc-deploy) deploys cloud functions
- [`sandbox`](#arc-sandbox) runs cloud function code locally, offline and completely in memory
- [`modules`](#arc-modules) manage common npm tasks across all cloud functions

### Setup

```bash
npm i @architect/workflows --save-dev
```

Add the following to `scripts` in `package.json`:

```javascript
{
  "create": "AWS_PROFILE=xxx AWS_REGION=us-west-1 arc-create",
  "deploy": "AWS_PROFILE=xxx AWS_REGION=us-west-1 arc-deploy",
  "start": "NODE_ENV=testing arc-sandbox",
  "i": "arc-modules-install",
  "link": "arc-modules-link",
  "uninstall": "arc-modules-uninstall",
  "update": "arc-modules-update",
}
```

Don't forget: you have to set up `AWS_PROFILE` and `AWS_REGION` env variables ([see more here](/quickstart/setup)).

---

## <a href=#arc-create id=arc-create>`create`</a>

Create code and infra from `.arc` in the current directory:

```bash
npm run create
```

---

## <a href=#arc-deploy id=arc-deploy>`deploy`</a>

Deploy all code in `./src` to `staging`:

```bash
npm run deploy
```

Deploy all code in `./src` to `production`:

```bash
ARC_DEPLOY=production npm run deploy
```

Deploy a single function (example: `get /`) to `staging`:

```bash
npm run deploy src/html/get-index
```

Deploy a single function (example: `get /`) to `production`:

```bash
ARC_DEPLOY=production npm run deploy src/html/get-index
```

---

## <a href=#arc-sandbox id=arc-sandbox>`sandbox`</a>

Start a local web server and in-memory DyanmoDB instance:

```bash
npm start
```

Tip: Works super well with [Nodemon](https://nodemon.io)!

---

## <a href=#arc-modules id=arc-modules>`modules`</a>

Install a module to all `.arc`-defined functions in `./src`:

```bash
npm run install lodash
```

Link a local module to all `.arc`-defined functions in `./src`:

```bash
npm run link src/md
```

Uninstall a module from all `.arc`-defined functions in `./src`:

```bash
npm run uninstall lodash
```

Update a module in all `.arc`-defined functions in `./src`:

```bash
npm run update lodash
```

---

## Next: [Authoring `.arc`-defined cloud functions](/reference/functions)
