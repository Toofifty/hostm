hostm
=====

Command-line hosts file manager for bash/zsh on macOS

## Install

```bash
git clone https://github.com/Toofifty/hostm && cd hostm/
# linking (if you want to make changes)
ln -s $(pwd)/hostm /usr/local/bin/hostm

# moving (if you just want to use the util)
mv hostm /usr/local/bin/hostm
cd ..
rm -rf hostm/
```

## Usage

Commands commented out are planned but not yet implemented.

`sudo` is required to use all commands except `hostm get`.

```bash
Usage:
   hostm clean                            Clean your hosts file - move each domain to an individual line and format all entries consistently inside the hostm tags
   hostm add <ip> <domain> [domain2...]   Adds each entry seperately to your hostm file
   hostm disable <ip>                     Disable all entries for an IP
   hostm disable <domain>                 Disable all entries for a domain (usually a single entry)
   hostm enable <ip>                      Enable all entries for an IP
   hostm enable <domain>                  Enable all entries for a domain (usually a single entry)
   hostm get <ip> [enabled|disabled]      Get all entries for an IP
   hostm get <domain> [enabled|disabled]  Get all entries for a domain
#  hostm delete <ip>                      Delete all entries for an IP
#  hostm delete <domain>                  Delete all entries for a domain
#  hostm alias <domain> <domain new>      Add an extra domain as an alias for a previous
#  hostm name <ip> <name>                 Name all domains with the same IP to help organize entries
```

## Precautions

The script is not fully tested an can possibly corrupt your hosts file. A backup is taken on the first write to your hostsfile, and again before any `hostm clean`. If you have any error with your hosts file, use the following commands to restore a backup.

```bash
# view list of backups
ls /etc/hosts*

# restore single backup
sudo mv -f /etc/hosts.YYYY-MM-DD.HH:MM:SS.hmbk /etc/hosts

# restore single backup (keep backup)
sudo cp /etc/hosts.YYYY-MM-DD.HH:MM:SS.hmbk /etc/hosts
```

Because of the potential dangers on using the untested program, it will not edit your hosts file by default. You will need to change the $hosts_file variable and remove the `.t`.
