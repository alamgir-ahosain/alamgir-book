
<h1>Package Management in Linux</h1>

A system to **install, update, query, or remove software packages**.

* Debian-based systems (like Ubuntu) use **dpkg** at a low level.
* **apt-get** is a front-end to dpkg, easier for everyday use.
* Most commands require **administrative privileges** → use `sudo`.


Example : 

```bash
sudo apt-get update             # Update package list

apt-cache search cow            # Search for packages
# Output: cowsay - configurable talking cow

sudo apt-get install cowsay     # Install a package
cowsay 'NDG Linux Unhatched'    # Run the package
sudo apt-get upgrade            # Upgrade all installed packages
sudo apt-get remove cowsay      # Remove a package but keep config files
sudo apt-get purge cowsay       # Remove package completely including config files
```