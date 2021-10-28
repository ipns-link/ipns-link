# Host a proxy

Thanks for your interest in IPNS-Link. Welcome and Happy Hosting 😊

Let's get going. Feel free to report issues with this tutorial [here](https://github.com/ipns-link/ipns-link/issues).

## Table of Contents  
[![tocgen](https://img.shields.io/badge/Generated%20using-tocgen-blue)](https://github.com/SomajitDey/tocgen)  
  - [Host a proxy](#host-a-proxy)  
      - [Aim](#aim)  
      - [Steps](#steps)  
        - [Prelude](#prelude)  
        - [Generate key](#generate-key)  
        - [Expose the site](#expose-the-site)  
        - [Postlude](#postlude)  
#####   

### Aim

Expose an https site, e.g. `www.google.com`, with `ipns-link`. 

### Steps

#### Prelude

Install, initialize and launch daemon steps can be followed from the [Quick Start](/tutorials/QuickStart.md) tutorial.

#### Generate key

Let's now generate the IPNS-key the would later expose our server. Because the key is hard to remember, we must give it a human-friendly name, e.g. `google`.

```bash
ipns-link gen google
```

#### Expose the site

There are two ways to do this:

1. Edit the config specific to the key named `google` with 

   ```bash
   ipns-link config google
   ```

   and put `local.endpoint: "https://www.google.com"`. Then, expose `google` simply as 

   ```bash
   ipns-link expose google
   ```

2. Or, you can simply do

   ```bash
   ipns-link expose google https://www.google.com
   ```

If everything goes alright, https://www.google.com should be accessible using any IPNS-Link-Gateway within a few minutes. Try the BaseURL at any browser.

#### Postlude

Monitor, hide and shutdown steps can be followed from the [Quick Start](/tutorials/QuickStart.md) tutorial.
