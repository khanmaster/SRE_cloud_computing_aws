# SRE introduction 
## Cloud Computing with AWS
### SDLC stages
#### Risk factors with SDLC stages
##### Monitoring

### Key Advantages:
- Ease of use
- Flexibility
- Robustness
- Cost

**SRE introduction**
- What is the role of SRE?




**Cloud Computing**
- What is Cloud Computing and the benefits of using it?


**What is Amazon Web Services (AWS)**
- What is AWS and benefits of using it



**What is SDLS and stages of SDLC**
- What is SDLC and what are the stages of it

**What are the Risk level at each stage of SDLC?**
- LOW
- Medium
- High

- What is on prem, cloud and Hybrid cloud and multi cloud
- add a diagram for each case with real life example or use cases
- pros and cons of each model

- Let's move onto creating Dev env with Virtual box and vagrant
- create a file `Vagrantfile`
- Add below code:
```bash
Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/xenial64"
    config.vm.network "private_network", ip: "192.168.10.100"
    
    # Synced app folder
    config.vm.synced_folder "app", "/app"

    # Provisioning
    config.vm.provision "shell", path: "provision.sh", privileged: false

end
```
- Run `vagrant up`
- type in the browswer `192.168.10.100`

#### Let's install dependencies for our node app
- install nodejs
- `sudo apt-get install nodejs -y`
- Ensure to install correct version
```bash
  sudo apt-get install python-software-properties
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install nodejs -y
```

- install pm2
`sudo npm install pm2 -g`
- Ensure to run this inside the app folder - install npm `npm install`
- Launch the app `npm start`
- `192.168.10.100:3000`
-----------------------------------


#### Let's set up Reverse proxy with ngingx
```
server {
    listen 80;

    server_name _;

    location / {
        proxy_pass http://localhost:3000;      
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade'; 
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;      
    }
}
```
- `sudo nginx -t`
- `sudo systemctl restart nginx`
- Restart the node app from the app location `npm start`
- check your browser now without the port 3000

- If you have mongodb installed 
- `sudo nano /etc/mongo.conf`
- `ip 127.0.0.1` change to `0.0.0.0` port: `27017`
- restart mongo
- enable mongo
- check status to ensure it's active 