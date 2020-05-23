Set up a new `remote` (google drive, onedrive, etc...)
: `rclone config`

List size and path of files
: `rclone ls -max-depth=1 foo:/bar`

List size, modification time and path of files
: `rclone lsl -max-de`

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
eyJoaXN0b3J5IjpbLTY4ODQzNTAzMiwtMTc3MTc3MTU4MSwtNj
M4NjQ4MzkxLDE3MTg2MTc0NCwtMTIxOTQ4NzUyNCwtNTA4NDg5
OTI0LDg3MDkxNzUzMiwxNjQ4MTcwMzM4LDM5NzA2NDQ5MSwtMT
EyNjYxMTE5Ml19
-->