# Get Next Version

Get Next Version is a GitHub Action that calculates the next semantic version (major.minor.patch) based on the latest Git tag.

## Usage

```yml
- name: Get next version
  id: get_version
  uses: danielboxer/get-next-version@v1.0.0
  with:
    # which part of the version to increment (major, minor, patch)
    increment: patch
    # optional: manually set a version instead of auto-incrementing
    version: null
    # optional: add "v" prefix to version
    use_v_prefix: null

- name: Create release
  uses: softprops/action-gh-release@v2
  with:
    # use the new version generated by this action
    tag_name: ${{ steps.get_version.outputs.new_version }}
```

## Notes

- If no previous tag exists, defaults to 0.1.0
