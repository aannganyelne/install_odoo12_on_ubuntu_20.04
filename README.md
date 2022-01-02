# Install Odoo 12.0,14.0 on Ubuntu 20.04, Debian 11

## Install Postgres
```sh
sudo apt install postgresql
```
```sh
sudo su
```
```sh
su - postgres
```
```sh
createuser -P -s -e admin
```
Untuk contoh disini passwordnya `admin` , nanti bisa sesuaikan dengan isi file `conf` odoo.

```sh
exit
```
```sh
exit
```

## Install Required libs

Install nodejs, lalu install library dibawah:

### NodeJs
```sh
npm install -g less less-plugin-clean-css sass
```

### Python and Libraries
```sh
sudo apt install git python3-pip build-essential wget python3-dev \
python3-venv python3-wheel libxslt-dev libzip-dev libldap2-dev \
libsasl2-dev python3-setuptools
```
```sh
sudo python3 -m pip install virtualenv
```

### Virtualenv
```sh
python3 -m virtualenv nama_folder_virtualenv
```

### Install pip Libs
```sh
source nama_folder_virtualenv/bin/activate
```
```sh
pip install --upgrade pip
```
```sh
pip install "setuptools<58.0.2"
```
```sh
pip3 install Babel decorator docutils ebaysdk feedparser gdata \
gevent greenlet html2text Jinja2 lxml Mako MarkupSafe mock \
num2words ofxparse passlib Pillow psutil psycogreen psycopg2-binary \
pydot pyparsing PyPDF2 pyserial python-dateutil python-openid \
pytz pyusb PyYAML qrcode reportlab requests six suds-jurko vatnumber \
vobject XlsxWriter xlwt xlrd polib chardet zeep
```
```sh
pip3 install "Werkzeug<1"
```
```sh
pip3 install "libsass<1"
```

### Install wkhtmltopdf
Download [disini](https://wkhtmltopdf.org/downloads.html)

```sh
sudo dpkg -i nama_file_wkhtmltopdf.deb
```
```sh
sudo apt install -f
```

### Install Odoo Via Git

Untuk odoo 12:
```sh
git clone https://www.github.com/odoo/odoo --depth 1 --branch 12.0 --single-branch nama_project_odoo
```

Untuk odoo14:
```sh
git clone https://www.github.com/odoo/odoo --depth 1 --branch 14.0 --single-branch nama_project_odoo
```

```sh
cd nama_project_odoo
```
```sh
mkdir data
```
```sh
touch odoo.conf
```

Bual file konfigurasi (conf) misalnya `odoo.conf` . Isi odoo.conf:
```conf
[options]
; This is the password that allows database operations:
admin_passwd = admin
db_host = localhost
db_port = 5432
db_user = admin
db_password = admin
xmlrpc_port = 8069
addons_path = /lokasi/nama_project_odoo/addons
data_dir = /lokasi/nama_project_odoo/data
```

### Init Running odoo
```sh
source nama_folder_virtualenv/bin/activate
```
```sh
cd lokasi/folder/nama_project_odoo
```
```sh
./odoo-bin -c odoo.conf -d nama_db
```

### Open Odoo
http://127.0.0.1:8069
