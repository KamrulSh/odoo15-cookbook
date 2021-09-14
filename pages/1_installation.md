## Installation and environment setup

### In ubuntu 20.04:

- Update, Upgrade & Prerequisites:

  ```sh
  sudo apt-get update
  sudo apt-get -y upgrade
  sudo apt install curl ca-certificates
  ```

- Create Odoo user and group:

  ```sh
  sudo adduser --system --home=/opt/odoo --group odoo
  ```

- Install Ubuntu dependencies:

  ```sh
  sudo apt install git python3-pip build-essential wget python3-dev python3-venv python3-wheel libxslt-dev libzip-dev libldap2-dev libsasl2-dev python3-setuptools node-less python3-psycopg2
  ```

- Install Python dependencies:

  ```sh
  sudo -H pip3 install -r https://raw.githubusercontent.com/odoo/odoo/master/requirements.txt
  ```

- Python Web Dependencies:

  ```sh
  sudo apt-get install -y npm
  sudo ln -s /usr/bin/nodejs /usr/bin/node
  sudo npm install -g less less-plugin-clean-css
  sudo apt-get install node-less
  sudo python3 -m pip install libsass
  ```

- Add PostgreSQL GPG key & repository:

  ```sh
  # Install
  sudo apt-get install software-properties-common
  sudo apt-get install python3-software-properties

  # Add GPG Key:
  wget -q https://www.postgresql.org/media/keys/ACCC4CF8.asc -O- | sudo apt-key add -

  # Create a PPA file for PostgreSQL
  sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ focal-pgdg main" >> /etc/apt/sources.list.d/pgdg.list'

  # Install the latest PostgreSQL server
  sudo apt update
  sudo apt-get install postgresql postgresql-contrib
  # Press ‘y’ for any confirmation prompted
  ```

- Secure PostgreSQL default Database

  ```sh
  # Login to PostgreSQL shell:
  sudo -u postgres psql

  # set root user credentials
  ALTER USER postgres PASSWORD 'any_password';
  ```

- Create Database user for Odoo:

  ```sh
  createuser -s odoo
  createuser -s pc_user_name	# give pc user name not ubuntu_user_name
  \q    # exit
  ```

- Permanent permission to read & write:

  ```sh
  sudo chown -R $USER:$USER /opt/odoo
  ```

- Clone odoo from git to the location /opt/odoo:

  ```sh
  git clone https://www.github.com/odoo/odoo --depth 1 --branch 14.0 --single-branch
  # change the folder name from odoo to odoo14
  # /opt/odoo/odoo14
  ```

- Create Odoo Log file:

  ```sh
  sudo mkdir /var/log/odoo
  sudo chown -R odoo:root /var/log/odoo
  ```

- Edit Odoo configuration file:

  ```sh
  sudo cp /opt/odoo/odoo14/debian/odoo.conf /etc/odoo.conf
  sudo chown odoo: /etc/odoo.conf
  sudo vim /etc/odoo.conf
  # install vim if you haven't installed
  ```

- Copy and paste below content in config file:

  ```sh
  # copy and paste the below text from [option] to error > press esc > type :wq > press enter

  [options]
  ; This is the password that allows database operations:
  ; admin_passwd = PASSWORD
  db_host = False
  db_port = False
  db_user = odoo
  db_password = False
  addons_path = /opt/odoo/odoo14/addons
  ;Log Settings
  logfile = /var/log/odoo/odoo.log
  log_level = error
  ```

- Install pgAdmin4:

  ```sh
  # import the repository signing GPG key and add the pgAdmin4 PPA to your system
  curl https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo apt-key add -

  sudo sh -c 'echo "deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/focal pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list'

  sudo apt update
  sudo apt install pgadmin4

  # configure pgadmin4
  sudo /usr/pgadmin4/bin/setup-web.sh

  # Press ‘y’ for any confirmation prompted
  # Go to: http://127.0.0.1/pgadmin4
  # Set email and password and you are good to go for web version
  ```

- Install Wkhtmltopdf:

  ```sh
  sudo wget https://github.com/wkhtmltopdf/packaging/releases/download/0.12.6-1/wkhtmltox_0.12.6-1.bionic_amd64.deb
  sudo dpkg -i wkhtmltox_0.12.6-1.bionic_amd64.deb
  sudo apt-get install -f
  sudo ln -s /usr/local/bin/wkhtmltopdf /usr/bin
  sudo ln -s /usr/local/bin/wkhtmltoimage /usr/bin
  ```

- Run Odoo 14 using command:

  ```sh
  # For default odoo addons
  /opt/odoo/odoo14/./odoo-bin --addons-path=/opt/odoo/odoo14/addons --xmlrpc-port=8014

  # For default odoo add custom addons
  /opt/odoo/odoo14/./odoo-bin --addons-path=/opt/odoo/odoo14/addons,/opt/odoo/odoo14/custom_addons --xmlrpc-port=8014
  ```

- Create new database from database selector:
  ```sh
  http://localhost:8014/web/database/selector
  ```

### For odoo error:

- Kill odoo process if it runs in the background

  ```sh
  pkill -f odoo
  ```
