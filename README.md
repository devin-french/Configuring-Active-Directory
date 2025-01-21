<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Installing Active Directory in Azure</h1>
This lab shows how I installed Active Directory on a VM in Azure, which will serve as the domain controller. The second VM, on the same VNet, will be used as a client in a future lab.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (21H2)

<h2>Installation Steps</h2>
<img width="1280" alt="Screenshot 2024-12-27 at 4 38 37 PM" src="https://github.com/user-attachments/assets/6d99877b-13ef-4a59-9ca6-d1e6446df49b" />

Set the domain controller VM’s IP to static to ensure proper communication with the client VM. In the Azure portal, go to the Networking tab, select the Network Interface, and set the IP Assignment to Static. This ensures the domain controller has a fixed IP for future configurations.


<img width="1280" alt="Screenshot 2025-01-18 at 1 35 32 AM" src="https://github.com/user-attachments/assets/3de77c1a-4afb-4445-a3d2-aa6ae3d37d97" />
<img width="1280" alt="Screenshot 2025-01-18 at 1 36 26 AM" src="https://github.com/user-attachments/assets/81b9a9a0-d330-48b3-8efd-df8b7d177956" />
<img width="1280" alt="Screenshot 2025-01-18 at 1 37 15 AM" src="https://github.com/user-attachments/assets/5e78a7e5-2771-4984-8ff6-158177fbe801" />

After setting the static IP, log into the client VM and ping the domain controller’s private IP. If it times out, enable ICMPv4 on the domain controller by opening wf.msc, going to Inbound Rules, and click on the "Domain Profile, Private Profile, and Public Profile" tabs on the top and make sure to turn the firewall state to off for all of them. The ping from the client VM should now succeed.


<img width="1280" alt="Screenshot 2025-01-19 at 3 53 17 PM" src="https://github.com/user-attachments/assets/7a3d221f-b3b1-4dae-8e18-162fd3a28384" />
<img width="1280" alt="Screenshot 2025-01-21 at 2 37 52 AM" src="https://github.com/user-attachments/assets/2c9515ce-a7ab-41b6-a27d-9e9e936c7e57" />

In Server Manager, click "Add Roles and Features," select "Active Directory Domain Services," and install. Afterward, click the warning flag, select "Promote this server to a domain controller," choose "Add a new forest," set the domain name (e.g., ernestotest.com) and password, then complete the installation.
