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
Click next and click install now:  
<img width="1023" height="770" alt="image" src="https://github.com/user-attachments/assets/bae76fb5-9479-49bf-9e61-695cf17b801c" />  
After clicking, choose the second option from the operating system list:  
<img width="1025" height="772" alt="image" src="https://github.com/user-attachments/assets/f778a429-cd21-49fa-8be4-13614ab603e3" />  
After going through the license agreement, chose create custom and choose drive zero for installation:  
<img width="1026" height="771" alt="image" src="https://github.com/user-attachments/assets/b31b307b-c85a-486c-ba40-ad01bd4fe6a5" />  
Click next, then wait since it will take a while and don't click anything.  
<img width="1028" height="776" alt="image" src="https://github.com/user-attachments/assets/ce7cf541-af80-4155-9951-a91f09fc7e70" />  

After waiting, you will be greeted by a customize settings screen with asking for a password to be set. Create a simple password and hit finish  
Then you be taken to the sign in screen. Look up the top of the VM, click input, then keyboard, and then click insert control, alt, delete and will be taken to the sign screen and type in the password set.  
<img width="1024" height="772" alt="image" src="https://github.com/user-attachments/assets/34b87a32-70f9-49f3-a3c1-e12cd458fddc" />  

Next click on the folder, then This PC, and you will see the VirtualBox Guest Additions and click on it:  
<img width="1020" height="771" alt="image" src="https://github.com/user-attachments/assets/40759515-a8bd-438a-b446-420ec86f08c1" />  
And then click on the amd64 application: 
<img width="1024" height="772" alt="image" src="https://github.com/user-attachments/assets/fe09d0f2-30ac-4299-9149-28627f040d31" />  
And click next and install on everything, then go and click on shutdown to close out the VM to install properly.  
After signing back in, go to the network icon and click on unidentified network, scroll down and click on change adapter options and a screen will pop up next to it:  
<img width="1295" height="445" alt="image" src="https://github.com/user-attachments/assets/4eedcec1-76fd-4b76-8c64-00c008a8b632" />  
Check out both ethernet connections, the home network one will be the one with IP address of 10.0. and son on. The internal network one will be something like 255.255.0.0  
Rename the both ethernets to Internet and Internal Network Respectively, then assign the IP address to the second one later.  
Next go rename the PC, by going to the start menu, clicking on system, and scrolling down till you see rename this PC to DC and click restart now and wait.  
Then go and assign the IP address for internal network like this:  
<img width="443" height="557" alt="image" src="https://github.com/user-attachments/assets/8de62c5a-7134-460e-9c00-d8c111f9f7ae" />  

Next go to the Server Manager and click on add roles and features, click on next till you get to server roles and check on Active Directory Domain Services and continue clicking on next and click on install.  
Then wait on it too install which takes a few minutes.  
After finishing, you will then want to clock the yellow sign on the flag:  
<img width="352" height="318" alt="image" src="https://github.com/user-attachments/assets/6f65e9b4-8974-461a-ba1b-1fb3fae0b77a" />  
Click on promote, then in deployment configuration, click on add a new forest and name it whatever you want, such as mydomain.com. Then click next, type password you set, and click next until you see click install which takes a while.  
The VM will then restart and will be greeted with this screen:  
<img width="923" height="622" alt="image" src="https://github.com/user-attachments/assets/a25465f3-a248-4b53-b3f0-6700b64194e5" />  
Sign in and go to the start menu, click on the Windows Administrative Tools dropdown and click on Active Directory Users and Computers and you will be greeted by this:  
<img width="759" height="526" alt="image" src="https://github.com/user-attachments/assets/0f945e8d-5583-4557-9c04-437d587b9e34" />  
Click on mydomain.com and go down to new, and then go down to Organizational Unit, click on it and name the new object _ADMINS and uncheck protect container
Then click on _ADMIN and click on create new user and be greeted by this prompt:  
<img width="785" height="536" alt="image" src="https://github.com/user-attachments/assets/856f37ba-f997-4324-826d-1d616972fe3d" />  
Enter in your first and last name along with a login name such as first-initial and then last name. Click next and enter a password to keep up with. Uncheck must change password at next logon and check password never expires.  
Click next and click finish.  
You will then be greeted by this screen, click on the user account and go to properties to change it to admin account:  
<img width="563" height="401" alt="image" src="https://github.com/user-attachments/assets/5d13c7f5-c164-4ad3-9254-89d2c0891946" />  
After clicking on properties you be taken to this page:  
<img width="420" height="546" alt="image" src="https://github.com/user-attachments/assets/fba6f618-dc60-4802-ab47-c6663875ce1a" />  
Go to Member of tab and click on the add button. In the enter objects to select pane, type domain admins and then click ok.  
To use the admin account, sign out and sign in to the new admin account.  
You will see this screen with other user and then click on it:  
<img width="1790" height="965" alt="image" src="https://github.com/user-attachments/assets/d8a28dee-fa30-4cca-bdeb-2a956c5f66cc" />  
Now sign in and go to server manager and click on add roles and features. Click on next until server roles and click on remote access. On the role services screen click on routing and and click on add features. Click on next and then on install and then wait a while for it too install.  
Then on server manager click on tools and go to routing and remote access:  
<img width="621" height="436" alt="image" src="https://github.com/user-attachments/assets/8d9172db-aa87-42ee-bae0-74f64674d24d" />  
Then click on DC (local) and then click on configure and enable. Click next and change configuration from remote to NAT. On NAT Internet Connection clock on internal, then next and finish. To see if it worked, click on the drop down menu for DC:  
<img width="620" height="438" alt="image" src="https://github.com/user-attachments/assets/08f10286-4ab7-4b28-8ca4-98ad159a2ab6" />  
For DHCP, click on add roles and features and click on next till server roles and click on DHCP Server. Click on next until clicking on install and then wait a few minutes.  
Then go to tools and click on DHCP and be greeted by this window:  
<img width="584" height="405" alt="image" src="https://github.com/user-attachments/assets/343c9d34-6864-4995-9fdc-6185c06894d6" />  
Click on the dropdown menu and you will see that IPv4 and IPv6 are both down. Click on IPv4 and click on new scope and name it 172.168.100-200 and click next and for address range:   
<img width="634" height="450" alt="image" src="https://github.com/user-attachments/assets/0bf610,af-4000-4b4a-9f5c-df717e40058d" />  
Click next until router and add 172.16



















