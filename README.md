# px

A simple cli to interact with Proxmox VE API. I wrote this mainly as an easy shortcut to launch remote viewer on Proxmox VE virtual machines without having to mess with the website.

![outm](https://github.com/eskerda/px/assets/208952/62c124c2-e3bd-416c-9bb4-117f50fa571f)



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
