# SL(A)EMP

SL(A)EMP stands for Secure L(A)EMP.
It will install all necessary binaries for a secure LAMP or LEMP server automatically. Supported are the latest versions of Debian (Stretch) and CentOS (7.x).

## Features

- Setup a secure webserver config
  - Using the strong cipherlist from https://cipherli.st
- nginx OR Apache Support (HTTP2 is not supported by Apache on CentOS)
- Secure your host with a Let's Encrypt certificate
- Subdomain support
- Domain Redirects and Alias support
- Multiple PHP versions (7.1, 7.2, 7.3) running as FPM service
- MariaDB databases with random generated passwords
- Install Nextcloud or Wordpress with an optimized configuration for Apache and Nginx
- Redis support (optional, but recommended if you are using Nextcloud)
- Fail2ban support (optional)
- UFW (uncomplicated firewall) support (Debian only, optional)

## Requirements

- OS: Debian 9 (Stretch) or CentOS 7.x, clean install!

## Installation
Important: SL(A)EMP makes use of various open-source software.
Please assure you agree with their license before using it. Any part of SL(A)EMP itself is released under GNU General Public License, Version 3.

```
yum install git -y
git clone https://github.com/cunninghambr/SLEMP SLEMP
cd SLEMP
chmod +x installer.sh add_domain.sh
./installer.sh
```
The setup script will add the following repositories, dependent on your OS:

- NGINX (original repository by the nginx developers)
- PHP
  - Debian: DEB.SURY.ORG https://deb.sury.org/
  - CentOS: Remi's RPM repository (https://rpms.remirepo.net)
- MariaDB (original repository by the MariaDB developers)

After the installer is finished, CentOS user have to restart there system, because SELinux will be disabled during the installation.
Also save your MySQL root password on a secure place! You will see the password at the end of the installation.

If something goes wrong there is an installer log available at /tmp/slemp_install.txt

## Usage
```
./add_domain.sh
```

The script will guide you through the setup.
Be sure to point your domain to the IP of your server (www and non-www dns record)

You will find the config and files at the following paths:

#### Apache
CentOS: /etc/httpd/conf.d/
Debian: /etc/apache2/sites-enabled/

#### nginx
- /etc/nginx/conf.d/

#### PHP
- CentOS: /etc/opt/remi/php7x/php-fpm.d/
- Debian: /etc/php/7.x/fpm/pool.d/

#### Web
- /var/www/YOUR-DOMAIN/

### How I upload files?

- Set a password to your location user
- Connect over SCP with your server (Windows: WinSCP, macOS: Transmit)

## What's next
- Cleanup the script
- Option to anonymize IPs
- Advices to secure the server in general
