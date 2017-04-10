# sampeu
Base Map Engine for Geospatial Framework

## Installation
### Ubuntu 16.04
apt-get install cgi-mapserver
Location on :
/usr/lib/cgi-bin/mapserv

apt-get install libpcre3 libpcre3-dev
pip install virtualenv
pip install uwsgi
pip install MyMapProxy



#### Nginx
server {
    listen 80;
    server_name map.vas.web.id;

    location / {
        include         uwsgi_params;
        uwsgi_pass      unix:/var/www/awangga/sampeu.sock;
    }
}

#### Make it as service
virtualenv sampeuenv
/bin/bash
source sampeuenv/bin/activate
deactivate

edit sampeu.service

cp sampeu.service /etc/systemd/system/

## Editing Mapdata
### Edit Atribut in dbf
by using dbfpy. try it with python cli
```sh
from dbfpy import dbf
db = dbf.Dbf("00.dbf")
db[23]
rec = db[23]
rec['PROVINSI']= 'ACEH'
rec.store()
del rec
db.close()
```