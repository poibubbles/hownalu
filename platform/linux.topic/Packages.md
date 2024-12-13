Verifying integrity via RPM database, RPM file, and `diff`:
```
rpm -Va

rpm -V httpd

dnf --downloadonly --downloaddir=. reinstall httpd
rpm -Vp httpd*.rpm

mkdir tmp_httpd
rpm2cpio httpd*.rpm | cpio -idmv -D tmp_httpd
diff /actual/file tmp_httpd/rpm/file
```

And to restore file modification times after resetting the content (restoring
size and MD5):
```
ORIGINAL_DATE=`date -R -r tmp_httpd/rpm/file`
MODIFIED_DATE=`date -R -r /actual/file`
touch -d "$ORIGINAL_DATE" /actual/file
# or
touch -d "$(date -R -r tmp_httpd/rpm/file)" /actual/file
```

Did ya know?:
```
touch -d "$(date -R -r file) - 2 hours" file
touch -r thisfile thatfile   # thisfile's mtime
```
