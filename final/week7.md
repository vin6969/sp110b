## SQLite

SQLite database engine is an easy to install program, that let you create your database without involving a server application.

#### Windows
For Windows machines:
```
1.Download the sqlite-tools-win32-x86-3200100.zip file and unzip it.
2.From your git-bash terminal, open the directory of the unzipped folder with cd ~/Downloads/sqlite-tools-win32-x86-3200100/sqlite-tools-win32-x86-3200100/.
3.Try running sqlite with the command winpty ./sqlite3.exe. If that command opens a sqlite> prompt, congratulations! You’ve installed SQLite.
```

#### Mac OS X
For Macs, use the Mac OS X (x86) sqlite-tools package:
```
1.Install it, and unzip it.
2.In your terminal, navigate to the directory of the unzipped folder using cd.
3.Run the command mv sqlite3 /usr/local/bin/. This will add the command sqlite3 to your terminal path, allowing you to use the command from anywhere.
4.Try typing sqlite3 newdb.sqlite. If you’re presented with a sqlite> prompt, you’ve installed SQLite! Enter control + d to quit. You can also exit by typing .exit in the prompt and pressing return.
```

#### Linux
In Ubuntu or similar distributions:
```
1.Open your terminal and run sudo apt-get install sqlite3. Otherwise, use your distribution’s package managers.
2.Try typing in the command sqlite3 newdb.sqlite. If you’re presented with a sqlite> prompt, you’ve successfully created the sqlite3 command for your terminal. You can exit by typing .exit in the prompt and pressing enter.
```

#### source
https://www.codecademy.com/article/what-is-sqlite
