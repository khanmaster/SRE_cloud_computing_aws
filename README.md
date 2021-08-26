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

    # Provisioning
    config.vm.provision "shell", path: "provision.sh", privileged: false

end
```

- Run `vagrant up`
- type in the browswer `192.168.10.100`