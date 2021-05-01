# Amarillo

## NB

Development on this application is not yet complete, and `amarillo` should not be used in a production environment at this time.

## Overview

Amarillo is a Ruby applications written to automation issuing Let's Encrypt certificates using dns-01 challenges through AWS Route 53.

## Quickstart

Amarillo is distributed as a RubyGem and can be installed with:

```
gem install amarillo
```

`amarillo` requires the use of OpenSSL libraries and you may need to install with supplying the location of the OpenSSL headers.

macOS:
```
gem install amarillo -- --with-openssl-dir=/opt/homebrew/Cellar/openssl@1.1/1.1.1k
```

Debian/Ubuntu:
```
```

Usage:  `amarillo --zone ZONE --name COMMONNAME --email EMAIL`

For example:

```
amarillo --zone iachieved.it --name zabbix.operations.iachieved.it --email noreply@iachieved.it
```

## Why?

It's always bothered me that there is an entire industry around making money issuing SSL certificates.  Sure, I understand that OV and EV certificates verify that there's an actual organization behind the certificate and that they are legitimate.  But DV (domain validation) certificates still cost money, and all that's validated is you control a domain or an e-mail address.  Unless you're running a bank...

Enter Let's Encrypt...

Unfortunately there a many of us who want _secure_ communications between services and websites inside a corporate or private network.  Let's Encrypt's out-of-the-box `certbot` assumes that the website is on the public Internet.

## Configuration

To use `amarillo` you'll need to provide AWS credentials in an `aws.env` file located in `/etc/amarillo/aws.env` or `/usr/local/etc/amarillo/`.  These credentials should be that of an AWS IAM user that only has programmatic access to Route 53 with the `AmazonRoute53FullAccess` policy.

The format of the `aws.env` file is:

```
[default]
aws_access_key_id=
aws_secret_access_key=
```

You'll also want to have:

* an E-mail address
* Zone
* Server Name

## Output

By default `amarillo` wants to leave files in `/etc/ssl/amarillo` and will try to create this directory. 

## Renewals

Let's Encrypt certificates expire 90 days after issuance.

# For Developers

On macOS, without `rvm`

```
sudo gem install bundler
bundle install
```

```
sudo -s ruby -Ilib ./bin/amarillo --zone iachieved.it --name test.iachieved.it --email joe@iachieved.it
```


# Amarillo

Pronounced "ah-ma-ree-show" in honor of mis amigos uruagayos.  🇺🇾🇺🇸
