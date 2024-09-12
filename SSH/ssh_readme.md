How To Use SSH to Connect to a Remote Server

SSH works by connecting a client program to an ssh server, called sshd


# On Ubuntu, you can start the ssh server
sudo systemctl start ssh


In Ubuntu, the main sshd configuration file is located at /etc/ssh/sshd_config

# view ssh config
cat /etc/ssh/sshd_config


# default setting 
PubkeyAuthentication yes
ChallengeResponseAuthentication no
UsePAM yes
X11Forwarding yes
PrintMotd no
AcceptEnv LANG LC_*
PasswordAuthentication yes
PermitRootLogin yes
Subsystem       sftp    /usr/lib/openssh/sftp-server
