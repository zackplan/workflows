# Workflows

Collection of reusable GitHub Action workflows used in our projects

## `node.yml`

### How to use

Add the following to your workflow:
```yaml
node-js-workflow:
  name: Node.js Workflow 📝
  uses: zackplan/workflows/.github/workflows/nodejs.yml@main
  with:
    node_version: 16
```

### Example

```yaml
lint-test-and-build:
  name: Lint 👓, Test ✅ & Build 🏗
  uses: zackplan/workflows/.github/workflows/nodejs.yml@main
  with:
    node_version: 16
    lint: true
    test: true
    build: true
```

### Inputs

| Name                          | Required | Type                                     | Default   | Description                                                      | 
|-------------------------------|----------|------------------------------------------|-----------|------------------------------------------------------------------|
| `node_version`                | ✓        | `string`                                 |           | Node version to use                                              |
| `package_manager`             |          | `string` (`"npm"`, `"pnpm"` or `"yarn"`) | `"npm"`   | Package manager to use                                           |
| `lint`                        |          | `boolean`                                | `false`   | Whether to do linting                                            |
| `lint_script`                 |          | `string`                                 | `"lint"`  | Name of the script in package.json that does linting             |
| `lint_continue_on_error`      |          | `boolean`                                | `false`   | Whether to continue when an error occurs while doing linting     |
| `check`                       |          | `boolean`                                | `false`   | Whether to run checks                                            |
| `check_script`                |          | `string`                                 | `"check"` | Name of the script in package.json that runs checks              |
| `check_continue_on_error`     |          | `boolean`                                | `false`   | Whether to continue when an error occurs while running checks    |
| `test`                        |          | `boolean`                                | `false`   | Whether to run tests                                             |
| `test_script`                 |          | `string`                                 | `"test"`  | Name of the script in package.json that runs tests               |
| `test_continue_on_error`      |          | `boolean`                                | `false`   | Whether to continue when an error occurs while running tests     |
| `build`                       |          | `boolean`                                | `false`   | Whether to run the build                                         |
| `build_script`                |          | `string`                                 | `"build"` | Name of the script in package.json that runs the build           |
| `build_continue_on_error`     |          | `boolean`                                | `false`   | Whether to continue when an error occurs while running the build |
| `build_upload`                |          | `boolean`                                | `false`   | Whether to upload the built files as an artifact                 |
| `build_upload_directory`      |          | `string`                                 | `"dist"`  | Directory to upload (for example "dist")                         |
| `build_upload_name`           |          | `string`                                 | `"build"` | Name of the artifact for the uploaded build files                |
| `build_upload_retention_days` |          | `number`                                 | `1`       | How many days to keep the artifact for the uploaded build files  |


## `python.yml`

### How to use

Add the following to your workflow:
```yaml
python-workflow:
  name: Python Workflow 📝
  uses: zackplan/workflows/.github/workflows/python.yml@main
  with:
    python_version: 16
```

### Example

```yaml
lint-and-test:
  name: Lint 👓 & Test ✅
  uses: zackplan/workflows/.github/workflows/python.yml@main
  with:
    python_version: 3.8
    lint: true
    lint_flake8: true
    lint_autopep8: true
    test: true
    test_directory: ./tests
```

### Inputs

| Name                           | Required                   | Type                                              | Default                                     | Description                                                                                     | 
|--------------------------------|----------------------------|---------------------------------------------------|---------------------------------------------|-------------------------------------------------------------------------------------------------|
| `python_version`               | ✓                          | `string`                                          |                                             | Python version to use                                                                           |
| `requirements_file`            |                            | `string`                                          | `"./requirements.txt"`                      | Text file containing the list of required dependencies                                          |
| `pip_install_in_order`         |                            | `boolean`                                         | `false`                                     | Whether to install the dependencies in the order specified in the requirements file             |
| `blender`                      |                            | `boolean`                                         | `false`                                     | Whether to setup blender and use pytest-blender for testing                                     |
| `blender_version`              | ✓ (if `blender` is `true`) | `string`                                          | `"3.0.0"` (but you should still specify it) | Blender version to use                                                                          |
| `blender_requirements_file`    |                            | `string`                                          | `"./requirements.txt"`                      | Text file containing the list of required dependencies for blender                              |
| `blender_pip_install_in_order` |                            | `boolean`                                         | `false`                                     | Whether to install the dependencies for blender in the order specified in the requirements file |
| `lint`                         |                            | `boolean`                                         | `false`                                     | Whether to do linting                                                                           |
| `lint_flake8`                  |                            | `boolean`                                         | `false`                                     | Whether to do linting using flake8 (needs to be installed)                                      |
| `lint_autopep8`                |                            | `boolean`                                         | `false`                                     | Whether to do linting using autopep8 (needs to be installed)                                    |
| `lint_continue_on_error`       |                            | `boolean`                                         | `false`                                     | Whether to continue when an error occurs while doing linting                                    |
| `test`                         |                            | `boolean`                                         | `false`                                     | Whether to run tests using pytest                                                               |
| `test_verbosity`               |                            | `number`                                          | `2`                                         | Verbosity level ("--verbosity" option)                                                          |
| `test_capture_method`          |                            | `string` (`"fd"`, `"sys"`, `"tee-sys"` or `"no"`) | `"no"`                                      | Per-test capturing method ("--capture" option)                                                  |
| `test_directory`               |                            | `string`                                          | `"./"`                                      | Directory that contains the test files                                                          |
| `test_continue_on_error`       |                            | `boolean`                                         | `false`                                     | Whether to continue when an error occurs while running tests                                    |


## `docker.yml`

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


## `webhook.yml`

### How to use

Add the following to your workflow:
```yaml
webhook-workflow:
  name: Webhook Workflow 🔗
  uses: zackplan/workflows/.github/workflows/webhook.yml@main
  with:
    url: https://example.com
```

### Secrets

| Name     | Required | Description                                                                                                                                                      |
|----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `url`    | ✓        | Webhook URL to call                                                                                                                                              |
| `secret` |          | Secret used to verify that the webhook is coming from GitHub<br/>(see https://docs.github.com/en/developers/webhooks-and-events/webhooks/securing-your-webhooks) |
