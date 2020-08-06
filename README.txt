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
  cp /usr/local/lib/python3.8/site-packages/bots/install/botsdb /usr/local/lib/python3.8/site-packages/bots/botssys/sqlitedb/botsdb

If you are migrating from old bots version you need to update your databasefile. For sqllite use for example https://sqlitebrowser.org/dl/
Since Django 1.8 AbstractUser.last_login allows null values, so whe need to update the database.
go to auth_user table and modify the tabel go to last_login an remove the Not Null (NN) and press ok. then its saved.

Test bots engine:
 bots-engine.py
 
 
