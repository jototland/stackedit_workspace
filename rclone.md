Set up a new `remote` (google drive, onedrive, etc...)
: `rclone config`

List files and directories: only names
: `rclone lsf -max-depth=1 foo:/bar/`

List only files: size and path
: `rclone ls -max-depth=1 foo:/bar/`

List only files: size, modification time and path
: `rclone lsl -max-depth=1 foo:/bar/`

List only directories/containers/buckets
: `rclone lsd -max-depth=1 foo:/bar/`

List everything in JSON
: `rclone lsjson --max-depth=1 foo:/bar/`

List recursively
: replace `--max-depth=1` with `-R` above

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
eyJoaXN0b3J5IjpbLTE3Mzc4NTcxMzcsLTE3Mzc4NTcxMzcsLT
E3NzE3NzE1ODEsLTYzODY0ODM5MSwxNzE4NjE3NDQsLTEyMTk0
ODc1MjQsLTUwODQ4OTkyNCw4NzA5MTc1MzIsMTY0ODE3MDMzOC
wzOTcwNjQ0OTEsLTExMjY2MTExOTJdfQ==
-->