Linux SSH key setup
===============================
step 1.) Change directory to below path
----------------
cd /root/.ssh

step 2.) Generate ssh key using ssh-keygen
-----------------------------------
ssh-keygen

keep secret password for ssh
--------------------------
RSA_PASSWORD #Ot0616@

step 3. Copy id_rsa.pub to authorized_keys
----------------------------------------
cat id_rsa.pub >> authorized_keys



JENKINS ssh key setup
============================
https://plugins.jenkins.io/ssh-agent/
Add credentials
---------------------
http://localhost:8000/credentials/store/system/domain/_/
With privatekey and passphrase