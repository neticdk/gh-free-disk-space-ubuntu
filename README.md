# Free Disk Space (Ubuntu)

A lightweight, configurable GitHub Action to free up valuable disk space on hosted Ubuntu runners.

## Features

- **Diagnostic output:** Runs `df -h` before and after cleanup so you can see exactly how much space was saved.
- **Customizable cleanup:** Toggle individual pre-installed tooling, runtimes, and system directories.
- **Resilient execution:** Runs all commands safely, reporting failures as standard GitHub Actions warnings or debug logs without breaking your pipeline.

## Usage

Add the action to your workflow steps before tasks that require large amounts of disk space:

```yaml
steps:
  - name: Free Disk Space
    uses: neticdk/gh-free-disk-space-ubuntu@v1
    with:
      # Optional customization:
      # tools-cache: true
```

## Inputs

The following inputs are supported (all inputs default to `true` unless otherwise specified):

### Core Runtimes & Caches

| Input | Description | Default |
|---|---|---|
| `android` | Remove Android SDK and tools | `true` |
| `dotnet` | Remove .NET SDK and tools | `true` |
| `haskell` | Remove Haskell GHC and Cabal | `true` |
| `docker-images` | Prune all Docker images | `true` |
| `tools-cache` | Remove the hosted tools cache (`/opt/hostedtoolcache`) | `false` |
| `swap-storage` | Disable and remove swap storage | `true` |

### Package Cleanup (`apt-get`)

| Input | Description | Default |
|---|---|---|
| `apt-aspnetcore` | Remove aspnetcore apt packages | `true` |
| `apt-dotnet` | Remove dotnet apt packages | `true` |
| `apt-llvm` | Remove LLVM apt packages | `true` |
| `apt-php` | Remove PHP apt packages | `true` |
| `apt-mongodb` | Remove MongoDB apt packages | `true` |
| `apt-mysql` | Remove MySQL apt packages | `true` |
| `apt-azure-chrome-firefox-powershell-mono-mesa` | Remove Azure CLI, Chrome, Firefox, Powershell, Mono, and Mesa drivers | `true` |
| `apt-google-cloud-sdk` | Remove Google Cloud SDK | `true` |
| `apt-google-cloud-cli` | Remove Google Cloud CLI | `true` |
| `apt-autoremove` | Run `apt-get autoremove -y` | `true` |
| `apt-clean` | Run `apt-get clean` | `true` |

## Attribution

This action is inspired by [jlumbroso/free-disk-space](https://github.com/jlumbroso/free-disk-space), which has served as a valuable resource for the GitHub Actions community but appears to be no longer actively maintained.

