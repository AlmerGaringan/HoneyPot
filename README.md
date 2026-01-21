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
The next step is choosing the image for the honeypot. I decided to go with Ubuntu 24.04 (TLS) x64 because I've seen that it is compatible with the Telekom security, which we will need for our dashboard to analyze the attackers' behavior and location. 

After deciding on the image, now we have to choose the size, and for the honeypot, it takes up a lot of space. The minimum needed memory is 8GB to build the honeypot. Hence, the reason I chose the 8 GB and 4 CPUs. The CPU options don't matter, and any options would work.
