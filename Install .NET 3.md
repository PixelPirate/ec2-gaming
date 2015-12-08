*Copy of a technet.microsoft.com [article](https://technet.microsoft.com/en-us/library/dn482071.aspx)*

# Install .NET 3.5

## Enable .NET Framework 3.5 by using the Add Roles and Features Wizard

You can use Server Manager to enable .NET Framework 3.5 for a local or remote installation of Windows Server 2012 R2.

### Requirements

* Windows Server 2012 R2 

* Installation media

* Administrator user rights. The current user must be a member of the local Administrators group to add or remove Windows features.

* Target Computers might need network access and rights to use either alternate sources or an Internet connection to use Windows Update.

### Steps

1. In Server Manager, click `Manage` and then select `Add Roles and Features` to start the Add Roles and Features Wizard.

2. On the `Select installation type` screen, select `Role-based or feature-based installation`.

3. Select the target server.

4. On the `Select features` screen, check the box next to `.Net Framework 3.5` Features.

5. On the `Confirm installation selections screen, a warning will be displayed asking `Do you need to specify an alternate source path?. If the target computer does not have access to Windows Update, click the `Specify an alternate source path` link to specify the path to the `\sources\sxs` folder on the installation media and then click `OK`. After you have specified the alternate source, or if the target computer has access to Windows Update, click the `X` next to the warning, and then click `Install`. 

   If you are using Server Manager in Windows Server 2012 to add a role or feature to a remote server, the remote server’s computer account (DOMAIN\ComputerName$) requires access to the alternate source file path because the deployment operation runs in the SYSTEM context on the target server.