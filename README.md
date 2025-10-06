# Active-Directory-via-PowerShell
*Project done back in 2022. Providing documentation*
Project done from watching this video: https://youtu.be/MHsI8hJmggI?si=uCmsgk7di5o59Ggq

Active Directory is a management system in which administrators can configure and administer user accounts and permissions for access to different groups and resources. Being able to configure the right permissions based off principle of least privilege and a few other factors help out with keeping things in check in terms of access and configurations in the organization. 

For this lab, you will need to download several resources for this activity. You will need to get the PowerShell script from Josh Madakor's project for this, a Windows 10 iso, and a Windows Server 2019 iso for this lab to work.  
Windows 10: https://www.microsoft.com/en-us/software-download/windows10  
Windows Server 2019: https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019  
PowerShell script: https://github.com/joshmadakor1/AD_PS   

When downloading the Windows 10 iso, it will first instead download a Media Creation tool for it. Go through the steps needed to get the Windows 10 iso and wait for it to be created, after which you will have the Windows 10 iso to work with. 

First create the DC/Windows Server VM:  
128 MB of Video Memory  
Base Memory: 4048 MB  
Adaptar 1: NAT  
Adapter 2: Internal network  
Processors: 2-4  
ISO: Windows Server.iso  

After startup:  
<img width="1027" height="773" alt="image" src="https://github.com/user-attachments/assets/9f67797e-a38d-4d4e-93ce-c28e3e1690b7" />  




