# generate ssh key on slave  machine

ssh-keygen -t rsa

# copy id_rsa.pub and paste into authorized keys
cat id_rsa.pub

# copy private key (without space and new line) paste into jenkin ssh with private key 


# if know host issue remove old config 
ssh-keygen -R 192.168.1.100

# ref
https://www.youtube.com/watch?v=Se7JtzFVZGE&ab_channel=DevOpsVijay

