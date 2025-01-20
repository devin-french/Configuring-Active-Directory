<h1>Installing Active Directory within Azure</h1>
This lab shows how I installed Active Directory on a VM in Azure, which will serve as the domain controller. The second VM, on the same VNet, will be used as a client in a future lab. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (21H2)

<h2>Installation Steps</h2>
<img width="1280" alt="Screenshot 2025-01-18 at 12 57 28 AM" src="https://github.com/user-attachments/assets/4d36063c-d007-498c-a538-03936bbaeba7" />

Set the domain controller VM’s IP to static to ensure proper communication with the client VM. In the Azure portal, go to the Networking tab, select the Network Interface, and set the IP Assignment to Static. This ensures the domain controller has a fixed IP for future configurations.


<img width="1280" alt="Screenshot 2025-01-18 at 1 35 32 AM" src="https://github.com/user-attachments/assets/6e71d1dc-84d9-4be8-8414-af70618ec437" />

<img width="1280" alt="Screenshot 2025-01-18 at 1 36 26 AM" src="https://github.com/user-attachments/assets/9cfa5dfe-ac57-4cf4-b54b-001216f0d19a" />

<img width="1280" alt="Screenshot 2025-01-18 at 1 37 15 AM" src="https://github.com/user-attachments/assets/e79879f0-bb94-4928-915d-70e5544a3863" />


After setting the static IP, log into the client VM and ping the domain controller’s private IP. If it times out, enable ICMPv4 on the domain controller by opening wf.msc, going to Inbound Rules, and click on the "Domain Profile, Private Profile, and Public Profile" tabs on the top and make sure to turn the firewall state to off for all of them. The ping from the client VM should now succeed.


<img width="1280" alt="Screenshot 2025-01-19 at 3 53 17 PM" src="https://github.com/user-attachments/assets/052473e8-1f72-437b-9eea-b1df77445b0a" />
<img width="1280" alt="Screenshot 2025-01-19 at 3 56 36 PM" src="https://github.com/user-attachments/assets/0d8d0d67-f757-493e-b6f2-4129775507e0" />

In Server Manager, click "Add Roles and Features," select "Active Directory Domain Services," and install. Afterward, click the warning flag, select "Promote this server to a domain controller," choose "Add a new forest," set the domain name (yourdomain.com) and password, then complete the installation.
