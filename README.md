## Notes to Reviewer

website: http://ec2-52-26-72-67.us-west-2.compute.amazonaws.com/

remote login:
`ssh -i ~/.ssh/udacity_key.rsa grader@52.26.72.67 -p 2200`
my private key:
```
-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEApjQtJHOEHPA9y2OV1H6smQb4m64vgPD7SUdFnRYyuKPvAhSR
gf6M0ueTCMQrW+iphYQDWg3DPUM4o7xkALt0P/R2yzehq8oxGbkhMelsZYBt7Qpn
ISbu2OpZnEaIBDOF0u4i9kf7+ASt2xDwg0JuvWkc6OSYVF3DknVc6LwUx+Vd+w7f
k248aQrZ6ETVYCnCoKo2lq2OrZnWnHORil362ku1PYtuMNw1xBa46Y31huf4ljWr
EY+JEMMhJcgkdvL4AxyNA8gQBUxUMidSKeAvhK3atg3KeUrVQjCmjFFOi+3nIF7H
kPo/5lHRzQvLTJ6KoIhV9YIftIIPQuNpbFvebQIDAQABAoIBAD0EUr5bGll1aXpN
6SfGCZ90i7i7zfzMe7R/UfNFvwFCTfC5lGHhDdov4i8JtdFcLUAzIvfgrZjEIPsb
oqsSJq+EFEiu98+Vv0juSl2EkKMC71hixVHKdU11W8ifrDe+opa5jmRUMRDwxtLx
+Rp3PSiUemSV58axVadjJuTah9aKqsrmXa4Hz+w1WWyIF8sRioTM70QKQTbj7O7E
jcp3S2Wu2+YxozJmYgOJVBujVTlwrYdtYeGc2FGIJxvafzvWyoP8nsl727+XLiem
xv3qFImF2afAmKHIdpwIw9mhDYCLLNll5cziFLAhK3F9UKMdODWEHsMtqVTGvjTL
/DuLtoECgYEA1ybS0fZGsNab4KRpG7kPpW1wNQI1oHUvMzzUG8pp4LlnKZa+4Ho3
OipAE+RCMbsClCkFlqts1BfT6VFbZsntC/t2TkjjsbrQ6XJUrRPc/fwidl7aChcE
FYD9a4TZdOgKk7jfcyEufVriZmhBHJp2OUZAIoyHgKsUETLr/mzH1tUCgYEAxcJN
7B1fZ/LnccaWWThYk11zwn7KBBWMLXPzbOhfzWHF7Ydqb/ajZ1fVoH+/bziTIl8y
cvqDo39VskaN57NX01C8DIdzfEJdTu1lG/MPIHiPGntE8RcPi1CtbB5FVyIoN070
FMeOdNlCGO0arE7YOgAiyZH1w5H2UuPO478vZTkCgYAt82fBWhT8/cjq8JJWTm8O
CNKXL7KeY4jCK7KtgMyeJ1rmIgEAVnnnHVD0LqMIlgVV+XDtHg2vOquSwEKCMIxF
K963l4+xzNGDmlyFXqGrSSdfGqD82K+RnCwDw6rh8hEYPbrTjvmr4jZKYufNIRww
3VUjS9pA28j8Z2DJxRflRQKBgQCm6TJ/gOMPhzLVErm/IBGSf6O+mujCvbUMf/sL
Bq4lWMqHim3Jhi+wf6/swSXAJ833isW3ybzleAnKaEZJM1ODJXcyU/ii/hhnD3Lx
PhqcW2TdAwHTQpV6DmPxBzObMVckJ11XVH7mHKDvDOAgYoOZoJe77ZeyszVmDKSI
EMtd8QKBgQC7UEIKCuFLFPl4p8KLyqLkTVkQz/LicFh2KQEwr7CPbfWsyOKRREZ2
0Ji2r8zeyJuajJ9rHjgstubuDcOGG15gj2LmeiIynndhitld0Y/g7TkrhKcDPjzV
7PKFtmyPud6eH1Jf5Nn+02NkPl+DAH45IyaPAHgiUo2/SoGt5tX/YQ==
-----END RSA PRIVATE KEY-----
```




