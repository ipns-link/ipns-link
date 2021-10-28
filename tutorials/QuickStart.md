# Quick Start / Demo

Thanks for your interest in IPNS-Link. Welcome and Happy Hosting 😊

Let's get going. Feel free to report issues with this tutorial [here](https://github.com/ipns-link/ipns-link/issues).

## Table of Contents  
[![tocgen](https://img.shields.io/badge/Generated%20using-tocgen-blue)](https://github.com/SomajitDey/tocgen)  
  - [Quick Start / Demo](#quick-start--demo)  
      - [Aim](#aim)  
      - [Steps](#steps)  
        - [Install `ipns-link`](#install-ipns-link)  
        - [Initialize](#initialize)  
        - [Launch the daemon](#launch-the-daemon)  
        - [Generate key](#generate-key)  
        - [Expose our server](#expose-our-server)  
        - [Monitor](#monitor)  
        - [Undo expose if needed](#undo-expose-if-needed)  
        - [Shutdown daemon when done](#shutdown-daemon-when-done)  
#####   

### Aim

Expose local web-server running at, say, port `8000` with `ipns-link`. 

### Steps

#### Install `ipns-link`

```bash
git clone https://github.com/ipns-link/ipns-link
cd ipns-link
```

If you have `sudo` privilege, 

```bash
sudo install ipns-link /usr/local/bin/
```

Otherwise, 

```bash
mkdir -p ~/.bin
cp ipns-link ~/.bin
export PATH="${PATH}":"${HOME}"/.bin
```

Also put the last command in your `.bashrc` file.

#### Initialize

```bash
ipns-link init
```

This asks for your favorite text-editor. Provide the corresponding command or absolute path to the executable when prompted.

**Note:** You can always change the editor with `ipns-link config`.

#### Launch the daemon

```bash
ipns-link daemon
```

#### Generate key

Let's now generate the IPNS-key the would later expose our server. Because the key is hard to remember, we must give it a human-friendly name, e.g. `my-site`.

```bash
ipns-link gen my-site
```

#### Expose our server

There are two ways to do this:

1. Edit the config specific to the key named `my-site` with 

   ```bash
   ipns-link config my-site
   ```

   and put `local.endpoint: "http://localhost:8000"`. Then, expose `my-site` simply as 

   ```bash
   ipns-link expose my-site
   ```

2. Or, you can simply do

   ```bash
   ipns-link expose my-site localhost:8000
   ```

If everything goes alright, our site should be accessible using any IPNS-Link-Gateway within a few minutes. Try the URL shown at the screen, for example. You can even grab the `/ipns/<key>` part from the URL and use any good old [IPFS-gateway](https://ipfs.github.io/public-gateway-checker/), e.g. `https://ipfs.io/ipns/<key>/`. It would redirect the browser to an IPNS-Link-Gateway.

**Note**: If you wanna expose `localhost:80` instead, just do `ipns-link expose my-site`, because that endpoint is the default endpoint.

#### Monitor

You can check the list of exposed servers anytime using 

```bash
ipns-link exposed
```

 Check on the daemon anytime using 

```bash
ipns-link log
```

#### Undo expose if needed

If we need to take our exposed site offline, simply

```bash
ipns-link hide my-site
```

This would only hide `my-site` and not any other site exposed by the daemon.

#### Shutdown daemon when done

When you need to shutdown everything, just

```bash
ipns-link quit
```
