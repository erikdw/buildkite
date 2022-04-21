# buildkite-go

This is a Buildkite client that's designed to be used with Buildkite builds.

### Installation

In the future we may offer compiled binaries, for now just download the source:

```
go install github.com/kevinburke/buildkite@latest
```

## Roadmap

Implement the features from e.g. github.com/kevinburke/go-circle, for example:

- Print out timings for each step of a completed build
- Download and display build logs for failed build steps
- "open" command to open a browser
- download build artifacts
- cancel or rebuild builds on a given branch

### Configuration

You need an API token that you can get from https://buildkite.com/user/api-access-tokens. Once you have that, put a file in one of the following locations:

```
- $XDG_CONFIG_HOME/buildkite
- $HOME/cfg/buildkite
- $HOME/.buildkite
```

With e.g. the following contents:

```toml
# buildkite config file: github.com/kevinburke/buildkite

# Default organization to load a token from if none of your configurations match.
default = "kevinburke"

[organizations]

    [organizations.example]
    token = "token_for_example_org"
    # If your Github org name does not match the Buildkite org name, add
    # a mapping here - in this case the org is at github.com/example_gh
    git_remotes = [
        'example_gh'
    ]

    [organizations.kevinburke]
    token = "token_for_kevinburke"
```

### Usage

`cd` to the Git repo for your Buildkite project and then write:

```
buildkite wait
```

This will wait for your build to complete and then print out summary statistics.