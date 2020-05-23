Set up a new `remote` (google drive, onedrive, etc...)
: `rclone config`

List all objects (with size and pat h) in remote `foo` under  path `/bar/`
: `rclone ls foo:/bar/

List all directories/containers/buckets in remote `foo` under path `bar`
: `rclone lsd foo:/bar/`

Test what would happen without doing it
: `--dry-run`

Copy files
: `rclone copy ~/source/ foo:/dest/`
`rclone copy foo:/source ~/dest.`

Sync files
: file syncing is one-way, from source to destination. Unlike `copy`, `sync` will delete any file in destination, not in source.
`rclone sync ~/source/ foo:/dest/`

delete/move/etc
: see manual

Google drive duplicated files fix
: `rclone dedupe`

serve as other protocol
: `rclone serve ftp foo:/bar/`
Protocols: `http`, `ftp`, `sftp`, `dlna`, `restic`, `webdav`, possibly others...

mount as local directory
: `rclone mount foo:/bar/ ~/mydir/ &`
`fusermount -u ~/mydir/` 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3NzE3NzE1ODEsLTYzODY0ODM5MSwxNz
E4NjE3NDQsLTEyMTk0ODc1MjQsLTUwODQ4OTkyNCw4NzA5MTc1
MzIsMTY0ODE3MDMzOCwzOTcwNjQ0OTEsLTExMjY2MTExOTJdfQ
==
-->