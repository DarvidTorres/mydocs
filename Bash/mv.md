`mv file1 file2`: If `file2` does not exist, then `file1` is renamed `file2`. If `file2` exists, its contents are silently replaced with the contents of `file1`.

`mv -i file1 file2`: Like above however, since the `-`i (interactive) option is specified, if `file2` exists, the user is prompted before it is overwritten with the contents of `file1`.

`mv file1 file2 dir1`: `file1` and `file2` are moved to `dir1`. If `dir1` does not exist, `mv` will exit with an error.

`mv dir1 dir2`: If `dir2` does not exist, then `dir1` is renamed `dir2`. If `dir2` exists, the directory `dir1` is moved within directory `dir2`.

`mv *.extension dir`: move .extension files to dir
