*Stackoverflow [answer](http://stackoverflow.com/questions/614766/run-a-script-on-windows-startup-without-a-user-logged-on/617313#617313) from [TristanK](http://stackoverflow.com/users/74103/tristank)*

# Initialize Z drive properly on boot

**GPEDIT.MSC** (Start, Run, GPEdit.msc) is the Group Policy editing console, and runs against the local computer's Group Policy store when it's used directly, so it's useful for setting local-only parameters.

When using Active Directory, the same interface is used to edit policy objects, so the same settings are available across a bunch of machines.

Windows 2000 and above offer a computer **Startup Scripts** collection in the policy editor:

* Computer Settings -> Windows Settings -> Scripts (Startup/Shutdown)

There's an equivalent logon script area (i.e. after computer startup, when a user logs on) in the User configuration bit.

The computer startup scripts run in the computer context, i.e. LocalSystem, as you noted, so they often can't access network drives which require a certain user or group membership to work, and so on. When computers access the network, they generally (with exceptions) use their MACHINENAME$ account.

A startup script is a quick and easy way of getting a process running when the machine boots.

The computer startup process will be affected by the time it takes to run the program, though, so you might want to ensure you call it with the START command from a batch file, or specifying not to wait for the executable to complete in whatever script language you use. (the key point there is: run the script asynchronously unless it's critical, or doesn't need to be run asynchronously cos it will always take no time at all. Long boots = unhappy users).

Using a Win32 Service is an alternative option - you can use the `SRVANY` utility from the Resource Kit to "service-ify" pretty much any executable. VS.Net 2002 and later also let you build a managed service directly.

And **Task Scheduler** gets much more capable as of Vista/2008, able to run scripts at startup, on idle, and/or when certain other conditions are met: it's pretty cool! Scheduled Tasks has the possible advantage of being able to specify the user account under which the task runs, if that's important to you.

Caveat Scriptor: http://support.microsoft.com/kb/256320

Run Startup Scripts Asynchronously: http://msdn.microsoft.com/en-us/library/ms811602.aspx

Vista Task Scheduler (what's new): http://technet.microsoft.com/en-us/appcompat/aa906020.aspx

---

`Computer Settings/Configuration --> Windows Settings --> Scripts` This can be found by opening the Local Group Policy Editor, since no one explained how to even get to this window. -- [liltitus27](http://stackoverflow.com/users/1322243/liltitus27)