# 42Berlin_Born2BeRoot
The project aims to install Debian virtual machine.

![Born2Be](https://github.com/user-attachments/assets/f95de2dd-df3e-4e0f-9b5d-073eee581a06)

<h1>About the project</h1>

<h1>General questions related to the project</h1></h3>

<h3>How does a virtual machine work ? And what its purpose?</h3>

<h3>Why did I choose Debian?</h3>

<h3>What's the difference between Debian and Rocky?</h3>

<h3>What's the difference between aptitude, apt and what's APPArmor ?</h3>

AppArmor provides Mandatory Access Control (MAC) security. In fact, AppArmor allows the system administrator to restrict the actions that processes can perform. For example, if an installed application can take photos by accessing the camera application, but the administrator denies this privilege, the application will not be able to access the camera application. If a vulnerability occurs (some of the restricted tasks are performed), AppArmor blocks the application so that the damage does not spread to the rest of the system.
In AppArmor, processes are restricted by profiles. Profiles can work in complain-mode and in enforce-mode. In enforce mode, AppArmor prohibits applications from performing restricted tasks. In complain-mode, AppArmor allows applications to do these tasks, but creates a registry entry to display the complaint.

And what is the difference between Apt and Aptitute?
In Debian-based OS distributions, the default package manager we can use is dpkg. This tool allows us to install, remove and manage programs on our operating system. However, in most cases, these programs come with a list of dependencies that must be installed for the main program to function properly. One option is to manually install these dependencies. However, APT (Advanced Package Tool), which is a tool that uses dpkg, can be used to install all the necessary dependencies when installing a program. So now we can install a useful program with a single command.
APT can work with different back-ends and fron-ends to make use of its services. One of them is apt-get, which allows us to install and remove packages. Along with apt-get, there are also many tools like apt-cache to manage programs. In this case, apt-get and apt-cache are used by apt. Thanks to apt we can install .deb programs easily and without worrying about dependencies. But in case we want to use a graphical interface, we will have to use aptitude. Aptitude also does better control of dependencies, allowing the user to choose between different dependencies when installing a program.

<h3>What the advantages of a strong password policy? How's its implementation?</h3>
A password policy is a set of guidelines and rules that define how passwords should be created, used, and protected in an organization’s network or web application. The policy may include requirements for password length, complexity, and expiration, as well as guidelines for protecting passwords from unauthorized access or disclosure. A password policy is intended to help ensure the security of an organization’s digital assets by reducing the risk of password-related attacks, such as brute-force attacks or password cracking. It is typically enforced through security software or by administrative procedures, and users are expected to comply with the policy in order to access the organization’s resources.

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

<h3>What's an UFW and what's the value of using it? How to add new rules?</h3>

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


<h1>What's in this repo?</h1>

---
<h1>References</h1>
<a href="https://medium.com/identity-beyond-borders/the-importance-of-implementing-a-strong-password-policy-bb08a9c7b475">The Importance of Implementing a Strong Password Policy</a>


