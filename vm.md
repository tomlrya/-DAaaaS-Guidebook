#Using your Cloud VM
---
##Creating a VM
A GEO Virtual Machine will be created for you and you will not have permission to create a GEO-VM. 

See the [FAQ](faq.md) if you need to make changes to your virtual machine.

!!!info
    Depending on your project, you *may* have the ability to create a *standard* virtual machine via the CAE **[link needed]**, or create a workspace in the AAW**[link needed]**.



---

##Finding a VM
From ______ page select **Overview**, scroll down until you see your VM under **My virtual machines**. Click on your VM to access its **Overview** page.  

---

## Start Your Virtual Machine

1. From the **Overview** page for your VM, click on the **Start** button.  

    ![VM Start Button](images/VMStartButton.png)  

2. It takes a few minutes for your VM to start up. Monitor its startup progress by selecting the Notifications icon at the top right of the window.   

    ![Start Notification](images/VMRestartNotification.png)  

---

## Connect To Your Virtual Machine

1. From the **Overview** page for your VM, click on the **Browser connect** button (if you do not see a **Browser connect** button you might have to click on the **Connect** button and then choose **Bastion** from the dropdown menu).

    ![Browser Connect Button](images/VMBrowserConnect.png)    

2. Ensure the *Open in new window* checkbox is selected, enter the Username and Password that you used when you created your VM, and click on the **Connect** button. Your VM should open in a new browser tab.

    **Note** : By default, the **Ubuntu** virtual machine opens in Terminal mode. You can access the GUI of your Ubuntu machine from a Windows machine using [X2Go](https://docs.microsoft.com/en-us/azure/machine-learning/data-science-virtual-machine/dsvm-ubuntu-intro#x2go).

    **Note** : After attempting to login for the first time, an error may appear that a popup blocker is preventing a new window to open. To disable it, an icon will pop up on the browser's search bar, select the button and click **always allow**. 

    ![Allow PopUps](images/VMPopUp.png)

---
   
## Stop Your Virtual Machine

Virtual machines only incur costs while they are running. You should shut down your virtual machine when not in use to prevent unneccessary charges.

1. From the **Overview** page for your VM, click on the **Stop** button.  

    ![VM Stop Button](images/VMStopButton.png)  

---

##Common Errors & Fixes
|Error||Solution|
|----||----|
|![error1](images/error_bastion_falseStart.png)||Your VM is still starting; wait a minute and try again|
|![error2](images/error_loginFailed.png)||You likely entered the VM username or password incorrectly, try again.|
|![error3](images/error_bastion.png)||You are experiancing some nextwork latency; this usually resolves itself. If not, try restarting your VM|
|place||holder|



##Tips

:maple_leaf: Using keyboard shortcuts while connected to a VM may not result in the same action as expected. (i.e. *ctrl + z* will close your main broswer window, not the VM browser window)

:maple_leaf: VMs have an auto-shutdown time of 7pm est. (this can be adjusted upon request)

:maple_leaf: [Moving the taskbar](https://support.microsoft.com/hr-hr/topic/how-to-move-the-windows-taskbar-from-its-default-position-or-reset-it-to-its-default-position-71e48b52-9373-191a-d3e8-78fe78419302) to the top or side of the VM will help differentiate between your OZ-PC and VM workspace.