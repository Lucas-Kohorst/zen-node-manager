# ZenCash Node Manager

This is an ansible and docker setup that can manage ZenCash nodes (both secure nodes and super nodes).

There are 3 core folders. `secnodetracker` and `zend` are both for docker configurations to run the secure node tracker and zend daemon in docker containers. The third and final folder is `ansible` which is where the deployment magic happens.

## How to use

Take a look into the `ansible/` directory for an explaination of how to use this tool to deploy zen nodes to multiple servers.

## Acknowledgements

The original inspiration for this is [this repo by WhenLamboMoon](https://github.com/WhenLamboMoon/docker-zen-node). Alot of the core architecture and setup code of this project is derived from that project. I just wanted to have my own version that I could tweak to my own desires and needs.
