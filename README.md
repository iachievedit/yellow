# Yellow

An Ruby script to issue Let's Encrypt certificates with dns-01 challenges through AWS Route 53.

**NB**:  This documentation is not yet complete!

## Quickstart

Usage:  `yellow --zone ZONE --name COMMONNAME --email EMAIL`

For example:

## Why?

It's always bothered me that there is an entire industry around making money issuing SSL certificates.  Sure, I understand that OV and EV certificates verify that there's an actual organization behind the certificate and that they are legitimate.  But DV (domain validation) certificates still cost money, and all that's validated is you control a domain or an e-mail address.  Unless you're running a bank...

Enter Let's Encrypt...

Unfortunately there a many of us who want _secure_ communications between services and websites inside a corporate or private network.  Let's Encrypt's out-of-the-box `certbot` assumes that the website is on the public Internet.

## Configuration

To use `yellow` you'll need to provide AWS credentials in `aws.env`.  You'll also want to have:

* an E-mail address
* Zone
* Server Name

## Output

By default `yellow` wants to leave files in `/etc/ssl/`.

# For Developers

On macOS, without `rvm`

```
sudo gem install bundler
bundle install
```