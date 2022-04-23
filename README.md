docker-compose stop
sudo chmod -R 777 13.0
cd 13.0
docker build -t 13.0/odoo13:20220423 .
cd\
nano yml
13.0.20220423 .
docker-compose up -d

###
install ubuntu 20.04
update
snap install docker         
apt install docker-compose
upgrade
nano docker-compose.yml
//// 
version: '2'
services:
  db:
    image: postgres:latest
    environment:
      - POSTGRES_PASSWORD=odoo
      - POSTGRES_USER=odoo
      - POSTGRES_DB=postgres
    restart: always             # run as a service
    volumes:
        - ./postgresql:/var/lib/postgresql/data

  odoo13:
    image: 13.0/odoo13:20220421
    depends_on:
      - db
    ports:
      - "8069:8069"
    tty: true
    command: -- --dev=reload

    volumes:
      - ./addons:/mnt/extra-addons
      - ./etc:/etc/odoo
    restart: always             # run as a service 
/////
docker-compose up -d
git clone https://github.com/kankankuli/addons.git
nano etc/odoo.conf
////
[options]
addons_path = /mnt/extra-addons
data_dir = /var/lib/odoo

admin_passwd = Lsf7000+
;list_db = False
list_db = True
/////
wget https://www.soladrive.com/downloads/enterprise-13.0.tar.gz
tar -zxvf enterprise-13.0.tar.gz
mv -v ~/13.0/* ~/addons/
docker-compose stop
docker-compose up -d


###
docker image rm 4bb46517cac3
docker image rmi -f xxxx
