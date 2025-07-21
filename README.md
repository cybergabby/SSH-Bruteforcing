# SSH-Bruteforcing
🚨 SSH Brute Forcing: Attack & Defense Explained
🔐 What is SSH Brute Forcing?

SSH Brute Forcing is an attack where an attacker attempts to gain unauthorized access to a system by guessing the username and password repeatedly on port 22 (SSH service) until successful.

It’s a common initial access technique used by attackers and often seen in Capture The Flag (CTF) challenges or real-world penetration tests.
🧠 How It Works

The attacker uses a wordlist of usernames and passwords and tries all combinations against an SSH service using automation tools. If the target allows weak credentials, the attacker gets a shell.
🔁 Attack Flow:

    Target system has SSH open (nmap scan on port 22).

    Use a tool like Hydra or Medusa with a username/password list.

    Upon success, SSH access is gained, often with user privileges.

🛠 Tools for SSH Brute Force
1. Hydra

A popular login cracker that supports many protocols.

hydra -l root -P /usr/share/wordlists/rockyou.txt ssh://192.168.1.10

    -l root: username

    -P rockyou.txt: password list

    ssh://: protocol and IP

2. Medusa

medusa -h 192.168.1.10 -u root -P /usr/share/wordlists/rockyou.txt -M ssh

    -M ssh: module

    -u root: username

3. Ncrack

ncrack -p 22 -u root -P rockyou.txt 192.168.1.10

    Built for speed, great for large-scale brute-force.

🔍 Finding Targets

First, use Nmap to find systems with SSH enabled:

nmap -p 22 --open -T4 -Pn 192.168.1.0/24

🎯 Example in a Lab (e.g., TryHackMe or HackTheBox)

    Find IP with SSH open:

nmap -sS -p 22 10.10.10.10

    Brute force with Hydra:

hydra -l admin -P rockyou.txt ssh://10.10.10.10

    On success:

ssh admin@10.10.10.10

You now have access!
🔐 Real-World Impacts

    Unauthorized access to systems.

    Lateral movement within a network.

    Privilege escalation if weak credentials are reused across systems.

    Data exfiltration or ransomware deployment after access.

🛡 How to Defend Against SSH Brute Forcing
Defense	Description
✅ Disable root login	In /etc/ssh/sshd_config, set PermitRootLogin no
✅ Use strong passwords	Enforce minimum 12+ character complex passwords
✅ Enable key-based login	Use public/private keys instead of passwords
✅ Rate limiting	Use fail2ban to block IPs with repeated failed attempts
✅ Change default SSH port	Use an uncommon port instead of 22
✅ Disable password login entirely	Use PasswordAuthentication no in sshd_config
💬 Final Thoughts

SSH brute forcing is a simple yet powerful technique when systems are misconfigured or protected with weak credentials. It’s a common entry point during red team operations and a must-know for cybersecurity learners.

👉 Always test ethically, with permission, or in lab environments like TryHackMe, HackTheBox, or your own VM labs.
📎 Resources

    Hydra GitHub

    Fail2Ban Guide

    TryHackMe Brute Force Room

    Common Password Lists

✍️ About the Author

Gabriel Odusanya Oluwapelumi
3rd-Year CS Student | Cybersecurity Enthusiast | API & Network Pentester

    GitHub: @cybergabby
    Medium: Gabbytech
    X (Twitter): @Gabriel_coder01
