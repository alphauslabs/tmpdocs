# bluectl

[`bluectl`](https://github.com/alphauslabs/bluectl) is the official command line interface (CLI) for Alphaus services.

## Installation
You can install `bluectl` using [Homebrew](https://brew.sh/) (MacOS, Linux, and Windows through [WSL/2](https://docs.microsoft.com/en-us/windows/wsl/install)). Run the command below in a terminal:
```sh
$ brew install alphauslabs/tap/bluectl
```

## Usage
`bluectl` uses API client credentials for authentication. You can generate your API credentials either from Ripple under "Tools > API Access Tokens", or Wave(Pro) under "Settings > API Access Tokens".

To validate your credentials with `bluectl`, run the command below (replace the `{client-*}` part with your actual client id and client secret values):
```sh
$ bluectl whoami --client-id {client-id} --client-secret {client-secret}
```

If successful, it will output some information about the authenticated user.

Instead of providing your credentials to `bluectl` everytime you run a command, you can store your credentials as environment variables. Check out the "Environment setup" section [here](https://alphauslabs.github.io/docs/blueapi/authentication/#environment-setup).

You should be able to run any `bluectl` commands without the `--client-id` and `--client-secret` flags.
```sh
$ bluectl whoami
```
