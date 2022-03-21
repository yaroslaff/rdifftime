# rdifftime
Compare directories recursively and (for files which content differs) report which files are most recenly modified.

rdifftime uses md5 to compare content of files.

~~~shell
$ ./rdifftime /tmp/dir1/ /tmp/dir2/
/tmp/dir1/x.txt > /tmp/dir2/x.txt
./dir1only.txt MISS /tmp/dir2/
./dir2only.txt MISS /tmp/dir1/
~~~
In this example x.txt differs, and `/tmp/dir1/x.txt` is newer (mtime is bigger). Files which exists in both directories and has same md5sum are not reported.

Use '-i TEMPLATE' to ignore specific files (full path relative to any of dir is used, not just filename). Example:

~~~
./rdifftime /tmp/dir1/ /tmp/dir2/ -i .svn/* ./dir1*
~~~
