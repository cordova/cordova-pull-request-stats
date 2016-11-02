# cordova-pull-request-stats

Stats pulled in from Apache Cordova repos on Github, and compiled using the [cordova-coho](https://github.com/apache/cordova-coho) tool.

To grab new `platforms` json:

`coho list-pulls --repo=platforms --stats-only --json | tail -n +2 > platforms-YYYY-MM-DD.json`

To grab new `plugins` json:

`coho list-pulls --repo=plugins --stats-only --json | tail -n +2 > plugins-YYYY-MM-DD.json`

Put the json in the appropriate `YYYY` directory in this repo.

```
--json only works with `--stats-only` and outputs the stats in JSON format (false by default).
--sort-ascending only works with `--stats-only` and sorts the results by fresh pull requests (false by default).

--json output starts on the second line, filter it out by piping the output to `tail -n +2`
`old` pull requests are PRs that are older than `--max-age`.
`stale` pull requests are PRs that are `old` and last commented on by `--hide-user`
````

## Easy scripts

`npm install && npm list:all`

This will grab the plugins and platforms PRs and put them in the appropriate year folder automatically, and name them accordingly to the current date.

## Github API key

Set env variable `CORDOVA_GIT_ACCOUNT` to `<username>:<password>` or `<api-token>` to avoid hitting GitHub rate limits.

e.g.

`CORDOVA_GIT_ACCOUNT=a7shh41jkkh1661h1 coho list-pulls --repo=plugins --stats-only --json | tail -n +2 > plugins-DD-MM-YYY.json`
