# filemaker-logwatch
Logwatch configuration files for FileMaker servers

## Installing with MacPorts

```Shell
sudo port install logwatch
```
## Installing from Source on Mac OS

* download the current tar.gz file from http://sourceforge.net/projects/logwatch/files/
* untar files (double-click in Finder)
* cd into logwatch folder
```Shell
sudo -s
chmod +x install_logwatch.sh
./install_logwatch.sh
use the default paths at prompts
cp -r conf/* /etc/logwatch/conf/
cp -r scripts/services/* /etc/logwatch/scripts/services/
```
## Configuring Logwatch
```Shell
nano /etc/logwatch/conf/logwatch.conf
```
```Shell
MailTo = logwatch@somedomain.com
MailFrom = YourServerHostname@somedomain.com
```
* in /usr/sbin/logwatch around line 88, change zcat to gzcat
* create a file at /etc/periodic/daily/980.run-logwatch with the following lines:
```Shell
echo "Sending logwatch report to logwatch@somedomain.com" 
/opt/local/bin/logwatch --mailto logwatch@somedomain.com
```
