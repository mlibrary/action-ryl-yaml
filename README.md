# action-ryl-yaml
Lint yaml files with [owenlamont/ryl](https://github.com/owenlamont/ryl)

## Inputs

- `enforce_extension`: Require all yaml files to use `.yaml` file extension. (Default: `true`)
- `strict`: Run `ryl check` with `--strict`, which elevates warnings to errors. (Default: `false`)
- `config`: Use one of the packaged preset configs. Must be one of the following:
  - [repo](configs/standard.toml): This is the **default** setting, uses your repo's
    config instead of a packaged config. Recommended.
  - [standard](configs/standard.toml): This repo's lint config. Recommended.
  - [basic](configs/basic.toml): A simple demo config. Use this as a starting point for your own config.
  - [default](configs/default.toml): ["default" config from `ryl` docs](https://ryl-docs.pages.dev/config-presets/#default-toml-equivalent).
    Matches "default" setting in `yamllint`. Included for reference/completeness. Not recommended.
  - [relaxed](configs/relaxed.toml): ["relaxed" config from `ryl` docs](https://ryl-docs.pages.dev/config-presets/#relaxed-toml-equivalent-fully-expanded).
    Matches "relaxed" setting in `yamllint`. Included for reference/completeness. Not recommended.

## Usage

This action uses your repo's `ryl` config by default. You must ensure there is a valid config in your
repository (e.g. `.ryl.toml`) or set the `config:` parameter to choose one of the included preset
config files. `yamllint` config files are also accepted, but will produce a warning. See `ryl`
[configuration docs](https://ryl-docs.pages.dev/config-presets/) for a list of accepted config files.

```
steps:
- name: Lint yaml files
  uses: mlibrary/action-ryl-yaml@v0.2.0
  with:
    config: standard
    strict: false
```

## Correcting errors

### Recommended method: Run `ryl` locally

If you're using a config in your repo, run `ryl format .` and `ryl check .` locally in your repo to
correct and check your yaml files. These same commands will work with the preset configs, but you
must either copy the preset config to your repo or supply a path to a copy of your desired config with
`--config-file=…`.

### Alternative: Copy corrections from Action annotations

Errors and warnings will show up in GitHub Actions annotations. This should include
all the information needed to guide manual corrections.
