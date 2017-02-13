# howto_install_vagrant_on_windows
A how to guide on installing Vagrant on Windows

# Overview
- Install VirtualBox
- Install Vagrant
- Install Cygwin
- Verify installation

# Install VirtualBox
- In your browser and navigate to: https://www.virtualbox.org/wiki/Downloads
- Under the "VirtualBox binaries" section, click the first "Windows hosts" link un VirtualBox platform packages
- Once downloaded, launch the VirtualBox installer, allow it to have administrator privileges to install the software

# Install Vagrant
- In your browser and navigate to: https://www.vagrantup.com/downloads.html
- Under the "WINDOWS" section, click the Universal (32 and 64-bit) link
- Once downloaded, launch the Vagrant installer, allow it to have administrator privileges to install the software

# Install Cygwin
- In your browser and navigate to: https://www.cygwin.com
- Under the "Current Cygwin DLL version" section, click the"setup-x86.exe" link
- Navigate to your Start Menu, and find the "Command Prompt" icon in your program list in the "Windows System" section
- Right click on the "Command Prompt" and choose "Pin to taskbar"
- Once "setup-x86.exe" has downloaded, open a Command Prompt window
- Type the following lines into your Command Prompt window
cd Downloads
mkdir C:\cygwin-installer"
move /y setup-x86.exe C:\cygwin-installer
cd C:\cygwin-installer
notepad install-cygwin.bat
- Copy and paste the following text into the bat file in Notepad, then save and exit Notepad
setup-x86.exe ^
--no-desktop ^
--quiet-mode ^
--disable-buggy-antivirus ^
--upgrade-also ^
--packages ^
curl,^
git,^
openssh,^
rsync,^
vim,^
wget
- Type the following lines into your Command Prompt window, and allow it to have administrator privileges to install the software.
install-cygwin.bat
- Navigate to your Start Menu, and find the "Cygwin Terminal" icon in your program list
- Right click on the "Cygwin Terminal" and choose "Pin to taskbar"

# Verify installation
- Type the following lines into your Command Prompt window
mkdir C:\Vagrant
cd C:\Vagrant
mkdir centos-test
cd centos-test
vagrant init bento/centos-7.2
vagrant up
- If everything goes right, you should see output that looks something like:
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Importing base box 'bento/centos-7.2'...
==> default: Matching MAC address for NAT networking...
==> default: Checking if box 'bento/centos-7.2' is up to date...
==> default: Setting the name of the VM: centos-test_default_1487016045788_11084
==> default: Fixed port collision for 22 => 2222. Now on port 2200.
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 (guest) => 2200 (host) (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2200
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: Warning: Remote connection disconnect. Retrying...
    default:
    default: Vagrant insecure key detected. Vagrant will automatically replace
    default: this with a newly generated keypair for better security.
    default:
    default: Inserting generated public key within guest...
    default: Removing insecure key from the guest if it's present...
    default: Key inserted! Disconnecting and reconnecting using new SSH key...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
==> default: Mounting shared folders...
    default: /vagrant => C:/Vagrant/centos-test
- Let's log into the box.
- Type the following lines into your Command Prompt window
vagrant ssh
- You should see:
[vagrant@localhost ~]$
- Congratulations!  To exit the vagrant box, just type:
exit
- To destroy the vagrant box, type the following line into your Command Prompt window
vagrant destroy -f
- That's how easy it is!
