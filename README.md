# bkup

An incremental backup system written in bash.

## How it works

It creates a tar ball of the directory and then every time after that, it
captures the diff. Any of the history points can be restored to. If a backup is
created after a restore, the restore gets written to the end of the history.
This means that you can restore to before the restore.

## Example

```
$ ./backup . ~/backup_dir
$ ./list ~/backup_dir/
backup_2021-07-04_16-50-56.tar
$ ./backup . ~/backup_dir/
$ ./list ~/backup_dir/
backup_2021-07-04_16-50-56.tar
backup_2021-07-04_16-51-26.tar
$ ./restore ~/backup_dir/backup_2021-07-04_16-51-26.tar
Restoring from backup_2021-07-04_16-50-56.tar
Restoring from backup_2021-07-04_16-51-26.tar
Restore dir found
Restore complete
$ ./restore ~/backup_dir
Restoring from backup_2021-07-04_16-50-56.tar
Restoring from backup_2021-07-04_16-51-26.tar
Restore complete
```

