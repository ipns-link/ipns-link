# IPNS-Link

![Activity](https://img.shields.io/badge/Expect%20major%20updates-yes-violet.svg) ![PR](https://img.shields.io/badge/PRs-Accepted-green) ![Platform](https://img.shields.io/badge/Platform-GNU%2fLinux-blue.svg) ![Lang](https://img.shields.io/badge/Lang-Bash-cyan.svg) ![UI](https://img.shields.io/badge/UI-Command%20line-orange.svg)

Prototype implementation of [IPNS-Link](https://github.com/ipns-link/specs).

## Table of Contents  
[![tocgen](https://img.shields.io/badge/Generated%20using-tocgen-blue)](https://github.com/SomajitDey/tocgen)  
  - [IPNS-Link](#ipns-link)  
      - [Usage](#usage)  
          - [Options](#options)  
      - [Dependency](#dependency)  
      - [Test drive](#test-drive)  
  - [Contribute](#contribute)  
#####   

### Usage

```bash
ipns-link [option] <port>
```

##### Options

`-c <path to the local IPFS repository>`

​	Can also use the environment variable `IPFS_PATH` instead. Default: `~/.ipns-link`

`-g <IPNS-link-gateway>`

​	The [IPNS-Link-gateway](https://github.com/ipns-link/specs#redirect-to-ipns-link-gateway) that the [public IPFS gateways](https://ipfs.github.io/public-gateway-checker/) shall redirect to. Default: https://ipns-link.herokuapp.com

`-v`

​	Version

`-h`

​	Show help

### Dependency

- `bash`
- [`go-ipfs-cli`](https://docs.ipfs.io/install/command-line/#linux) v0.9.0 or above
- [`jq`](https://stedolan.github.io/jq/download/)
- `curl` and other standard GNU/Linux tools

### Test drive

1. Run a web-server at `localhost:8080`. For example, 

   ```bash
   mkdir my-website
   cd my-website
   echo "<a href='./file.txt'>Link1</a> <a href='/file.txt'>Link2</a>" > index.html
   echo "IPFS + IPNS rocks!" > file.txt
   python3 -m http.server 8080
   ```

2. Expose the http server through IPNS:

   ```bash
   ipns-link 8080
   ```

   Wait till you see `Published` at stderr. Also note the `IPNS-name` or`PeerID` from stderr.

3. In any modern browser, access the path `/ipns/PeerID` from any [public gateway](https://ipfs.github.io/public-gateway-checker/). For example, go to https://ipfs.io/ipns/PeerID.

4. Try the URL that was obtained from Step 2 above and access file.txt directly: https://ipfs-link.herokuapp.com/ipns/PeerID/file.txt

5. Checkout https://ipns-link.herokuapp.com. Enter `PeerID` or`PeerID/file.txt` in the input box and click GET.

# Contribute

Lots of things to be done, lots of help needed. You may contribute to this project in [multiple](https://github.com/ipns-link/contribute) ways.

[![Sponsor](https://www.buymeacoffee.com/assets/img/custom_images/yellow_img.png)](https://buymeacoffee.com/SomajitDey)
