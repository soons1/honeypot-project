# _T-Pot_ honeypot on Debian 11

The project started as a way for me to figure out how to implement a honeypot on a server. I eventually settled on using [T-Pot](https://github.com/telekom-security/tpotce) as my open-source honeypot of choice due to its support for a wide variety of platforms and its comprehensive dashboard. In order to securely host the honeypot, I spun up a virtual _Debian 11_ instance using [AWS EC2](https://aws.amazon.com/).

*Pre-requisites:*
- AWS account (to spin up EC2 instance)
- Git (to pull the GitHub repo)
- SSH client (in my case, Terminal)

*Timeline:*
1. To begin, I spun up an EC2 instance purely meant to host the honeypot. Security considerations meant having a remote, virtual server via cloud services separate from any local instance was the best option. Using the recommended instance type and RAM requirements, I created the instance with a Debian 11 image, with configured firewall rules to allow malicious actors to "attack" the system.
   ![Screenshot 2024-01-31 at 4 52 50 PM](https://github.com/soons1/honeypot-project/assets/103474763/aac32301-0c76-4258-8ce6-1f5c1a3fd55d)
2. Next, using my Terminal, I SSH-ed to my instance using the key-pair created earlier.
3. On my virtual machine, I then pulled the GitHub repository of T-Pot and installed the honeypot on the machine. This was the commands used:
   ```
   sudo apt update -y 
   sudo apt install git -y
   git clone https://github.com/telekom-security/tpotce
   cd tpotce/iso/installer/
   sudo ./install.sh --type=user
   ```
4. Following the instructions on the installation of T-Pot, I set up the honeypot platform on the Debian instance.
   ![Screenshot 2024-05-18 at 2 56 24 PM](https://github.com/soons1/honeypot-project/assets/103474763/89eab605-bb8c-44c6-99e2-94aa665df234)
5. Once installed, I can access the dashboard locally on the machine. Here are some of the features available on T-Pot:
   ![tpotportfolio](https://github.com/soons1/honeypot-project/assets/103474763/eb6b82b1-d9a2-43c7-81e9-9febdcbd8722)

   The *attack map* allows administrators to see the source of the attacks on the honeypot (though it is likely to be spoofed locations)
   ![Screenshot 2024-01-18 at 2 00 24 AM](https://github.com/soons1/honeypot-project/assets/103474763/ae340f46-c718-4be9-86a4-eeac12037dc3)

   The comprehensive *dashboard* summarises the attacks on the honeypot:
   ![Screenshot 2024-01-18 at 2 11 25 AM](https://github.com/soons1/honeypot-project/assets/103474763/98bf9d92-9196-4fdd-8404-ab93c3b82ee3)

*Thoughts:*
- This exercise allowed me to explore more amazing open-source tools in the world of security, this time with a common defense tactic: _honeypots_.
- Furthermore, I was able to practice the setting up and configuration of EC2 instances

Thank you for reading!🍯
