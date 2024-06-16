# Auto-Bump Version File

This action will automatically bump a version file in a repository. It will bump the last number in the version file.

## Inputs

### `file`
**required** The path to version file.
### `prefix`
**optional**(default: `''`) The prefix for the version number.
### `suffix`
**optional**(default: `''`) The suffix for the version number.
### `separator`
**optional**(default: `'.'`) The separator for the version number.

## Example usage

```yaml
name: Bump version file
on:
  push:
    branches:
      - main

jobs:
  bump-version-file:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout
      uses: actions/checkout@v4
    - name: Bump version file
      uses: francktrouillez/auto-bump-version-file@v1
      with:
        file: 'VERSION'
    - name: Commit and push
      run: |
        git config --local user.email "auto-bump-version-file@github-actions.com"
        git config --local user.name "Auto Bump Version File Action"
        git add .
        git commit -m "[ABVF] Bump version file"
        git push
```

## Contributions

Contributions are welcome! Feel free to open an issue or submit a pull request if you have any ideas or improvements for the action.
