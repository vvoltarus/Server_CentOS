### Setup ###

 **Step 1 - Installation.**  First install CentOS iso on your VM machine. https://www.centos.org/download/

**Step 2 - Changing password.**  On the first connection to machine after installation, suggest to chande password of user:

<code>passwd user_name</code>

=== Note : Your username ===
<br>

**Step 3 - Setup root privileges to new user.** We need to give priveleges to our new user that we created.
To do that, type this command:
<code>/usr/sbin/visudo</code>
<br>
#### Allow root to run any commands anywhere ####
root      ALL=(ALL)        ALL

newuser   ALL=(ALL)        ALL

*Note: If you dont have nano editor, you can hit 'a', add text in file after that hit ESC.
To save hold Shift +ZZ and you good to go.*
<br>

**Step 4 - Change SSH default port and disable root login.**  
Type  nano /etc/ssh/sshd_config.

Then fine following lines: 
<code> #port 22 </code>

Remove the # symbol and change the “22” (it is default port) to to any number between 1025 and 65536, For example is port 22000. Example: 1028
 <br>
 
Next, also find: 
<code> #PermitRootLogin yes </code>

Remove the # symbol and change yes to no
<br>

And this line as well: <code> #UseDNS yes </code>

Remove the # symbol and change yes to no
<br>

Don’t close editor just yet, now proceed to the next step:
<br>

**Step 5 - Allow new user to login via SSH to your server.** Simply add this line in the very bottom of that file: <code> AllowUsers newuser </code>


**Step 6 - Reload SSH Service.**

<code> systemctl reload sshd </code>
