# Install VMs
- Installed Windows Server 2022 as a Virtual machine in VMware Workstation
- Installed Windows 11 as a Virtual machine in VMware Workstation

# Management Client & PS Remoting
- Create XYZ DC & Management workstation 
- Use management workstation to control XYZ DC via PS Remoting
- First enable-psremoting on XYZ DC
- Start-Service WinRM service on management workstation 
- Configure New-PSSession on management workstation to connect to XYZ DC
- Set-Item WSMan:\localhost\Client\TrustedHosts -Value 192.168.29.134
- For connecting 
- New-PSSession -ComputerName 192.168.29.134 -Credential (Get-Credential)
- Enter-PSSession 2

# Setup AD on Domain controller 
- Now On XYZ DC1 change the host name and set static ip to it
- Again Modify Trusted Host for static ip of xyz dc1
- Set DNS Server as xyz dc1 itself
- Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
- Import-Module ADDSDeployment
- Install-ADDSForest
- Configure values
- You have to change dns again because while installtion of adds it automaticlly loop addreess of dns
- Change via sconfig dns option on xyz dc or via following command
- Get-DNSClientServerAddress
- Set-DNSClientServerAddress -InterfaceIndex 4 -ServerAddresses 192.168.29.155

# Workstation
- Create ws01 
- Change dns of ws01 to dc1
- On ws01 join the domain xyz.com
- Add-Computer -DomainName xyz.com -Credential xyz\Administrator -Force -Restart

# Copy Item from mangement client to dc via Ps Remoting
- $dc = New-PSSession -ComputerName 192.168.29.155 -Credential (Get-Credential)
- Copy-Item .\README.md -ToSession $dc C:\Windows\Tasks
