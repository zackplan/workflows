# Workflows

Collection of reusable GitHub Action workflows used in our projects

## `node.yml` - WIP

### How to use

Add the following to your workflow:
```yaml
node-js-workflow:
  name: Node.js Workflow 📝
  uses: zackplan/workflows/.github/workflows/node.yml@main
  with:
    node_version: 16
```

### Example

```yaml
lint-test-and-build:
  name: Lint 👓, Test ✅ & Build 🏗
  uses: zackplan/workflows/.github/workflows/node.yml@main
  with:
    node_version: 16
    lint: true
    test: true
    build: true
```

### Inputs

| Name                          | Required | Type                                       | Default   | Description                                                      | 
|-------------------------------|----------|--------------------------------------------|-----------|------------------------------------------------------------------|
| `node_version`                | ✓        | `string`                                   |           | Node version to use                                              |
| `package_manager`             |          | `string` (`"npm"` or `"pnpm"` or `"yarn"`) | `"npm"`   | Package manager to use                                           |
| `lint`                        |          | `boolean`                                  | `false`   | Whether to do linting                                            |
| `lint_script`                 |          | `string`                                   | `"lint"`  | Name of the script in package.json that does linting             |
| `lint_continue_on_error`      |          | `boolean`                                  | `false`   | Whether to continue when an error occurs while doing linting     |
| `check`                       |          | `boolean`                                  | `false`   | Whether to run checks                                            |
| `check_script`                |          | `string`                                   | `"check"` | Name of the script in package.json that runs checks              |
| `check_continue_on_error`     |          | `boolean`                                  | `false`   | Whether to continue when an error occurs while running checks    |
| `test`                        |          | `boolean`                                  | `false`   | Whether to run tests                                             |
| `test_script`                 |          | `string`                                   | `"test"`  | Name of the script in package.json that runs tests               |
| `test_continue_on_error`      |          | `boolean`                                  | `false`   | Whether to continue when an error occurs while running tests     |
| `build`                       |          | `boolean`                                  | `false`   | Whether to run the build                                         |
| `build_script`                |          | `string`                                   | `"build"` | Name of the script in package.json that runs the build           |
| `build_continue_on_error`     |          | `boolean`                                  | `false`   | Whether to continue when an error occurs while running the build |
| `build_output_directory`      |          | `string`                                   | `"dist"`  | Directory where the built files are (for example "dist")         |
| `build_upload`                |          | `boolean`                                  | `false`   | Whether to upload the built files as an artifact                 |
| `build_upload_name`           |          | `string`                                   | `"build"` | Name of the artifact for the uploaded build files                |
| `build_upload_retention_days` |          | `number`                                   | `1`       | How many days to keep the artifact for the uploaded build files  |

## `docker.yml` - WIP

### How to use

Add the following to your workflow:
```yaml
docker-workflow:
  name: Docker Workflow 🐳
  uses: zackplan/workflows/.github/workflows/docker.yml@main
  with:
    image_name: vendor/image
```

### Inputs

| Name         | Required | Type     | Default     | Description                                     |
|--------------|----------|----------|-------------|-------------------------------------------------|
| `image_name` | ✓        | `string` |             | Name of the built docker image                  |
| `context`    |          | `string` | `"."`       | Context for the build (where the Dockerfile is) |
| `registry`   |          | `string` | `"ghcr.io"` | Docker registry to upload the image to          |
