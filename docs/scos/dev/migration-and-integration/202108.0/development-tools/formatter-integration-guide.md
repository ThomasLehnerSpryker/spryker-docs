---
title: Formatter integration guide
description: Learn how to integrate Formatter into your project
last_updated: Jun 16, 2021
template: howto-guide-template
originalLink: https://documentation.spryker.com/2021080/docs/formatter-integration-guide
originalArticleId: 4afd703c-3ce1-4924-901f-19c43b588cb0
redirect_from:
  - /2021080/docs/formatter-integration-guide
  - /2021080/docs/en/formatter-integration-guide
  - /docs/formatter-integration-guide
  - /docs/en/formatter-integration-guide
---

Follow the steps below to integrate [Formatter](/docs/scos/dev/sdk/{{page.version}}/development-tools/formatter.html) intor your project. 

## 1. Install the dependencies

To install the dependencies:

1. Install Prettier:
```bash
npm install prettier@2.0.x --save-dev
```
2. Install config for Prettier:
```bash
npm install @spryker/frontend-config.prettier --save-dev
```
3. Install the CLI parser:
```
npm install commander@4.0.x --save-dev
```
## 2. Update the scripts

To update the scripts:

1. Add formatting file extensions to the global settings `/frontend/settings.js`:
```const globalSettings = {
    ....
    
    formatter: [
        `**/*.(scss|css|less|js|ts|json|html)`,
    ],
};
```
2. Add the formatter script to `/frontend/libs/formatter.js`:
```
const { spawn } = require('child_process');
const { globalSettings } = require('../settings');
const commandLineParser = require('commander');
const configPath = 'node_modules/@spryker/frontend-config.prettier/.prettierrc.json';

commandLineParser
    .option('-f, --fix', 'execute stylelint in the fix mode.')
    .option('-p, --file-path <path>', 'execute stylelint only for this file.')
    .option('-i, --ignore-path <path>', 'path to prettier ignore file.')
    .parse(process.argv);

const mode = commandLineParser.fix ? '--write' : '--check';
const filePaths = commandLineParser.filePath ? [commandLineParser.filePath] : globalSettings.formatter;
const ignorePath = commandLineParser.ignorePath ? commandLineParser.ignorePath : './.prettierignore';

spawn(
    'npx',
    ['prettier', '--config', configPath, '--ignore-path', ignorePath, mode, ...filePaths],
    { stdio: 'inherit' }
);
```
 Check [here](https://github.com/spryker-shop/suite/blob/master/frontend/libs/formatter.js) for the example file.
 
3. Adjust the `/package.json` scripts: 
```
"scripts": {
    ....
    "formatter": "node ./frontend/libs/formatter",
    "formatter:fix": "node ./frontend/libs/formatter --fix"
}
```
4. Add the ignore file `/.prettierignore`:
```
# Ignore paths
/.github/
/.yarn/
/docker/
/frontend/
/vendor/
/public/Yves/assets/
/public/Zed/assets/
**/dist/**

/composer.json
/package-lock.json
```


