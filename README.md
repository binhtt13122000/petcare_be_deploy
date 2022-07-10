# Pull this git repository
```bash
$ git pull origin
``` 
After that, you must change certbot's command: Replace email and hostname
# Run script to create ssl certificate
```bash
$ pwd //print working directory
> /working_directory
$ mkdir dhparam
$ cd dhparam
$ openssl dhparam -out /working_directory/dhparam-2048.pem 2048
$ ls
> dhparam-2048.pem
```
# Check server certbot, everything is ok.