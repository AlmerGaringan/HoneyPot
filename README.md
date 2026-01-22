# HoneyPot
A honeypot is a fake vulnerable network to trick attackers, so we are able to analyze their behavior, including how they attack and where they attack. The reason I wanted to build a honeypot is to deepen my skills and learn how attackers behave, as well as where most attackers originate from. I learned a lot while building this project, including Linux, firewalls, security grouping, cloud providers, and defensive security.

# Things I used to build this project

VirtualBox: - 4096 MB Memory
             - 4 CPU
             - Kali Iso

DigitalOcean: - Ubuntu 24.04 (LTS) x64 (Image) - Basic CPU - 8 GB Memory - 4 CPU

Github Repo: - Telekom Security Repo (T-Pot)
               
# Installation 

<img width="2046" height="714" alt="screenshot-1768990249232" src="https://github.com/user-attachments/assets/88e4285e-6ce6-4e11-b49c-38402c73090c" />
I decided to use Digital Ocean cloud provider because I wanted to do something a little different since everyone does an AWS EC2 HoneyPot. In Digital Ocean, I created a droplet, then I chose San Fransico because I wanted to see how many attackers attack in my region.  

<img width="2047" height="1032" alt="screenshot-1768990312451" src="https://github.com/user-attachments/assets/c7d152c7-cc0d-4a75-bae7-44d071a0186d" />
The next step is choosing the image for the honeypot. I decided to go with Ubuntu 24.04 (TLS) x64 because I've seen that it is compatible with the Telekom security, and I was already comfortable with Ubuntu. The telekom security will be important because we will need it for our dashboard to analyze the attackers' behavior and location. 

After deciding on the image, now we have to choose the size, and for the honeypot, it takes up a lot of space. The minimum needed memory is 8GB to build the honeypot. Hence, the reason I chose the 8 GB and 4 CPUs. The CPU options don't matter, and any options would work.

<img width="2049" height="1033" alt="screenshot-1768990366313" src="https://github.com/user-attachments/assets/dd000826-06f7-4e23-a1f0-9efda6749330" />
Next, I had to choose an authentication method. I decided to go with the password method because I've already done the ssh key method, so I feel like the password method is faster than the SSH key method. The reasoning is that you would have to download the ssh key to your file and then chmod the file so that it is only readable. Once I finished choosing the password method, I was ready to create the droplet. 

<img width="2044" height="1037" alt="droplet covered" src="https://github.com/user-attachments/assets/b2a2328c-2b6c-4b40-8d6a-f07b7c1830ae" />
This is what it looks like after I created my droplet. We are given IPv4, which is the public IP. This will be important because we will need to ssh into this IP address, and  this is where we will be accessing the T-Pot later on. We also given the private IP for the cloud that is being used. 

<img width="1269" height="662" alt="Screenshot 2026-01-21 010617" src="https://github.com/user-attachments/assets/9aaf1184-f865-4599-b010-a0b4e98b5b9a" />
Inside the Virtual Box, I went to the terminal, and before I even started, I did the command  "ip a" to make sure my eth0 reaches the network and shows an IP address like 10.XX.XX.XX. The reasoning for this is that sometimes I wouldn't be able to reach the network, so I would have to disconnect my wired connection, then reconnect the wired connection, then in the terminal test out "ip a" again. Eventually, I would see an IP address under eth0. I ssh into root@IP-Address to remote into the server. I successfully got into the server, and you could see that at the bottom, where you see root@HoneyPot. 

<img width="1137" height="970" alt="screenshot-1768989724439" src="https://github.com/user-attachments/assets/dac8888a-266d-41fc-b316-074207c950ca" />
Before adding the user, I ran the command "apt-get update && apt-get upgrade -y". This will update the server and upgrade any tools or repositories. 

