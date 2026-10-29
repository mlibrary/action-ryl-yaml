# action-ryl-yaml
Lint yaml files with [owenlamont/ryl](https://github.com/owenlamont/ryl)

## Inputs

- `enforce_extension`: Require all yaml files to use `.yaml` file extension? Defaults to `true`.

## Usage

Be sure there is a config file at the root of your repository that `ryl` recognises (e.g. `.ryl.toml`).
`yamllint` config files are also accepted, but will produce a warning. See `ryl`
[configuration docs](https://ryl-docs.pages.dev/config-presets/) for a list of accepted config files.

```
steps:
- name: Lint yaml files
  uses: mlibrary/action-ryl-yaml@<commit-sha>
```
