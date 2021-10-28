# Command-Line Reference

This is the complete Manual for [`ipns-link`](https://github.com/ipns-link/ipns-link). In the following, angular brackets `<>` imply parameters to be provided by the user and square brackets `[]` imply optional parameters.

TL;DR : See the [Quick-Start](/tutorials/QuickStart.md) tutorial

## Table of Contents  
[![tocgen](https://img.shields.io/badge/Generated%20using-tocgen-blue)](https://github.com/SomajitDey/tocgen)  
  - [Command-Line Reference](#command-line-reference)  
      - [Synopsis](#synopsis)  
      - [Subcommands](#subcommands)  
        - [`init`](#init)  
        - [`daemon`](#daemon)  
        - [`log`](#log)  
        - [`quit`](#quit)  
        - [`gen`](#gen)  
        - [`export`](#export)  
        - [`import`](#import)  
        - [`list`](#list)  
        - [`rename`](#rename)  
        - [`del`](#del)  
        - [`expose`](#expose)  
        - [`hide`](#hide)  
        - [`config`](#config)  
        - [`version`](#version)  
      - [Config file](#config-file)  
        - [General config](#general-config)  
          - [`version`](#version)  
          - [`editor`](#editor)  
          - [`Listener`](#listener)  
          - [`Listener.port`](#listenerport)  
        - [Key-specific config](#key-specific-config)  
          - [`cache`](#cache)  
          - [`stream`](#stream)  
          - [`on_fail`](#onfail)  
          - [`host`](#host)  
          - [`local`](#local)  
          - [`local.endpoint`](#localendpoint)  
#####   

### Synopsis

```bash
ipns-link <subcmd> <args>
```

Just as like `ipfs` or `git`, each `ipns-link` command-line consists of a subcommand and its arguments.

### Subcommands

#### `init`

```bash
ipns-link init
```

Initializes/resets `ipns-link` on your machine. This is akin to `ipfs init` or `git init`. Executing this command asks for a text-editor. The repository is at `$HOME/.ipns-link`. 

#### `daemon`

```bash
ipns-link daemon
```

Launches the exposer engine on the background.

#### `log`

```bash
ipns-link log
```

Real-time monitoring what the daemon is doing. The actual log is stored at `$HOME/.ipns-link/log`.

#### `quit`

```Bash
ipns-link quit
```

Shutdown daemon.

#### `gen`

```bash
ipns-link gen <keyName>
```

Generates a [libp2p-key-pair](https://github.com/libp2p/specs/blob/master/peer-ids/peer-ids.md#keys) with the given name `<keyName>` and default config.

#### `export`

```bash
ipns-link export <keyName> [<output/path>]
```

Exports the libp2p-key-pair named `<keyName>` as the file at `<output/path>`. If no file-path is provided, the output is at `./<keyName>.key`.

#### `import`

```bash
ipns-link import <keyName> <input/path>
```

Imports the libp2p-key-pair from the file at `<input/path>` under the given name `<keyName>`.

#### `list`

```bash
ipns-link list
```

Lists all existing keys that were either generated or imported.

#### `rename`

```bash
ipns-link rename <old_keyName> <new_keyName>
```

Changes the name of any given key-pair from `<old_keyName>` to `<new_keyName>`.

#### `del`

```bash
ipns-link del <keyName>
```

Deletes an existing key-pair named `<keyName>`.

#### `expose`

```bash
ipns-link expose <keyName> [<socket>|<URL>]
```

Exposes the http(s)-server or web app at the given `<socket>` or `<URL>` using the IPNS-key `<keyName>`. The `<socket>` denotes an IPv4 TCP socket of the form, `<IP>:<port>` E.g. `127.0.0.1:8000`. If no `<socket>` or `<URL>` is provided, uses the value corresponding to `.local.destination` as given in the config from `<keyName>`. If even that value is not set, uses the default, `127.0.0.1:80`.

If the URL provided is `https://<some.domain>.<tld>`, a proxy is setup to handle the SSL.

#### `hide`

```bash
ipns-link hide <keyName>
```

Undoes a previous expose with the given key. The corresponding site would no longer be available through an IPNS-Link-Gateway, unless exposed again.

#### `config`

```bash
ipns-link config [<keyName>]
```

Shows/edits configuration associated with the given key. If no `<keyName>` is provided, shows/edits the global configuration. See the [Config file](#config-file) section for details.

#### `version`

```bash
ipns-link version
```

Shows version number of the currently installed `ipns-link`.

### Config file

Each config file is a JSON.

#### General config

Applies to the entire installation. Contains the following:

##### `version`

Stores the version of the repository. NOT to be edited by the user.

##### `editor`

Holds the command or absolute path to your favorite text-editor.

##### `Listener`

The Listener IPFS node listens for and forwards incoming connections from the IPFS world to your exposed endpoint.

##### `Listener.port`

Holds the TCP port the Listener should listen on. This is useful when your node has a public IP, yet only a (few) TCP port(s) are open for incoming/outbound connections. 

When this is unset (viz. `null` or `""`), the Listener IPFS node is setup at random TCP ports.

#### Key-specific config

Each key you generate or import has a config file associated with it. The configurations mostly hold what would be on the [IPNS-Link-Manifest](https://github.com/ipns-link/specs) when an endpoint is exposed with the corresponding key.

##### `cache`

Instructs IPNS-Link-Gateways to serve *GET* requests for paths with prefix `cache.path` from the directory hosted on IPFS that has CID=`cache.CID`. This is to be used to serve static content efficiently. 

**Example**: Put the static images, css, javascripts of your site in a directory, and pin the directory to be served via IPFS. Note the directory CID and put it as the value for `cache.CID`. To let *GET* requests with path `/static/*` be served from IPFS, add `/static/` as the value for `cache.path`.

##### `stream`

Not yet implemented.

##### `on_fail`

Provides the `URL` or `/ipfs/<CID>` or `ipns/<keyID>` that visitors are redirected to in case the Origin-server is down/offline temporarily. The default redirect is to a "Coming Soon" page.

##### `host`

Provides the hostname that IPNS-Link-Gateway should use in the `Host:` header when proxying web-requests to the exposed endpoint. For https endpoints this is configured automatically.

##### `local`

Contains everything not intended to be published with the IPNS-Link-Manifest; i.e. local configs.

##### `local.endpoint`

The default endpoint to be exposed.