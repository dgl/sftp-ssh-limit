# Restricted SFTP

This script implements SFTP restriction for Linux, based on user namespaces and bind mounts.

## How to use?

To configure this, copy `sftp-ssh-limit` to `~/bin/sftp-ssh-limit`:

```console
mkdir -p ~/bin
curl -Lo ~/bin/sftp-ssh-limit https://raw.github.com/dgl/sftp-ssh-limit/sftp-ssh-limit
chmod 755 ~/bin/sftp-ssh-limit
```

Then set up an SSH key in `~/.ssh/authorized_keys` with the following options
(edit the line to add these before the key) where `$HOME/Media`, etc. are the
directories to allow access to:

```
restrict,command="$HOME/bin/sftp-ssh-limit $HOME/Media $HOME/Pictures" ssh-ed25519...rest-of-key-all-on-one-line
```

You can also add -R before the list of directories to make the key only give read-only access.