The reason I decided to adduser is that I need a non-root user to run the honeypot on. Instead of the root user being where the honeypot is running, this can cause any compromised information. Then I had to put in the password for Almer. The password will be very important later on. But for the value for the user doesn't matter, you could leave them blank because for the honeypot, those values aren't being used. Almer has the least privileges, that's why I ran the command " sudo usermod -aG sudo almer ". This will give almer sudo privileges, which is like root or admin privileges. Then I wanted to switch user to almer. Hence, why you see " su almer " then you see " almer@HoneyPot/root$ ". I wanted to go home, but in the almer account, that's why I " cd /home/almer. I wanted to make sure I had git install so I ran " sudo apt install git " to just make sure I have git installed, and I did because the next command will need git for it to work. The next command is to copy the GitHub repositories for the T-Pot " git clone https://github.com/telekom-security/tpotce" that is the URL of the T-POT repository. When it was finished cloning, I wanted to make sure it was there, then I wanted to change my directory into the tpotce. I was able to see different types of directories and files. But the only one that we need here is "install.sh"; this will install the T-Pot. To install the T-Pot, I ran the " ./install.sh " command. 

During the middle of the installation of the T-Pot, it will show that the ssh port is now 64295. Also, towards the middle, it will ask you what type of installation type do you want to install. I chose h, which is hive because it is the T-Pot stand. There were other ones, including S (T-Pot Sensor), L (T-Pot LLM), I (T-Pot Mini), M (T-Pot Mobile), and T (T-Pot Tarpit). These are all different types of T-pot. Near the end, it will ask you to put a web user name and password, which will be important later on as well. 

<img width="1279" height="195" alt="Screenshot 2026-01-21 012112" src="https://github.com/user-attachments/assets/79abe2f7-785c-44ac-8b9b-9c79ae82a2b3" />
At the end of the installation, it will show us the active internet connections. I see that we have our 64295 active, which is the new port to ssh into. Then it asks us to reboot. Once we reboot, it will kick us back to our machine.

<img width="1270" height="642" alt="Screenshot 2026-01-21 012349" src="https://github.com/user-attachments/assets/e001f1b1-3dab-4ebe-8f2f-0afcc2750251" />
I have to ssh into the port because the old port (22) doesn't work anymore. So once I tried to ssh -p 64295 root@IP-Address, I was able to connect to the root server. -p means port. After this, everything should be able to work now.

<img width="1051" height="1083" alt="screenshot-1768989861649" src="https://github.com/user-attachments/assets/5d233de3-7e78-4a32-a30d-c0766af74106" />
So inside the browser of VirtualBox, I put " https://Public-IP:64297 ". 64297 is the listening port, and I was able to find this through the GitHub telekom-security repository. The reason why I did it inside of my VirtualBox is that I tried to access the website through my laptop, and it says unsecure which we need, but it didn't let me advance through the website. So I decided to try it in Firefox inside my VirtualBox, then I was finally able to get the option to advance. When loading, it will ask for your username and password; it will be the one you used during the T-Pot setup. 

# Results
I let my honeypot run for less than 2 hours, and during that time, I was able to get these results. 

<img width="986" height="1010" alt="screenshot-1768995715102" src="https://github.com/user-attachments/assets/84ebec27-498c-41c1-868a-9314ffa6463a" />
<img width="1049" height="812" alt="screenshot-1768995673051" src="https://github.com/user-attachments/assets/9a19e497-247c-4914-9b73-bacc7e59b0e5" />
<img width="1046" height="1012" alt="screenshot-1768995729260" src="https://github.com/user-attachments/assets/b8b2cede-5dda-40c6-a04d-9adcb1be2952" />
I was able to see where the attackers are mostly coming from its in Europe and the East Coast of America. I see that attackers are mostly trying " root " for the username and nothing for the password. To me, it is really interesting how basic the usernames and passwords they're trying are. I could also see which port they're attacking, which in this case is the majority port 22.

# Conclusion
This was a very fun project to build, and I definitely learned a lot while I was building this project. I ran into a couple of challenges while building this project, including troubleshooting my connection, missing Docker containers at times, and T-Pot wasn't working. But in reality, this is what the IT and CyberSecurity field is all about: running into an error and then stressing about it, and then figuring out a way to fix it and make it work. I am glad that I was able to fix my mistake and finish this project. I learned a lot about Blue Team concepts, hands-on troubleshooting, Linux, attacker mindset, cloud infrastructure, and networking. 
