# create archive
```sh
tar -czvf .\000_000.tar.gz
```

# extract archive
```sh
tar -xzvf .\000_000.tar.gz -C /tmp/-
```
`-C /tmp/` = change directory before

# list archive content
```sh
tar -ztvf .\000_000.tar.gz
```

# exclude file / dir 
```sh
tar -ztvf .\000_000.tar.gz --exclude='README.md'
```

# run tar in background
add &
```sh
tar -xzvf .\000_000.tar.gz &
```

# search inside archive files content 
```sh
zgrep -Hna 'search' .\000_000.tar.gz
```

# mans 
man tar 
man zgrep

# cools stuff:
- https://askubuntu.com/questions/147234/how-to-automatically-archive-a-directory
- https://help.ubuntu.com/community/rsync
- https://help.ubuntu.com/community/CronHowto
- https://stackoverflow.com/questions/4495266/cron-compress-files
- https://wipetools.tuxfamily.org/nautilus-wipe.html
- https://gnupg.org/
- https://otr.cypherpunks.ca/
