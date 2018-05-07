# Install decentralized tools from scratch in a Linux server to go onLine

SSH to your server.
Keep it up-to-date :
```
 sudo apt-get update
 sudo apt-get upgrade
```
Install TMUX to be able to keep your command line running after you close connection. Not the cleanest way to do it but the easiest.
```
sudo apt-get install tmux git
```

### IPFS
Check last version here : https://dist.ipfs.io/#go-ipfs
```
sudo apt-get update
sudo apt-get install golang-go -y
wget https://dist.ipfs.io/go-ipfs/v0.4.14/go-ipfs_v0.4.14_linux-amd64.tar.gz -O go-ipfs.tar.gz
tar xvfz go-ipfs.tar.gz
sudo cp go-ipfs/ipfs /usr/local/bin/ipfs
ipfs init
tmux
ipfs daemon
```
=> Close the terminal and IPFS daemon will keep running

## ETH testnet
```
  sudo apt-get install software-properties-common
  sudo add-apt-repository -y ppa:ethereum/ethereum
  sudo apt-get update
  sudo apt-get install ethereum
  tmux
  geth --testnet --fast --rpc --rpcapi eth,net,web3,personal --rpcport 9546
```

## Reverse proxy with NGINX

It allow you to make many HTTP servers running locally on different port avaliable on the port 80 via multiple domain pointing to the same IP.
It is the easiest way I find to expose services like node and GETH without open too many port.
The drawback is that you have to create domains.

```
  sudo apt-get install nginx
  sudo  nano /etc/nginx/sites-enabled/default 
```
 
```javascript
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
```
Run NginX
```
  sudo service nginx start
```

## Ganache-cli
```
  sudo apt-get install -y build-essential
  curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
  sudo apt-get install -y nodejs
  sudo npm install -g ganache-cli
```

=> Clone your project and run it

## HTTPS
Use let's Encrypt certbot

## Open port in firewall

Open tcp:22 for SSH
Open tcp:443 and tcp:80 for HTTP and HTTPS
open tcp:5001 and tcp:4001 For IPFS 

And that's it you good to go !