##User Management

###Create grader

- Created grader account : `sudo adduser grader`
- Resources used for this step.
  - [https://www.udacity.com/course/viewer#!/c-ud299-nd/l-4331066009/m-4801089468](https://www.udacity.com/course/viewer#!/c-ud299-nd/l-4331066009/m-4801089468)

###Set grader Admin

- Create the file grader in `/etc/sudoer.d/` with `nano /etc/sudoers.d/grader`
- Add the following text to the newly created file: `grader ALL=(ALL) ALL`
- Resources used for this step.
  - [https://www.udacity.com/course/viewer#!/c-ud299-nd/l-4331066009/m-4801089471](https://www.udacity.com/course/viewer#!/c-ud299-nd/l-4331066009/m-4801089471)

###Create SSH Keys

-  On local machine create SSH key with `ssh-keygen`
-  On the server create an .ssh direcory in `/home/grader/` with `mkdir .ssh`.
-  CD into the the directory just created with `cd ~/.ssh/`.
-  Create an authorized_keys file in the .ssh dirctory with `nano authorized_keys`.
-  Paste the public key into `/home/grader/.ssh/authorized_keys`.
-  Check to ensure you can log into the grader account with `ssh -i ~/.ssh/grader.rsa grader@52.26.72.67`.
-  Forcing Key Based Authentication, Edit sshd_config:`sudo nano /etc/ssh/sshd_config`, change line `PasswordAuthentication yes` to `PasswordAuthentication no`, Restarted ssh service: `sudo service ssh restart`
-  Resources used for this step.
   - [https://www.udacity.com/course/viewer#!/c-ud299-nd/l-4331066009/m-4801089477](https://www.udacity.com/course/viewer#!/c-ud299-nd/l-4331066009/m-4801089477)
   - [https://www.udacity.com/course/viewer#!/c-ud299-nd/l-4331066009/m-4801089481](https://www.udacity.com/course/viewer#!/c-ud299-nd/l-4331066009/m-4801089481)


### Update all currently installed packages
Updated all currently installed applications:
`sudo apt-get update`
`sudo apt-get upgrade`
### Configure the local timezone to UTC
Changed EC2 instance time zone to UTC:
`sudo dpkg-reconfigure tzdata`



### Configure the Uncomplicated Firewall (UFW)
- Check firewall status: `sudo ufw status`
- Denying incoming: `sudo ufw default deny incoming`
- Allowing outgoing: `sudo ufw default allow outgoing`
- Stabilising rules:
  - SSH (port 2200):  `sudo ufw allow 2200/tcp`
  - HTTP (port 80): `sudo ufw allow www`
  - NTP (port 123): `sudo ufw allow ntp`
  - Enabling firewall: `sudo ufw enable`








## Install PostgreSQL

### Install PostgreSQL

  `sudo apt-get install postgresql`

### Ensure remote connections are disabled.

  `sudo nano /etc/postgresql/9.3/main/pg_hba.conf`

The default configuration disables remote connections by default. Here is a cleaned up version of the section that controls connections.

| Type  | Database | User     | Address      | Method |
| ----- | -------- | -------- | ------------ | ------ |
| local | all      | postgres |              | peer   |
| local | all      | all      |              | peer   |
| host  | all      | all      | 127.0.0.1/32 | md5    |
| host  | all      | all      | ::1/128      | md5    |

  The host IPs point to local addresses by default.

### Create a new role named **catalog**:

- Create sql User catalog
  `sudo -u postgres`
  sql: 
  `CREATE USER catalog WITH CREATEDB;`
- Create system user **catalog**:
  `sudo adduser catalog`
- Login by catalog:
  `sudo su - catalog`
- create db, default name is same as the username 
  `createdb`
- login to postgresql:
  `psql`
- show user in sql:
  `SELECT current_user;`
- show db info in sql:
  `\conninfo`

- Resources used for this step.
  - [https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-14-04)
  - [https://www.digitalocean.com/community/tutorials/how-to-secure-postgresql-on-an-ubuntu-vps](https://www.digitalocean.com/community/tutorials/how-to-secure-postgresql-on-an-ubuntu-vps)
  - [https://www.digitalocean.com/community/tutorials/how-to-use-roles-and-manage-grant-permissions-in-postgresql-on-a-vps--2](https://www.digitalocean.com/community/tutorials/how-to-use-roles-and-manage-grant-permissions-in-postgresql-on-a-vps--2)
  - [http://www.postgresql.org/message-id/20040930142124.GA72856@winnie.fuhr.org](http://www.postgresql.org/message-id/20040930142124.GA72856@winnie.fuhr.org)




## Install application

###  Install and Enable apache2 and mod_wsgi
`sudo apt-get install apache2`
`sudo apt-get install libapache2-mod-wsgi`
To enable mod_wsgi: `sudo a2enmod wsgi`

### get app from git
 in dir `/var/www/`
 `sudo apt-get install git`
 `git clone https://github.com/chinaq/fullstack-nanodegree-vm.git`

### install Flask

- use *pip* to install *virtualenv* and *Flask*
   `sudo apt-get install python-pip`
   `sudo pip install virtualenv` 
- create a virtualenv instance venv in current path
   `sudo virtualenv venv`
- use venv
   `source venv/bin/activate` 
   `sudo pip install Flask`
   `sudo python /var/www/fullstack-nanodegree-vm/catalog/project.py`
- exit venv
   `deactivate`



### Configure and Enable a New Virtual Host

- edit **catalog.conf**


```
sudo nano /etc/apache2/sites-available/catalog.conf
```

```
<VirtualHost *:80>
                ServerName ec2-52-26-72-67.us-west-2.compute.amazonaws.com
                ServerAdmin admin@ec2-52-26-72-67.us-west-2.compute.amazonaws.com
                WSGIScriptAlias / /var/www/fullstack-nanodegree-vm/vagrant/catalog/catalog.wsgi
                <Directory /var/www/fullstack-nanodegree-vm/vagrant/catalog/>
                        Order allow,deny
                        Allow from all
                </Directory>
                Alias /static /var/www/fullstack-nanodegree-vm/vagrant/catalog/static
                <Directory /var/www/fullstack-nanodegree-vm/vagrant/catalog/static/>
                        Order allow,deny
                        Allow from all
                </Directory>
                ErrorLog ${APACHE_LOG_DIR}/error.log
                LogLevel warn
                CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
- Enable the virtual host 

```
sudo a2ensite catalog
```



### Create the .wsgi File

- edit **catalog.wsgi**

```
cd /var/www/fullstack-nanodegree-vm/vagrant/catalog/
sudo nano catalog.wsgi 
```


```
#!/usr/bin/python
import sys
import logging
logging.basicConfig(stream=sys.stderr)
sys.path.insert(0,"/var/www/fullstack-nanodegree-vm/vagrant/catalog/")

from project import app as application
application.secret_key = 'super_secret_key'
```



### Restart Apache

```
sudo apache2ctl restart 
```





### Problems

- absolute path with .db and .json
```
CLIENT_ID = json.loads(open('/var/www/fullstack-nanodegree-vm/vagrant/catalog/client_secrets.json', 'r').XXXXXXXXXX

#Connect to Database and create database session
engine = create_engine('sqlite:////var/www/fullstack-nanodegree-vm/vagrant/catalog/restaurantmenuwithusers.db')`
```

- using one session on different thread in sqlchemy
```
Base.metadata.bind = engine
DBSession = sessionmaker(bind=engine)
session = scoped_session(DBSession)

@app.teardown_request
def remove_session(ex=None):
    session.remove()
```


- Resources used for this step.

https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps
https://www.digitalocean.com/community/tutorials/how-to-run-django-with-mod_wsgi-and-apache-with-a-virtualenv-python-environment-on-a-debian-vps
https://discussions.udacity.com/t/apache-server-mod-wsgi-deploy-error/19106/4



