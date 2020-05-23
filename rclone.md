Set up a new `remote` (google drive, onedrive, etc...)
: `rclone config`

List only files: size and path
: `rclone ls -max-depth=1 foo:/bar/`

List only files: size, modification time and path
: `rclone lsl -max-depth=1 foo:/bar/`

List only directories/containers/buckets
: `rclone lsd -max-depth=1 foo:/bar/`

List files and directories: only names
: `rclone lsf -max-depth=1 foo:/bar/`

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
eyJoaXN0b3J5IjpbNzM4NTAyMjMxLC0xNzcxNzcxNTgxLC02Mz
g2NDgzOTEsMTcxODYxNzQ0LC0xMjE5NDg3NTI0LC01MDg0ODk5
MjQsODcwOTE3NTMyLDE2NDgxNzAzMzgsMzk3MDY0NDkxLC0xMT
I2NjExMTkyXX0=
-->