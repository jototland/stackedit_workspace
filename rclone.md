Set up a new `remote` (google drive, onedrive, etc...)
: `rclone config`

List all objects (with size and path) in remote `foo` under  path `/bar/`
: `rclone ls foo:/bar/

List all directories/containers/buckets in remote `foo` under path `bar`
: `rclone lsd foo:/bar/`

Copy files
: `rclone copy ~/source/ foo:/dest`
`rclone copy foo:/source ~/dest`

Sync files


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY0ODE3MDMzOCwzOTcwNjQ0OTEsLTExMj
Y2MTExOTJdfQ==
-->