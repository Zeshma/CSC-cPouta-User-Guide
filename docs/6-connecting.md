# 6. Connecting to Your Virtual Machine
After assigning a Floating IP to your virtual machine, you can connect to it using SSH. In this guide we use PuTTY.
## 6.1 Connecting with PuTTY (Windows)

1.	Open **PuTTY** and **Load** the session created earlier.
2.	In **Host Name (or IP address)**, enter: ubuntu@(your Floating IP here) and click **Open**.
**Note:** For your Floating IP check the guide **5.2 step 5**. 192.168.x.xxx is your virtual machine local IP, DO NOT use this.
       <p align="center">
    <img src="/images/Picture24.png" alt="A computer screenschot of putty interface" class="guide-screenshot" />
    </p>
3.	You should now be connected to the virtual machine and see the terminal.
       <p align="center">
    <img src="/images/Picture25.png" alt="A screenshot of a putty terminal window" class="guide-screenshot" />
    </p>
4.	After logging in, update the system with the script below. This ensures your VM has the latest security patches.

Run:

    sudo apt update && sudo apt upgrade -y

---

## 6.2 Common connection issues

- **Permission denied (publickey)**  
  → Wrong key file or not assigned during VM creation
    -	In **PuTTY** go to **Category → Connection → SSH → Auth → Credentials → Browse…** (Private key file for authentication:) and select the correct .ppk file

- **CIDR too strict**  
  → If your IP changed (e.g., mobile hotspot, different networks etc.) rules may block you.
    -	Update your SSH rule CIDR to match your new IP
