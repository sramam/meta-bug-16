# Reproduction

First install all dependencies - assumes `node` and `meta` are installed globally

```
npm i
meta npm install
```

## The problem:

### 1. `meta npm run lint`

does this:
```
/private/tmp/trial/meta-bug-16:
npm ERR! missing script: lint

npm ERR! A complete log of this run can be found in:
npm ERR!     /Users/sramam/.npm/_logs/2019-08-30T16_03_25_546Z-debug.log
/private/tmp/trial/meta-bug-16: command 'npm run lint' exited with error: Error: Command failed: npm run lint

repos/node-starter:

> @tufan/node-starter@1.0.0 lint /private/tmp/trial/meta-bug-16/repos/node-starter
> tslint -c tslint.json --project ./tsconfig.json --format stylish

no-use-before-declare is deprecated. Since TypeScript 2.9. Please use the built-in compiler checks instead.
no-unused-variable is deprecated. Since TypeScript 2.9. Please use the built-in compiler checks instead.
repos/node-starter ✓
 sramam  tmp  trial  meta-bug-16  master
```

### 2. `meta npm run lint --exclude .`

does this:
```
/private/tmp/trial/meta-bug-16:
npm ERR! missing script: lint

npm ERR! A complete log of this run can be found in:
npm ERR!     /Users/sramam/.npm/_logs/2019-08-30T16_03_35_898Z-debug.log
/private/tmp/trial/meta-bug-16: command 'npm run lint' exited with error: Error: Command failed: npm run lint

repos/node-starter:

> @tufan/node-starter@1.0.0 lint /private/tmp/trial/meta-bug-16/repos/node-starter
> tslint -c tslint.json --project ./tsconfig.json --format stylish

no-use-before-declare is deprecated. Since TypeScript 2.9. Please use the built-in compiler checks instead.
no-unused-variable is deprecated. Since TypeScript 2.9. Please use the built-in compiler checks instead.
repos/node-starter ✓
```

```
$ pwd
/tmp/trial/meta-bug-16
```

### 3. `meta npm run lint --exclude /tmp/trial/meta-bug-16`
does this:
```
/private/tmp/trial/meta-bug-16:
npm ERR! missing script: lint

npm ERR! A complete log of this run can be found in:
npm ERR!     /Users/sramam/.npm/_logs/2019-08-30T16_03_45_928Z-debug.log
/private/tmp/trial/meta-bug-16: command 'npm run lint' exited with error: Error: Command failed: npm run lint

repos/node-starter:

> @tufan/node-starter@1.0.0 lint /private/tmp/trial/meta-bug-16/repos/node-starter
> tslint -c tslint.json --project ./tsconfig.json --format stylish

no-use-before-declare is deprecated. Since TypeScript 2.9. Please use the built-in compiler checks instead.
no-unused-variable is deprecated. Since TypeScript 2.9. Please use the built-in compiler checks instead.
repos/node-starter ✓
```