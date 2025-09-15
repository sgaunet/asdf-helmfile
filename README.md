# asdf-helmfile

[![Build](https://github.com/sgaunet/asdf-helmfile/actions/workflows/build.yml/badge.svg)](https://github.com/sgaunet/asdf-helmfile/actions/workflows/build.yml)
[![Lint](https://github.com/sgaunet/asdf-helmfile/actions/workflows/lint.yml/badge.svg)](https://github.com/sgaunet/asdf-helmfile/actions/workflows/lint.yml)

[Helmfile](https://github.com/helmfile/helmfile) plugin for the [asdf version manager](https://asdf-vm.com).

Helmfile is a declarative spec for deploying Helm charts. It lets you keep a directory of chart value files and maintain changes in version control.

## Contents

- [asdf-helmfile](#asdf-helmfile)
  - [Contents](#contents)
  - [Dependencies](#dependencies)
  - [Install](#install)
    - [Plugin](#plugin)
    - [Helmfile](#helmfile)
  - [Environment Variables](#environment-variables)
  - [Features](#features)
  - [Contributing](#contributing)
    - [Development](#development)
    - [Testing Locally](#testing-locally)
    - [Credits](#credits)
  - [License](#license)

## Dependencies

**Required:**
- `bash` (3.2+), `curl`, `tar`, `git`
- [POSIX utilities](https://pubs.opengroup.org/onlinepubs/9699919799/idx/utilities.html)

**Optional:**
- `sha256sum` or `shasum` - For checksum verification
- `df` - For disk space checking

## Install

### Plugin

```shell
asdf plugin add helmfile
# or
asdf plugin add helmfile https://github.com/sgaunet/asdf-helmfile.git
```

### Helmfile

```shell
# Show all installable versions
asdf list-all helmfile

# Install specific version
asdf install helmfile latest

# Set a version globally (on your ~/.tool-versions file)
asdf global helmfile latest

# Now helmfile commands are available
helmfile version

# Get help
asdf help helmfile
```

Check the [asdf documentation](https://asdf-vm.com/guide/getting-started.html) for more instructions on how to install & manage versions.

## Environment Variables

The plugin supports several environment variables for customization:

| Variable | Default | Description |
|----------|---------|-------------|
| `ASDF_HELMFILE_DEBUG` | `0` | Enable debug output for troubleshooting |
| `ASDF_HELMFILE_MAX_RETRIES` | `3` | Maximum retry attempts for network operations |
| `ASDF_HELMFILE_RETRY_DELAY` | `2` | Delay in seconds between retries |
| `GITHUB_API_TOKEN` | - | GitHub token for higher API rate limits |

## Features

- ✅ **Automatic retries** - Network operations are retried on failure
- ✅ **Checksum verification** - Downloads are verified when checksums are available
- ✅ **Progress indicators** - Visual feedback during downloads
- ✅ **Debug mode** - Detailed logging for troubleshooting
- ✅ **Platform detection** - Automatic detection of OS and architecture
- ✅ **Disk space checking** - Verifies available space before installation
- ✅ **Multi-platform support** - Linux, macOS, Windows (WSL)
- ✅ **Architecture support** - amd64, arm64, 386

## Contributing

Contributions of any kind are welcome! See the [contributing guide](CONTRIBUTING.md).

### Development

This project uses Task for automation:

```shell
# List available tasks
task

# Format code
task format

# Run linting
task lint

# Run tests
task test
```

### Testing Locally

```shell
asdf plugin test <plugin-name> <plugin-url> [--asdf-tool-version <version>] [--asdf-plugin-gitref <git-ref>] [test-command*]

asdf plugin test helmfile https://github.com/sgaunet/asdf-helmfile "helmfile version"
```

Tests are automatically run in GitHub Actions on push and PR.

### Credits

[Thanks goes to these contributors](https://github.com/sgaunet/asdf-helmfile/graphs/contributors)!

## License

See [LICENSE](LICENSE)