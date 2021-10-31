# IPNS-Link

[![PR](https://img.shields.io/badge/PRs-Accepted-green)](https://github.com/ipns-link/ipns-link/pulls) ![Platform](https://img.shields.io/badge/Platform-GNU%2fLinux-blue.svg) ![Lang](https://img.shields.io/badge/Lang-Bash-cyan.svg) ![UI](https://img.shields.io/badge/UI-Command%20line-orange.svg)

Prototype implementation of [IPNS-Link](https://github.com/ipns-link/specs). 

### TL;DR

Expose dynamic site / web app / server-side code with IPNS. Run your http-server at localhost and get a URL that is basically an IPNS key. Put the key at any IPFS gateway (e.g. https://ipfs.io) or IPNS-Link-Gateway (e.g. https://ipns.live) in your browser and your site loads.

### Usage

See [Manual](/MANUAL.md).

### Test drive

Follow [Quick-Start](/tutorials/QuickStart.md).

### [Tutorials](/tutorials/)

### Notes

- This is just a proof-of-concept and is by no means foolproof. Although it mostly works, optimizations and enhancements are possible. 

- To keep things simple, [Manifest encryption and HLS stream using IPNS](https://github.com/ipns-link/specs) have been left out for now.

- Those who turn away from IPFS because of its huge bandwidth consumption need not worry. IPNS-Link takes great pains to [work around](https://github.com/ipns-link/specs) this.
- If your website contains relative URLs of the form `/ipfs/CIDhash`, IPNS-Link serves the corresponding resources from IPFS, decreasing the load on your server.
- You can configure IPNS-Link to serve all static content in your website, such as images, CSS and javascripts, from IPFS thus effectively acting as a CDN.
- IPNS-Link uses IPFS's built in NAT traversal tools. So a public IP is not a must, but is always preferable.
- You can configure IPNS-Link to redirect visitors whenever your machine goes offline for a while. So even intermittent connectivity is workable.

### Community

[GitHub Discussions](https://github.com/ipns-link/ipns-link/discussions)

[Reddit](https://www.reddit.com/r/ipns_link/)

### Contribute

[![Contribute](https://img.shields.io/badge/Contribute%20to-IPNS--Link-brightgreen)](https://github.com/ipns-link/contribute) 

### Donate

[![Sponsor](https://www.buymeacoffee.com/assets/img/custom_images/yellow_img.png)](https://buymeacoffee.com/SomajitDey)

