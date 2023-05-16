# Angular CLI issue

## Steps to reproduce

**1.** Create a new angular project using the latest Angular CLI: `npx @angular/cli@latest new test-app --skip-install`

**2.** Change the Angular version to the previous major version (at the time of writing the previous major version 
is `15.2.9`)

**3.** Add `@types/web` as a development dependency by following the instructions in [here](https://www.npmjs.com/package/@types/web):

```shell
pnpm add @typescript/lib-dom@npm:@types/web --save-dev
npm install @typescript/lib-dom@npm:@types/web --save-dev
yarn add @typescript/lib-dom@npm:@types/web --dev
```

**4.** Execute `ng update @angular/cli @angular/core --allow-dirty`

**5.** You should be seeing the following error:

```shell
✔ Packages successfully installed.
Using package manager: npm
Collecting installed dependencies...
Found 16 dependencies.
Fetching dependency metadata from registry...
✖ Migration failed: 404 Not Found - GET https://registry.npmjs.org/@typescript%2flib-dom - Not found
  See ".../angular-errors.log" for further details.
```

The stacktrace of the error:

```shell
[error] HttpErrorGeneral: 404 Not Found - GET https://registry.npmjs.org/@typescript%2flib-dom - Not found
    at /tmp/angular-cli-packages-Fv6UlW/node_modules/npm-registry-fetch/lib/check-response.js:95:15
    at process.processTicksAndRejections (node:internal/process/task_queues:95:5)
    at async RegistryFetcher.packument (/tmp/angular-cli-packages-Fv6UlW/node_modules/pacote/lib/registry.js:87:19)
    at async Promise.all (index 3)
    at async /tmp/angular-cli-packages-Fv6UlW/node_modules/@angular/cli/src/commands/update/schematic/index.js:671:36
    at async callRuleAsync (/tmp/angular-cli-packages-Fv6UlW/node_modules/@angular-devkit/schematics/src/rules/call.js:77:18)
```
