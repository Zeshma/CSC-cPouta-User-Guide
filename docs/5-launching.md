# 5. Launching a Virtual Machine

## 5.1 Creating a virtual machine
Once the SSH keys and security groups are ready, you can launch a new virtual machine.

1.	In cPouta dashboard navigate to **Compute → Instances** and click **Launch Instance**
     <p align="center">
    <img src="../images/picture17.png" alt="A screenshot of a cPouta dashboard" class="guide-screenshot" />
    </p>
2.	Add **Instance Name** and select the number of instances (**Count**) you wish to create. Click **Next**.
3.	Select your **Instance Boot Source**. Select “image” in the drop-down menu and click on the **↑** Click **Next**. In this guide we are using Ubuntu-24.04 but image source might change.
      <p align="center">
    <img src="../images/picture18.png" alt="A screenshot of a cPouta instances dashboard" class="guide-screenshot" />
    </p>
4.	Select the **Flavour** which means the “size” of the Virtual Machine by clicking on the **↑** icon.
5.	In **Networks** section, make sure your project is allocated.
6.	In **Security Groups** section assign the security group that was created earlier with **↑** icon.
       <p align="center">
    <img src="../images/picture19.png" alt="A screenshot of a cPouta security groups dashboard" class="guide-screenshot" />
    </p>
7.	In **Key Pair** section make sure the Key Pair created earlier is **Allocated**, if not select it with **↑** icon. **Important:** SSH keys must be selected at this stage, they cannot be added later. If no key is chosen, delete the VM and create a new one.
8.	You can now click **Launch Instance** to create the Virtual Machine.


---

## 5.2 Assigning a Floating IP
To connect to your virtual machine, you must assign a Floating IP (public IP):

1.	In the cPouta dashboard, go to **Compute → Instances**. Here you should see the new instance.
2.	On the right side under **Actions**, open drop-down menu and select **Associate Floating IP**.
        <p align="center">
    <img src="../images/picture20.png" alt="A screenshot of a cPouta dashboard showing how to setup floatinIP" class="guide-screenshot" />
    </p>
3.	Under **IP Address**, choose an available floating IP. If you see “**No floating IP addresses allocated**” click the **+** button and click **Allocate IP**.
   <div style="display:flex; justify-content:center; gap:20px; align-items:flex-start;">
   <img src="../images/picture21.png" alt="A screenshot of a cPouta floating IP dashboard" style="width:45%;">
   <img src="../images/picture22.png" alt="A screenshot of a cPouta floating IP dashboard" style="width:45%;">
   </div>
4.	Under **Port to be associated**, select your virtual machine and click **Associate**.
5.	You can now find **Floating IP** of your virtual machine on the **Instances** page.
       <p align="center">
    <img src="../images/picture23.png" alt="A screenshot of a cPouta dashboard" class="guide-screenshot" />
    </p>