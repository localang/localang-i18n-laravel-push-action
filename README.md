# I18n Laravel Push Action

This action pushes i18n keysets from Laravel project to [localang.xyz](https://localang.xyz) service.

## Inputs

### `api-key`

**Required** API Key to update translations on [localang.xyz](https://localang.xyz). [See documentation](https://docs.localang.xyz/docs/localang/api#obtaining-a-token)

### `project-id`

**Required** ID of project on [localang.xyz](https://localang.xyz). [See documentation](https://docs.localang.xyz/docs/localang/api#project-id)

### `folder`

The folder with keysets. `lang` by default. The path should be from the root of the project. Without `/` at the end. For example, `my/path/to/langs`.

## Example workflow

**.github/workflows/push-translations.yaml**:

```yaml
name: Push Translations to Localang

on:
  push:
    branches:
      - master

jobs:
  push-translations:
    runs-on: ubuntu-latest

    steps:
      - name: Check out the repository
        uses: actions/checkout@v3
        with:
          fetch-depth: 0

      - name: Push translations
        uses: localang/localang-i18n-laravel-push-action@v0.0.1
        with:
          api-key: ${{ secrets.LOCALANG_API_KEY }}
          project-id: 1
          folder: lang
```