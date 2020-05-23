Set up a new `remote` (google drive, onedrive, etc...)
: `rclone config`

List all objects (with size and path) in remote `foo` under  path `/bar/`
: `rclone ls foo:/bar/

List all directories/containers/buckets in remote `foo` under path `bar`
: `rclone lsd foo:/bar/`

Test what would happen without doing it
: `--dry-run`

Copy files
: `rclone copy ~/source/ foo:/dest`
`rclone copy foo:/source ~/dest`

Google drive duplicated files fix
: `rclone dedupe`


<!--stackedit_data:
eyJoaXN0b3J5IjpbODcwOTE3NTMyLDE2NDgxNzAzMzgsMzk3MD
Y0NDkxLC0xMTI2NjExMTkyXX0=
-->