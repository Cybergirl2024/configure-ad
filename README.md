<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/a0lpTlR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The first step I took was to create two virtual machines, one for the domain controller and one as a client to connect to the DC. Also they must be on the same vnet in order for this process to work.
</p>
<br />

<p>
<img src="https://i.imgur.com/ykw1CEX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The next step was to make the DC virtual machine's NIC ip addresss to static.
</p>
<br />

<p>
<img src="https://i.imgur.com/k0PgZRZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I log into Client-1's vm to command a perpetual ping to DC-1's vm but as you can see it is timed out. In the next step I will enable ICMPv4 protocols on DC-1's virtual machine through Firewall.
</p>
<br />

<p>
<img src="https://i.imgur.com/nnjh3In.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I enabled all of the ICMPv4 protocols on DC 1's virtual machine through Windows Firewall so now when I go back to Client 1's virtual machine the connectivity should be allowed.
</p>
<br />

<p>
<img src="https://i.imgur.com/wySClzo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now Client 1 is able to ping DC 1's virtual machine as you can see.
</p>
<br />

<p>
<img src="https://i.imgur.com/ij2Y8Nv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The next step was to install Active Directory through server manager on DC 1's virtual machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/r3QhcHw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The last step to fully download Active Directory was to promote the server to a domain controller. I did that and also created a new forest called mydomain.com.This is the new domain name I am going to log in as to access the Domain Controller.
</p>
<br />

<p>
<img src="https://i.imgur.com/aLfUQFE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I am going to login in as the domain name I created in the last step.
</p>
<br />

<p>
<img src="https://i.imgur.com/wmnmKe3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I logged into the domain controller. The next step was to create a new organizational unit called _EMPLOYEES.
</p>
<br />

<p>
<img src="https://i.imgur.com/kQPeIKS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I also created a another organizational unit called _ADMINS.
</p>
<br />

<p>
<img src="https://i.imgur.com/9YbxxOO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The next step was to create an admin user named Jane Doe and assign her to the Security group Domain Admins. So for now on I will be signing in as jane doe.
</p>
<br />

<p>
<img src="https://i.imgur.com/rgWbFNf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I am now signed in as Jane doe on the Domain Controller VM.
</p>
<br />

<p>
<img src="https://i.imgur.com/Wp3JZRU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The next step that I did was connect Client 1 to DC 1's DNS servers through azure.
</p>
<br />

<p>
<img src="https://i.imgur.com/Tq2vLB2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I restarted the Client 1's VM and connected it to the domain. Then I restarted the machine all over again.
</p>
<br />

<p>
<img src="https://i.imgur.com/wSRmzLL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The next step was to log into DC 1's VM to see if Client 1 is connected to Active Directory which it is because the name of the VM is labuser.
</p>
<br />

<p>
<img src="https://i.imgur.com/bbk2pks.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The next thing I did was create 10000 users that I can use to log into Client 1 VM. For this I used another persons code and paste it into powershell ise.
</p>
<br />

<p>
<img src="https://i.imgur.com/YPX8ypq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The last step was to login as one of the random users on the Client 1 VM. 
</p>
<br />






