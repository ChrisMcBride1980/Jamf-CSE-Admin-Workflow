# Jamf-CSE-Admin-Workflow
Admin Model for seperation of accounts to pass Cyber Security + certification
This workflow creates a new admin user account with a random password.  The user will be prompted after 15 minutes and asked if the account is still needed.

Create a policy to install the REMOVEUSER2 package (you may want to sign this package with your own certs) and under files and processes add the following command in the execute tab to create a launch daemon /usr/local/bin/jamf scheduledTask -command "/usr/local/bin/REMOVEUSER1.sh" -name Remove-User3 -runAtLoad -user root -startDelay 900
Scope this policy to any machine you plan to use this workflow.

Create another policy and add the remove user script and give the script a custom trigger of uofgremoval.  Scope this policy to any device you plan to use with this workflow.

Create a self service policy and add the create admin account script.  Remember to change the varriable to whatever you wish the name of your account to be.  Set the policy to run offline, when the account is created the script generates a randome password and displays a swift dialog message to the user with the new accounts password and username. Scope this policy to any machine you plan to use for this workflow.
