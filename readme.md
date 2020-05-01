# branch-name-lint [![Build Status](https://travis-ci.org/barzik/branch-name-lint.svg?branch=master)](https://travis-ci.org/barzik/branch-name-lint) [![Known Vulnerabilities](https://snyk.io/test/github/barzik/branch-name-lint/badge.svg)](https://snyk.io/test/github/barzik//branch-name-lint) ![npm](https://img.shields.io/npm/dt/branch-name-lint)

Allowing to lint the branch names! by CLI or by another means - like Husky or any other CI tool.

## Install

```
$ npm install branch-name-lint
```

## CLI

```
$ npm install --global branch-name-lint
```

```
$ branch-name-lint --help

  Usage
    branch-name-lint [configfileLocation JSON]

  Examples
    $ branch-name-lint
    $ branch-name-lint package.json
```

### CLI options.json

Any Valid JSON file with `branchNameLinter` attribute.

```
{
    "branchNameLinter": {
        "prefixes": [
            "feature",
            "hotfix",
            "release"
        ],
        "suggestions": {
            "features": "feature",
            "feat": "feature",
            "fix": "hotfix",
            "releases": "release"
        },
        "banned": [
            "wip"
        ],
        "skip": [
            "skip-ci"
        ],
        "disallowed": [
            "master",
            "develop",
            "staging"
        ],
        "seperator": "/",
        "msgBranchBanned": "Branches with the name \"%s\" are not allowed.",
        "msgBranchDisallowed": "Pushing to \"%s\" is not allowed, use git-flow.",
        "msgPrefixNotAllowed": "Branch prefix \"%s\" is not allowed.",
        "msgPrefixSuggestion": "Instead of \"%s\" try \"%s\".",
        "msgSeperatorRequired": "Branch \"%s\" must contain a seperator \"%s\"."
    }
}
```

## Husky usage

After installation, just add in any husky hook as node modules call.

```
"husky": {
    "hooks": {
        "pre-push": "node ./node_modules/branch-name-lint/cli.js [sample-configuration.json]"
    }
},
```

## Usage in Node.js

```js
const branchNameLint = require('branch-name-lint');

branchNameLint();
//=> 1 OR 0.
```

## API

### branchNameLint([options])

#### options

Type: `object`
Default: 
```
{
  prefixes: ['feature', 'hotfix', 'release'],
  suggestions: {features: 'feature', feat: 'feature', fix: 'hotfix', releases: 'release'},
  banned: ['wip'],
  skip: [],
  disallowed: ['master', 'develop', 'staging'],
  seperator: '/',
  msgBranchBanned: 'Branches with the name "%s" are not allowed.',
  msgBranchDisallowed: 'Pushing to "%s" is not allowed, use git-flow.',
  msgPrefixNotAllowed: 'Branch prefix "%s" is not allowed.',
  msgPrefixSuggestion: 'Instead of "%s" try "%s".',
  msgSeperatorRequired: 'Branch "%s" must contain a seperator "%s".'
}
```

## License

MIT © [Ran Bar-Zik](https://internet-israel.com)
