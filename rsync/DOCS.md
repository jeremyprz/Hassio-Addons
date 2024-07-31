## Precondition

Make sure to have `rsync` installed on the remote machine. In case the addon gives you an `bash: rsync: command not found` in the logs `rsync` is missing there.

## Key files

The addon generates its own key files when no file is found at the specified location. If you use your own key make sure it is passwordless.

## Config

Example config:

```yaml
private_key_file: /ssl/rsync/id_rsa
username: user
folders:
  - source: /config
    destination: /home/user/config-target
  - source: johndoe@mycomputer.local:/home/user/cool-playlists
    destination: /media/playlists
    options: '-archive --recursive --compress'
```

### `private_key_file`

The private key for the authentification on the remote machine. It specifies also the location of the generated key-pair if no key file is found.
The location of the file is fixed to the `/ssl` volume.

### `folders`

The list of folders you want to sync with the remote machine.

### `folders` - `source`

The source for rsync.

### `folders` - `destination`

The destination for rsync

### `folders` - `options` (optional)

Use your own options for rsync. This string is replacing the default one and get directly to rsync. The default is `--archive --recursive --compress --delete --prune-empty-dirs`.

### `remote_port` (optional)

The ssh port on the remote machine. If not set the default `22` is assumed.

