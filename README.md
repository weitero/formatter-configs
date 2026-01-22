# Code Formatter Configuration Files

| Configuration File       | Language(s)                                                                                                  |
| :----------------------- | :----------------------------------------------------------------------------------------------------------- |
| `_clang-format`          | [![c_cpp](https://skillicons.dev/icons?i=c,cpp)](https://skillicons.dev)                                     |
| `air.toml`               | [![r](https://skillicons.dev/icons?i=r)](https://skillicons.dev)                                             |
| `biome.json`             | [![multi](https://skillicons.dev/icons?i=css,html,js,markdown,react)](https://skillicons.dev)                |
| `dot_djlintrc`           | Jinja                                                                                                        |
| `dot_editorconfig`       | [![bash](https://skillicons.dev/icons?i=bash)](https://skillicons.dev)                                       |
| `dot_prettierrc.json`    | AWK, Jinja, [![multi](https://skillicons.dev/icons?i=css,html,js,markdown,react,ts)](https://skillicons.dev) |
| `dot_sql-formatter.json` | [![sql](https://skillicons.dev/icons?i=mysql,postgresql,sqlite)](https://skillicons.dev)                     |
| `ruff.toml`              | [![python](https://skillicons.dev/icons?i=py)](https://skillicons.dev)                                       |
| `rustfmt.toml`           | [![rust](https://skillicons.dev/icons?i=rust)](https://skillicons.dev)                                       |
| `stylua.toml`            | [![lua](https://skillicons.dev/icons?i=lua)](https://skillicons.dev)                                         |
| `taplo.toml`             | TOML                                                                                                         |
| `tombi.toml`             | TOML                                                                                                         |

## Use Prettier (with plugins) in a local project

This repo includes a Prettier config at `dot_prettierrc.json` that enables extra
formatters via plugins (for example: AWK or Jinja templates).

### 1) Add Prettier + plugins to your project

In your project directory, initialize npm (if needed) and install Prettier:

```sh
npm init -y
npm add -D prettier
```

Then install any plugins you want to use (choose one or both):

```sh
npm add -D prettier-plugin-awk
npm add -D prettier-plugin-jinja-template
```

### 2) Add the config file

Copy this repo’s config into your project as `.prettierrc.json`:

```sh
cp /path/to/formatter-configs/dot_prettierrc.json .prettierrc.json
```

Prettier will load plugins from `node_modules` based on the `plugins` list in
the config.

If you only installed one plugin, remove the other entry from the `plugins`
array in `.prettierrc.json` so your config matches what’s installed.

### 3) Run Prettier

Format everything (adjust globs as you like):

```sh
npx prettier . --write
```

Check formatting in CI:

```sh
npx prettier . --check
```

### (Optional) Add npm scripts

Add these to your `package.json`:

```json
{
  "scripts": {
    "format": "prettier . --write",
    "format:check": "prettier . --check"
  }
}
```

## SQL formatter config

`dot_sql-formatter.json` is configured with `"language": "sqlite"` by default.
If you want to format MySQL or PostgreSQL dialects, you need to manually change
the `language` setting in that file (for example, to `mysql` or `postgresql`).
