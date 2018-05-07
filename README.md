# dapps_experiment
Decentralized application test following https://www.theschool.ai

## Install from scratch on the Cloud

### IPFS
Check version here : https://dist.ipfs.io/#go-ipfs
sudo apt-get update
sudo apt-get install golang-go -y
wget https://dist.ipfs.io/go-ipfs/v0.4.14/go-ipfs_v0.4.14_linux-amd64.tar.gz -o go-ipfs.tar.gz
tar xvfz go-ipfs.tar.gz
sudo mv go-ipfs/ipfs /usr/local/bin/ipfs
tmux
sudo 

## ETH testnet
   40  sudo apt-get install software-properties-common
   41  sudo add-apt-repository -y ppa:ethereum/ethereum
   42  sudo apt-get update
    sudo apt-get install ethereum
   sudo apt-get install git
   
## Ouverture de port

## Reverse proxy

  sudo apt-get install nginx
  sudo  nano /etc/nginx/sites-enabled/default 
 
'''
server {
    listen 80;
    server_name testrpc.yourdomain.fr;
    location / {
        proxy_pass http://localhost:8545;
        proxy_redirect off;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
server {
    listen 80;
    server_name exoloop.yourdomain.fr;
    location / {
        proxy_pass http://localhost:3000;
        proxy_redirect off;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
'''

  sudo service nginx start

## HTTPS
Use let's encrypt and certbot

## Open port

And that's it you good to go !

sudo apt-get install tmux software-properties-common 
   20  sudo cp go-ipfs/ipfs /usr/local/bin/

   61  
   62  
   69  sudo usermod -a -G www-data youruser


 
  290  
  302  sudo npm install -g ganache-cli truffle
  339  sudo apt-get install node
  340  sudo apt-get install nodejs
  343  sudo apt-get remove nodejs
  344  sudo apt-get install nodejs npm
  345  sudo apt-get update
  346  sudo apt-get install nodejs npm
  347  sudo apt-get install -y build-essential
  349  curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
  350  sudo apt-get install -y nodejs
  353  sudo npm install -g ganache-cli solc web3@0.20.2
  376  sudo npm install -g ganache-cli
  379  sudo nano /etc/nginx/nginx.conf 
  388  sudo service nginx stop
  390  sudo service nginx start
  398  sudo service nginx restart
  411  sudo halt
  413  sudo apt get update
  414  sudo apt-get update
  597  sudo nano /etc/nginx/sites-enabled/default 
  598  sudo service nginx restart
