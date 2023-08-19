Requirements: 
-> deployment/NGINX & WEBSITE setup 
-> Install NVM node version manager
-> open ports from config.json
-> start XTEnetwork high availability server
-> start XTEservice for payment processing
-> Install and run xte-cryptonote-nodejs-pool and adjust config.js in website_example


# | FULL SETUP 
Install nvm: 
sudo apt install curl 
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash 
--> add setup variables

nvm install 11
nvm use 11
npm install forever -g


/- XTEnetwork high availability monitor

git clone https://github.com/TRRXITTE/XTEnetwork-ha
cd XTEnetwork-ha
npm install

wget https://github.com/TRRXITTE/XTEnetwork-ha/releases/download/0.10.0-XTEnetwork/XTEnetwork-0.10.0_ubuntu-20.04 XTEnetwork
chmod +x XTEnetwork

forever start service.js // node service.js


/- wallet service for payment processing

CREATE wallet with traaittwallet ++
name: pool
password: [YOUR PASSWORD]
download XTEservice for Ubuntu
screen -S service
./XTEservice --container-file /home/traaitt/pool.wallet --container-password YOURPASSWORD --enable-cors  * --rpc-legacy-security --bind-port 8440

control A + D to detach
// to reattach screen session -> screen ls -> screen -r sessionid.service


cd xte-cryptonote-nodejs-pool
nvm use 11
npm install

/ edit config.json parameters for [XTE]

forever start init.js // node init.js

