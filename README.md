# HoneyPot
A honeypot is a fake vulnerable network to trick attackers so we are able to analyze their behavior, including how they attack and where they attack. The reason I wanted to build a honeypot is to deepen my skills and learn how attackers behave, as well as where most attackers originate from. I learned a lot while building this project, including Linux, firewalls, security grouping, cloud providers, and defensive security.

# Things I used to build this project

Virtual Box: - 4096 MB memory
             - 4 CPU
             - Kali iso

Digital Ocean: - Ubuntu 24.04 (LTS) x64 (Image)
               - Basic CPU 
               - 8 GB 
               - 4 CPU

Github Repo: - Telekom Security Repo (T-Pot)
               
# Installation 

<img width="2046" height="714" alt="screenshot-1768990249232" src="https://github.com/user-attachments/assets/88e4285e-6ce6-4e11-b49c-38402c73090c" />
I decided to use Digital Ocean cloud provider because I wanted to do something a little different since everyone does an AWS EC2 HoneyPot. In Digital Ocean, I created a droplet, then I chose San Fransico because I wanted to see how many attackers attack in my region.  

<img width="2047" height="1032" alt="screenshot-1768990312451" src="https://github.com/user-attachments/assets/c7d152c7-cc0d-4a75-bae7-44d071a0186d" />
The next step is choosing the image for the honeypot. I decided to go with Ubuntu 24.04 (TLS) x64 because I've seen that it is compatible with the Telekom security and I was able comfortable with Ubuntu. The telekom security will be important because we will need it for our dashboard to analyze the attackers' behavior and location. 

After deciding on the image, now we have to choose the size, and for the honeypot, it takes up a lot of space. The minimum needed memory is 8GB to build the honeypot. Hence, the reason I chose the 8 GB and 4 CPUs. The CPU options don't matter, and any options would work.

<img width="2049" height="1033" alt="screenshot-1768990366313" src="https://github.com/user-attachments/assets/dd000826-06f7-4e23-a1f0-9efda6749330" />
Next, I had to choose an authentication method. I decided to go with the password method because I've already done the ssh key method, so I feel like the password method is faster then the ssh key method. The reasoning is that you would have to download the ssh key to your file and then chmod the file so that it is only readable. Once I finished choosing the password method, I was ready to create the droplet. 

<img width="2044" height="1037" alt="droplet covered" src="https://github.com/user-attachments/assets/b2a2328c-2b6c-4b40-8d6a-f07b7c1830ae" />
This is what it looks like after I created my droplet. We are given IPv4, which is the public IP, this will be important because we will need to ssh into this IP address also  this is where we will be accessing the T-Pot later on. We also given the private IP for the cloud that is being used. 

<img width="1269" height="662" alt="Screenshot 2026-01-21 010617" src="https://github.com/user-attachments/assets/9aaf1184-f865-4599-b010-a0b4e98b5b9a" />
Inside the Virtual Box, I went to the terminal, and before I even started, I did the command  "ip a" to make sure my eth0 reaches the network and shows an IP address like 10.XX.XX.XX. The reasoning for this is that sometimes I wouldn't be able to reach the network, so I would have to disconnect my wired connection, then reconnect the wired connection, then in the terminal test out "ip a" again. Eventually, I would see an IP address under eth0. I ssh into root@IP-Address to remote into the server. I successfully got into the server, and you could see that at the bottom, where you see root@HoneyPot. 
