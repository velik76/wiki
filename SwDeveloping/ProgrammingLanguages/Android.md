# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Get shell acess to device](#get-shell-acess-to-device)
  - [Sqlite in android](#sqlite-in-android)

## Get shell acess to device

Install android-tools-adb packet using classical:

```bash
sudo apt-get install android-tools-adb
```

Then in console run:

```bash
adb kill-server 
sudo adb start-server
adb shell
```

For more information about using of adb visit [Link](http://developer.android.com/tools/help/adb.html)

## Sqlite in android

SQlite stores the whole database in a file. If you have access to this file, you can work directly with the data base. Accessing the SQlite database file only works in the emulator or on a rooted device. A standard Android device will not grant read-access to the database file.

Shell access to the database It is possible to access an SQLite database on the emulator or a rooted device via the command line. For this use the following command to connect to the device.

```bash
adb shell 
```

The command adb is located in your Android SDK installation folder in the "platform-tools" subfolder. Afterwards you use the "cd" command to switch the database directory and use the "sqlite3" command to connect to a database. For example in my case:

```bash
# Switch to the data directory
cd /data/data
# Our application
cd de.vogella.android.todos
# Switch to the database dir
cd databases
# Check the content
ls
# Assuming that there is a todotable file
# connect to this table
sqlite3 todotable.db 
```

The most important commands are:

| Command | Description                                                                             |
| ------- | --------------------------------------------------------------------------------------- |
| .help   | List all commands and options                                                           |
| .exit   | Exit the sqlite3 command                                                                |
| .schema | Show the CREATE statements which were used to create the tables of the current database |
