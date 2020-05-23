Set up a new `remote` (google drive, onedrive, etc...)
: `rclone config`

List all objects (with size and path) in remote `foo` under  path `/bar/`
: `rclone ls foo:/bar/

List all directories/containers/buckets in remote `foo` under path `bar`
: `rclone lsd foo:/bar/`

Copy files
: `rclone copy ~/mydir/ foo:/bar`


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyMTI0MDgwMTYsMzk3MDY0NDkxLC0xMT
I2NjExMTkyXX0=
-->