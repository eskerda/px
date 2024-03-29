# px

A simple cli to interact with Proxmox VE API. I wrote this mainly as an easy shortcut to launch remote viewer on Proxmox VE virtual machines without having to mess with the website.

![outm](https://github.com/eskerda/px/assets/208952/62c124c2-e3bd-416c-9bb4-117f50fa571f)

# Requirements

This script assumes `bash`, `jq`, `fzf` and `remote-viewer` (virt-viewer) are available on your system.

## Usage


```

                      ____
                 ____|    \
                (____|     `._____
                 ____|       _|___
                (____|     .'
                     |____/

            px: a simple proxmox VE API cli

Usage: px action [options...]

Options:
  -n, --node        set target node (alias: $PX_NODE)
  -H, --host        set target host (alias: $PX_HOST)
  -t, --token       set auth token  (alias: $PX_TOKEN)
  -v, --verbose     echo every command that gets executed
  -h, --help        display this help

Commands:
  help                      Show usage

  ls                        List QEMU VMs

  spice <vmid>              Show spice config file for a given VM id

  rv [<vmid>]               Launch remote viewer on VM id. If none is specified
                            list VMs and filters them with fzf

  rpc <url> [options...]    Call proxmox API url with extra curl args
                            API docs: https://pve.proxmox.com/pve-docs/api-viewer/

```

To interact with Proxmox VE API you will need to create an API token. Simply go to pool view / datacenter / API Tokens / Add. Then Select user / Add token ID / Either disable privilage separation or grant `["perm","/vms/{vmid}",["VM.Console"]]`

This token must be either set as `$PX_TOKEN` on the environment, or passed along with a `-t` or `--token` flag. Set also the proxmox host and if desired, a default node.

```bash
$ px rpc json/nodes -t user@realm!some-key-id=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx -H 192.168.8.101
$ export PX_TOKEN='user@realm!some-key-id=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx'
$ export PX_HOST='192.168.8.101'
$ px rpc json/nodes
$ export PX_NODE='hope'
```

Now, to open remote-viewer on a VM, simply run `px rv` and select a VM.

### Pass extra arguments to remote-viewer

```bash
$ px rv -- --full-screen
```

### Explore Proxmox VE API

See available resources at https://pve.proxmox.com/pve-docs/api-viewer/

```bash
$ px rpc json/nodes
$ px rpc json/nodes/<node>/qemu
```
