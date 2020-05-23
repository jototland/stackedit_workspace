Set up a new `remote` (google drive, onedrive, etc...)
: `rclone config`

List all objects (with size and path) in remote `foo` under  path `/bar/`
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

Google drive duplicated files fix
: `rclone dedupe`

serve as other protocol
: `rclone serve ftp foo:/bar/`
Protocols: `http`, `ftp`, `
mount as local directory
: `rclone mount foo:/bar/ ~/mydir/ &`
`fusermount -u ~/mydir/` 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ0NjU2MTM5NywtMTIxOTQ4NzUyNCwtNT
A4NDg5OTI0LDg3MDkxNzUzMiwxNjQ4MTcwMzM4LDM5NzA2NDQ5
MSwtMTEyNjYxMTE5Ml19
-->