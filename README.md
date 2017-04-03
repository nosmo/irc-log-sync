irc-log-sync
========

Backup a remote irc session's logdir to a local computer, move them to
a local directory and then clean up any finished log files on the
remote system.

Assumptions
--------

The script assumes an irssi-like logdir setup using 'autolog_path =
"~/irclogs/$tag/$0.%Y-%m-%d.log";'. It moves files from the remote
directory into a similar directory structure locally. Once synced, the script removes all
remote files bar the logfile for the current day (or, worst case
scenario, the current day and the day before assuming a change of day
mid-sync).

Config
-------
The script takes a very simple configuration file of the following format:

```
{
    "user": "my_remote_user",
    "host": "myirc.example.com",
    "backup_root": "/home/user/mybackups/",
    "second_dir_behaviour": "skip"
}
```

With user being the ```remote user```, ```host``` being the remote
host upon which the logs are stored, ```backup_root``` the local
directory within which the files are to be stored, and
```second_dir_behaviour``` controlling the behaviour when the script
encounters a network with a name that ends with a "2", which generally
indicates a duplicate connection.
