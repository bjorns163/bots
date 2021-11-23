Bots sourceforge web site: http://bots.sourceforge.net
Wiki/documentation: http://http://bots.readthedocs.io
Wiki/documentation: http://skilchen.github.io/bots_doc_b/
Bots is licenced under GNU GENERAL PUBLIC LICENSE Version 3; for full text: http://www.gnu.org/copyleft/gpl.html
Commercial support by EbberConsult, http://www.ebbersconsult.com

To make bots a little more modern I upgraded the user interface and all other packages to be current versions.
Tested on Centos 8 server running:
 -Python version	   3.8.0
 -Django version	   (3, 0, 8, 'final', 0)
 -CherryPy version  18.6.0

Therefor this version is called Bots 3.8 

install on Linux:
     python3 setup_rpm.py  install
     pip3 install -r requirements.txt 

  
setup database SQLite in:

  /bots/config/settings.py
  mkdir /usr/local/lib/python3.8/site-packages/bots/botssys/sqlitedb
  cp /usr/local/lib/python3.8/site-packages/bots/install/botsdb /usr/local/lib/python3.8/site-packages/bots/botssys/sqlitedb/botsdb

If you are migrating from old bots version you need to update your databasefile. For sqllite use for example https://sqlitebrowser.org/dl/
Since Django 1.8 AbstractUser.last_login allows null values, so whe need to update the database.
go to auth_user table and modify the tabel go to last_login an remove the Not Null (NN) and press ok. then its saved.

Test bots engine:
 bots-engine.py
 
 
 
 ==Full install instruction Redhat 3.8==
#during install of redhat i created a user ediflex
 
#install all packeages neede to install latest version of python.
dnf install git make gcc openssl-devel libffi-devel sqlite-devel

cd /home/ediflex/
git clone https://github.com/bjorns163/bots

cd /tmp/
wget https://www.python.org/ftp/python/3.10.0/Python-3.10.0.tgz
tar xzf Python-3.10.0.tgz
cd Python-3.10.0/


sudo ./configure --with-system-ffi --with-computed-gotos --enable-loadable-sqlite-extensions
sudo make -j ${nproc}
sudo make altinstall


#test python
python3.10 -V
pip3.10 -V

##clean up
cd /tmp/
rm -rf Python-3.10.0/
rm -f Python-3.10.0.tgz

#optional
#link command python / pip  and python3 / pip3 to this version of python and pip

sudo ln -fs /usr/local/bin/python3.10 /usr/bin/python
sudo ln -fs /usr/local/bin/python3.10 /usr/bin/python3

sudo ln -fs /usr/local/bin/pip3.10 /usr/bin/pip
sudo ln -fs /usr/local/bin/pip3.10 /usr/bin/pip3


cd /home/ediflex/bots/
python3 setup_rpm.py  install
 
#test bots 
bots-engine.py
 
#if all goes well you will see:
INFO     served at port: "9000".
INFO     platform: "Linux-4.18.0-348.el8.x86_64-x86_64-with-glibc2.28".
INFO     machine: "x86_64".
INFO     python version: "3.10.0".
INFO     django version: "(3, 0, 8, 'final', 0)".
INFO     bots version: "3.8.0".
INFO     bots installation path: "/usr/local/lib/python3.10/site-packages/bots".
INFO     config path: "/usr/local/lib/python3.10/site-packages/bots/config".
INFO     botssys path: "/usr/local/lib/python3.10/site-packages/bots/botssys".
INFO     usersys path: "/usr/local/lib/python3.10/site-packages/bots/usersys".
INFO     DATABASE_ENGINE: "django.db.backends.sqlite3".
INFO     DATABASE_NAME: "/usr/local/lib/python3.10/site-packages/bots/botssys/sqlitedb/botsdb".
INFO     DATABASE_USER: "".
INFO     DATABASE_HOST: "".
INFO     DATABASE_PORT: "".
INFO     DATABASE_OPTIONS: "{}".
INFO     Connected to database.
INFO     This run is an acceptance test - as indicated in option "runacceptancetest" in bots.ini.
INFO     In acceptance test there is no script file "bots_acceptancetest.py" to check the results of the acceptance test.
INFO     Run "new".
INFO     Run active routes from database that are in default run: "[]".
INFO     Bots Report; type: new, time: 2021-11-23 16:16:46
    0 files received/processed in run.
    0 files send in run.

#now check if webserver will run
/usr/local/bin/bots-webserver.py

#make bots webserver run automaticly on boot
crontab -e
@reboot sleep 5 && /usr/local/bin/bots-webserver.py
