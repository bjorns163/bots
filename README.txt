Bots sourceforge web site: http://bots.sourceforge.net
Wiki/documentation: http://http://bots.readthedocs.io
Wiki/documentation: http://skilchen.github.io/bots_doc_b/
Bots is licenced under GNU GENERAL PUBLIC LICENSE Version 3; for full text: http://www.gnu.org/copyleft/gpl.html
Commercial support by EbberConsult, http://www.ebbersconsult.com


install on Linux:
     python3 setup_rpm.py  install
     pip3 install -r requirements.txt 

  
setup database SQLite in:

  /bots/config/settings.py
  cp /usr/local/lib/python3.8/site-packages/bots/install/botsdb /usr/local/lib/python3.8/site-packages/bots/botssys/sqlitedb/botsdb


Test bots engine:
 bots-engine.py
