# px: A simple proxmox VE API cli

A simple cli to interact with Proxmox VE API

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
