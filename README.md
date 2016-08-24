# cordova-pull-request-stats

Stats pulled in from Apache Cordova repos on Github, and compiled using the [cordova-coho](https://github.com/apache/cordova-coho) tool.

To grab new `platforms` json:

`coho list-pulls --repo=platforms --stats-only --json | tail -n +2 > platforms-DD-MM-YYY.json`

To grab new `plugins` json:

`coho list-pulls --repo=plugins --stats-only --json | tail -n +2 > plugins-DD-MM-YYY.json`

Put the json in the appropriate `YYYY` directory in this repo.

```
--json only works with `--stats-only` and outputs the stats in JSON format (false by default).
--sort-ascending only works with `--stats-only` and sorts the results by fresh pull requests (false by default).

--json output starts on the second line, filter it out by piping the output to `tail -n +2`
`old` pull requests are PRs that are older than `--max-age`.
`stale` pull requests are PRs that are `old` and last commented on by `--hide-user`
````