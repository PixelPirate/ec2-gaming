*Copy of a [Knowledge base entry](http://www.dell.com/support/article/us/en/19/SLN156432/EN) from Dell*

# Disable the windows firewall

## Windows Server - How to Properly Turn Off the Windows Firewall in Windows Server 2008 and Above

While it was common - and sometimes necessary - to stop or disable the Windows Firewall service in Windows Server 2003, this is no longer the case in later versions. In fact, stopping or disabling this service in Windows Server 2008, 2008 R2, or 2012 puts a server in an unsupported configuration. It can also cause numerous network-related issues, as described in [Effects of Stopping or Disabling the Windows Firewall Service in Windows Server 2008 and Above](http://www.dell.com/support/article/SLN156677).

There are still situations in which it is necessary to turn off the firewall, and there are supported methods for doing so that don't involve stopping or disabling the service. In Windows Server 2008 and 2008 R2, the firewall can be turned off using the Windows Firewall with Advanced Security console and netsh commands. Windows Server 2012 allows both of those methods and also offers the Set-NetFirewallProfile Windows PowerShell cmdlet.

To turn off the Windows Firewall using the Windows Firewall with Advanced Security console:

1. Open the Server Manager console.
2. In Windows Server 2008 and 2008 R2, in the left pane, expand `Configuration` and click `Windows Firewall with Advanced Security`.
In Windows Server 2012, select `Windows Firewall with Advanced Security` from the `Tools` menu.
3. In the center pane, click `Windows Firewall Properties`.
4. There are three profile tabs in the properties window, corresponding to the three Windows Firewall profiles (domain, private, and public). In each profile tab, select `Off` from the `Firewall state` dropdown list.
5. Click `OK` to close the firewall properties window.

To turn off the firewall using netsh commands:

1. Open an administrative command prompt.
2. Type `netsh advfirewall set allprofiles state off`.

To turn off the firewall using Windows PowerShell in Windows Server 2012:

1. Open Windows PowerShell.
2. Type `Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled False`.
