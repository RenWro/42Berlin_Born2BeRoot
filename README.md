# Table of Contents

1. [About the project](#about-the-project)
2. [General questions related to the project](#general-questions-related-to-the-project)
    1. [How does a virtual machine work ? And what its purpose?](#how-does-a-virtual-machine-work-and-what-its-purpose)
    2. [Why did I choose Debian?](#why-did-i-choose-debian)
    3. [What's the difference between Debian and Rocky?](#whats-the-difference-between-debian-and-rocky)
    4. [What's the difference between aptitude, apt and what's APPArmor ?](#whats-the-difference-between-aptitude-apt-and-whats-apparmor)
    5. [What the advantages of a strong password policy? How's its implementation?](#what-the-advantages-of-a-strong-password-policy-hows-its-implementation)
    6. [What's a partition ? And more generally how does LVM (Logical Volume Management) work ?](#whats-a-partition-and-more-generally-how-does-lvm-logical-volume-management-work)
    7. [What's the hostname of the machine and how to change it?](#whats-the-hostname-of-the-machine-and-how-to-change-it)
    8. [How do you check for partitions?](#how-do-you-check-for-partitions)
    9. [What's sudo ?](#whats-sudo)
    10. [What's an UFW and what's the value of using it? How to add new rules?](#whats-an-ufw-and-whats-the-value-of-using-it-how-to-add-new-rules)
    11. [What's SSH (Secure Shell) and what's the value of using it? How do you check it?](#whats-ssh-secure-shell-and-whats-the-value-of-using-it-how-do-you-check-it)
    12. [How does the script works and what is cron?](#how-does-the-script-works-and-what-is-cron)
    13. [Monitoring](#monitoring)
3. [What's in this repo?](#whats-in-this-repo)
4. [References](#references)

---

# About the project
The project aims to install Debian virtual machine.

![Born2Be](https://github.com/user-attachments/assets/f95de2dd-df3e-4e0f-9b5d-073eee581a06)

---

# General questions related to the project

### How does a virtual machine work ? And what its purpose?
According to RedHat, a virtual machine (VM) is a computing environment that functions as an isolated system with its own CPU, memory, network interface, and storage, created from a pool of hardware resources. Software called a hypervisor isolates the necessary computing resources and enables the creation and management of VMs.<br>

The physical machine that runs the VMs is called the host machine, host computer, host operating system, or simply host. The many VMs that use its resources are guest machines, guest computers, guest operating systems, or simply guests. The hypervisor treats compute resources—like CPU, memory, and storage—as a pool of resources that can easily be relocated between existing guests or to new virtual machines.<br>

VMs allow multiple different operating systems to run simultaneously on a single computer—like running a Linux® distribution on a MacOS or Windows system. Each operating system runs in the same way an operating system or application normally would on the host hardware, so the end user experience emulated within the VM is nearly identical to a real-time operating system experience running on a physical machine. <br>

### Why did I choose Debian?
Debian is excellent for those who want a versatile, stable, and free operating system for various use cases, from home labs to enterprise setups. It's very known and largely used. Rocky Linux is the go-to choice for organizations seeking a RHEL-compatible, stable, long-term support system, particularly after the shift in CentOS's direction, less common but still interesting.

### What's the difference between Debian and Rocky?

#### Debian


<ul>
<li>Overview: Debian is one of the oldest and most popular Linux distributions, known for its stability and reliability. It is a community-driven distribution that focuses on free software, and it has a massive package repository.</li>
<li>Package Management: Debian uses the .deb package format, and it relies on the APT package management system.</li>
<li>Release Cycle: Debian follows a "frozen" release cycle, with new stable versions being released approximately every two years. It is known for being a bit slower to release new software in favor of stability.</li>
<li>Target Users: Debian is widely used by both developers and system administrators who need a stable, versatile, and free OS. It is commonly used in servers, workstations, and even desktops by advanced users.</li>
<li>Community Support: As a community-driven project, Debian has a large and active user base, which means there are plenty of forums, mailing lists, and resources available.</li>
</ul>

#### Rocky
<ul>
<li>Overview: Rocky Linux is a relatively new distribution, created as a community-driven replacement for CentOS after Red Hat shifted CentOS to CentOS Stream. It is designed to be binary-compatible with Red Hat Enterprise Linux (RHEL).</li>
<li>Package Management: Rocky Linux uses the .rpm package format, and it relies on the YUM or DNF package management systems.</li>
<li>Release Cycle: Rocky Linux follows RHEL’s release cycle, with long-term support (LTS) releases typically coming every 3 to 4 years. Updates and security patches are provided for a long time.</li>
<li>Target Users: Rocky Linux is primarily used in enterprise environments that require stability, long-term support, and compatibility with RHEL. It’s perfect for businesses and organizations that were previously using CentOS or RHEL.</li>
<li>Community Support: Rocky Linux is a community-driven project that is backed by various contributors, and it has extensive support through forums, documentation, and mailing lists.</li>
</ul>
<h3>What's the difference between aptitude, apt and what's APPArmor ?</h3>

#### AppArmor provides Mandatory Access Control (MAC) security. 
In fact, AppArmor allows the system administrator to restrict the actions that processes can perform. For example, if an installed application can take photos by accessing the camera application, but the administrator denies this privilege, the application will not be able to access the camera application. If a vulnerability occurs (some of the restricted tasks are performed), AppArmor blocks the application so that the damage does not spread to the rest of the system.
In AppArmor, processes are restricted by profiles. Profiles can work in complain-mode and in enforce-mode. In enforce mode, AppArmor prohibits applications from performing restricted tasks. In complain-mode, AppArmor allows applications to do these tasks, but creates a registry entry to display the complaint.

#### And what is the difference between Apt and Aptitute?
In Debian-based OS distributions, the default package manager we can use is dpkg. This tool allows us to install, remove and manage programs on our operating system. However, in most cases, these programs come with a list of dependencies that must be installed for the main program to function properly. One option is to manually install these dependencies. However, APT (Advanced Package Tool), which is a tool that uses dpkg, can be used to install all the necessary dependencies when installing a program. So now we can install a useful program with a single command.
APT can work with different back-ends and fron-ends to make use of its services. One of them is apt-get, which allows us to install and remove packages. Along with apt-get, there are also many tools like apt-cache to manage programs. In this case, apt-get and apt-cache are used by apt. Thanks to apt we can install .deb programs easily and without worrying about dependencies. But in case we want to use a graphical interface, we will have to use aptitude. Aptitude also does better control of dependencies, allowing the user to choose between different dependencies when installing a program.


### <h3>What the advantages of a strong password policy? How's its implementation?</h3>


A password policy is a set of guidelines and rules that define how passwords should be created, used, and protected in an organization’s network or web application. The policy may include requirements for password length, complexity, and expiration, as well as guidelines for protecting passwords from unauthorized access or disclosure. A password policy is intended to help ensure the security of an organization’s digital assets by reducing the risk of password-related attacks, such as brute-force attacks or password cracking. It is typically enforced through security software or by administrative procedures, and users are expected to comply with the policy in order to access the organization’s resources. By implementing a password policy, you can establish clear guidelines for users to follow when creating and utilizing passwords on your web application. 

The password expiration helps to ensure the ongoing security of an organization’s digital assets by requiring users to periodically update their passwords. This helps to mitigate the risk of password-related attacks, such as brute-force attacks or password cracking, by limiting the window of time that an attacker has to use a stolen password. When passwords are set to expire after a certain period, it encourages users to create new, stronger passwords more frequently, which further enhances the security of the system. It also reduces the risk of a forgotten or compromised password going undetected for an extended period of time, since the user will be prompted to change it on a regular basis. 

One of the most effective ways of establishing a strong password policy is to enforce a level of password complexity. Requirements might include the password meeting a predetermined number of characters in length including digits, uppercase and lowercase letters, and special characters.Although you can’t fully control their behavior, it enables you to provide guidance for their safety and security.


1. Prevent Data Breaches

Ensuring the security of your business data and customers’ personal information is of utmost importance. Any vulnerability in your network can potentially lead to data breaches, which can have severe consequences on your reputation, finances, and legal obligations. Attackers can exploit even the slightest vulnerability to initiate a breach, leaving you exposed to professional, financial, and legal ramifications. By implementing a strong password policy, your business can make it more difficult for cyber criminals to gain access to its confidential data.

2. User protection

Password policies help protect users from themselves by requiring them to create strong passwords and change them regularly. This reduces the risk of their accounts being compromised due to weak passwords or password reuse.

3. Build Trust

Concerns about cyber attacks have made many online users hesitant to share their personal information on websites. However, seeing a password policy on a website can provide them with a sense of reassurance, as it indicates that the website owners prioritize cyber-security. By implementing a consistent password policy across the network, users can feel confident that their personal information is being safeguarded.

4. Helps to maintain accountability

password policies help organizations maintain accountability. By tracking and auditing user activity, organizations can identify potential security breaches and take appropriate action. This can help prevent data breaches and ensure that users are following security policies.

5. Foster a Culture of Cybersecurity

While implementing strong cybersecurity measures can seem intimidating, the most challenging aspect is often addressed when your team or users are educated on how to protect themselves. The majority of cyberattacks occur due to human-created vulnerabilities. By educating the users of your network on cyber threats and how to prevent them, you can significantly reduce the risk of successful attacks. This empowers your network to be more resilient and less vulnerable to intrusions by malicious actors.


<h3>What's a partition ? And more generally how does LVM (Logical Volume Management) work ?</h3>


LVM (Logical Volume Manager) is an abstraction layer between a storage device and a file system. We get many advantages from using LVM, but the main advantage is that we have much more flexibility when it comes to managing partitions. Suppose we create four partitions on our storage disk. If for any reason we need to expand the storage of the first three partitions, we will not be able to because there is no space available next to them. In case we want to extend the last partition, we will always have the limit imposed by the disk. In other words, we will not be able to manipulate partitions in a friendly way. Thanks to LVM, all these problems are solved.
By using LVM, we can expand the storage of any partition (now known as a logical volume) whenever we want without worrying about the contiguous space available on each logical volume. We can do this with available storage located on different physical disks (which we cannot do with traditional partitions). We can also move different logical volumes between physical devices. Of course, services and processes will work the same way they always have. But to understand all this, we have to know:

<ul>
<li>Physical Volume (PV): physical storage device. It can be a hard disk, an SD card, a floppy disk, etc. This device provides us with storage available to use.</li>
<li>Volume Group (VG): to use the space provided by a PV, it must be allocated in a volume group. It is like a virtual storage disk that will be used by logical volumes. VGs can grow over time by adding new VPs.</li>
<li>Logical volume (LV): these devices will be the ones we will use to create file systems, swaps, virtual machines, etc. If the VG is the storage disk, the LV are the partitions that are made on this disk.</li>
</ul>

<h3>What's the hostname of the machine and how to change it?</h3>

<h3>How do you check for partitions?</h3>

<h3>What's sudo ?</h3>
Sudo is a command-line utility for Unix and Unix-based operating systems such as Linux and macOS . The utility provides an efficient way to grant users or groups of users temporary privileged access to system resources so that they can execute commands that they cannot run using their normal accounts. Users can even be granted permission to execute commands under the root account—the account with the highest privileges on Unix systems. Sudo also logs all commands and arguments so that administrators can track sudo users' behavior.

Many sources say that sudo stands for superuser do , which used to be true. However, the group that developed sudo stopped using that name more than a decade ago. According to the group's website, sudo now means su "do" , indicating a tool that provides su-like functionality.<br>

sudo helps minimize such risks and gives system administrators more control. An administrator can do the following:

<ul>
<li>Configure the sudoers file to allow specific users or groups to run some or all commands under the root account or another privileged account.</li>
<li>Maintain granular control over which commands a user can run on each host based on the command names and their directory locations.</li>
<li>View logged activity , which shows which sudo users executed which commands and when they were executed.</li>
<li>Control how long users can execute privileged-level commands after entering their password.</li>
<li>Configure settings for sudo plugins , file paths, debugging , and the frontend interface.</li>
<li>Maintain a single sudoers file that controls access for multiple users on multiple systems.</li>
</ul>

<h3>What's an UFW and what's the value of using it? How to add new rules?</h3>

UFW (Uncomplicated Firewall) is a software application responsible for ensuring that the system administrator can manage iptables in a simple way. It is a tool that minimizes the effort of setting up a firewall by starting with an optimal default configuration. In many cases, it’s only necessary to know the name of the applications to be authorized. Since it is very difficult to work with iptables, UFW provides us with an interface to modify the firewall of our device (netfilter) without compromising security. Once we have UFW installed, we can choose which ports we want to allow connections, and which ports we want to close. This will also be very useful with SSH, greatly improving all security related to communications between devices.

UFW is available for all Linux distributions. UFW uses ports. A port is an unsigned integer from 0 to 65535 that allows the routing of data to a specific service. A port can be open, closed, or stealth. The desired behavior of a firewall is to allow incoming connections only on previously authorized (open) ports, blocking all other (stealth) ports. That’s why the UFW default policy is “deny incoming traffic” and “allow outgoing traffic.” As a result, our server can send requests to the outside world and receive responses. At the same time, the firewall will block all unsolicited incoming connections.

<h3>What's SSH (Secure Shell) and what's the value of using it? How do you check it?</h3>

SSH or Secure Shell is a remote administration protocol that allows users to control and modify their servers over the Internet thanks to an authentication mechanism. Provides a mechanism to authenticate a user remotely, transfer data from the client to the host, and return a response to the request made by the client.
SSH was created as an alternative to Telnet, which does not encrypt the information that is sent. SSH uses encryption techniques to ensure that all client-to-host and host-to-client communications are done in encrypted form. One of the advantages of SSH is that a user using Linux or MacOS can use SSH on their server to communicate with it remotely through their computer's terminal. Once authenticated, that user will be able to use the terminal to work on the server.

The command used to connect to a server with ssh is:

    ssh {username}@{IP_host} -p {port}
    
There are three different techniques that SSH uses to encrypt:

<ul>
  <li>Symmetric encryption: a method that uses the same secret key for both encryption and decryption of a message, for both the client and the host. Anyone who knows the password can access the message that has been transmitted.</li>
  <li>Asymmetric encryption: uses two separate keys for encryption and decryption. These are known as the public key and the private key. Together, they form the public-private key pair.</li>
  <li>Hashing: another form of cryptography used by SSH. Hash functions are made in a way that they don't need to be decrypted. If a client has the correct input, they can create a cryptographic hash and SSH will check if both hashes are the same.</li>
</ul>

<h3>How does the script works and what is cron?</h3>

There are two commands that will be very helpful in case of being system administrators. 
These commands are:
<ul>
<li>Cron: Linux task manager that allows us to execute commands at a certain time. We can automate some tasks just by telling cron what command we want to run at a specific time. For example, if we want to restart our server every day at 4:00 am, instead of having to wake up at that time, cron will do it for us.</li>
<li>Wall: command used by the root user to send a message to all users currently connected to the server. If the system administrator wants to alert about a major server change that could cause users to log out, the root user could alert them with wall.</li>
</ul>

Cron specifically is a job scheduling utility present in Unix-like systems, including Linux virtual machines (VMs). It allows you to schedule tasks to be executed automatically at specific times or intervals. The crond daemon runs in the background and reads the crontab (cron table) files to execute predefined scripts or commands at the specified times.

**Cron jobs are useful for automating repetitive tasks such as backups, log management, and system maintenance, ensuring that these tasks are performed regularly without manual intervention.**

In a Linux VM, cron jobs are managed through the crontab command. Here’s how it works:
1. Editing the Cron Table: Use the crontab -e command to edit the cron table. This command opens a text editor where you can add or modify cron job entries. If it’s your first time using crontab -e, you might be prompted to choose a text editor.
2. Syntax of Cron Jobs: Each cron job entry consists of a schedule and a command. The schedule is defined by five fields in the following order:
Minute (0-59)
Hour (0-23)
Day of the month (1-31)
Month (1-12)
Day of the week (0-6, where 0 or 7 is Sunday)
For example, 0 22 1-5 * * schedules a job to run at 22:00 every day from Monday to Friday.
3. Adding a Cron Job: To add a cron job, you write the schedule and the command in the crontab file. For instance:
4.     0 22 1-5 * * /path/to/your/script.sh

4. This line runs /path/to/your/script.sh at 22:00 every day from Monday to Friday.
5. Running the Cron Daemon: The cron daemon continuously checks the crontab files for scheduled tasks and executes them at the specified times.
6. Viewing Cron Jobs: Use crontab -l to list all the cron jobs for the current user.
7. Deleting Cron Jobs: Use crontab -r to remove all cron jobs for the current user. If you want to be prompted before removing each job, use crontab -i.


<h3>Monitoring</h3>

You have to create a simple script called monitoring.sh It must be developed in bash. At server startup, the script will display some information (listed below) on all ter- minals every 10 minutes (take a look at wall). The banner is optional. No error must be visible. Your script must always be able to display the following information:

<ul>
<li>The architecture of your operating system and its kernel version.</li>
<li>The number of physical processors.</li>
<li>The number of virtual processors.</li>
<li>The current available RAM on your server and its utilization rate as a percentage.</li>
<li>The current available memory on your server and its utilization rate as a percentage.</li>
<li>The current utilization rate of your processors as a percentage.</li>
<li>The date and time of the last reboot.</li>
<li>Whether LVM is active or not.</li>
<li>The number of active connections.</li>
<li>The number of users using the server.</li>
<li>The IPv4 address of your server and its MAC (Media Access Control) address.</li>
<li>The number of commands executed with the sudo program.</li>
</ul>

<h1>What's in this repo?</h1>

You can find the script monitoring.sh in this repository.

---

<h1>Shortcuts for evaluation</h1>

<h3>Check if sudo is installed</h3>
To check if sudo have been installed correctly we must switch to root user and then use the command

    sudo -V

<h3>Add user</h3>
Still in the root user we will create an aditional user with 
        
    sudo adduser <login>

<h3>Check group ID</h3>
To see all groups and the users in any of them

        getent group <groupname>

<h3>To add user to a group</h3>

    sudo adduser <user> <groupname>

---
<h1>References</h1>
<a href="https://www.computerweekly.com/de/definition/sudo">Definition sudo - Computerweekly magazine</a><br>
<a href="https://medium.com/identity-beyond-borders/the-importance-of-implementing-a-strong-password-policy-bb08a9c7b475">The Importance of Implementing a Strong Password Policy</a><br>
<a href="https://www.debian.org/">Debian</a><br>
<a href="https://rockylinux.org/">Rocky Linux</a><br>
<a href="https://github.com/ayoub0x1/born2beroot/blob/main/README.md">Ayoub Github Readme</a><br>
<a href="https://www.redhat.com/en/topics/virtualization/what-is-a-virtual-machine">What is a Virtual Machine - RedHat</a><br>
<a href="https://www.baeldung.com/linux/uncomplicated-firewall"> Uncomplicated Firewall - Baeldung</a><br>
<a href="https://opensource.com/article/17/11/how-use-cron-linux"> How to use cron Linux</a><br>
<a href="https://www.freecodecamp.org/news/cron-jobs-in-linux"> Cron Jobs in Linux</a><br>




