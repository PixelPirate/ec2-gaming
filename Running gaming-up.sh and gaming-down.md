*Copy of an [article](https://www.evernote.com/shard/s467/sh/94042f32-9b11-45f7-a95a-1a653fc5988b/d9a81d9cb608b78e) by [Matt Marino](https://twitter.com/Ephs05msm)*

# Running gaming-up.sh and gaming-down.sh on Windows

## EC2 Gaming (per lg.io): Running gaming-up.sh and gaming-down.sh on Windows

1. Install [Cygwin](https://www.evernote.com/OutboundRedirect.action?dest=https%3A%2F%2Fcygwin.com%2Finstall.html), ensuring the following packages are included:
   1. Developer package group, specifically:
      1. C compiler
      2. Make util
   2. Curl (found in the "Net" package group)
   3. Python (entire package group)
   4. I found it's not necessary to install libusb if prompted by Cygwin during this process

2. Install jq in Cygwin
   1. [Download](https://www.evernote.com/OutboundRedirect.action?dest=https%3A%2F%2Fstedolan.github.io%2Fjq%2Fdownload%2F), being sure to find the tarball in section "From source on Linux, OS X, Cygwin, and other POSIX-like operating systems"
   2. Build it using:
      1. `$ cd "C:\Users\yourfilepathhere\"`
         1. Note: Folder names may not contain spaces or $ make install will fail
      2. `$ ./configure`
      3. `$ make`
      4. `$ make install`

3. Install [Java](http://www.java.com/en/download/) in Windows
   1. Set variables in `C:\cygwin64\home\yourpcname\.bashrc`
      1. ```
         export JAVA_HOME=/cygdrive/c/yourjavainstallpathhere
         
         export PATH=$PATH:$JAVA_HOME/bin
         ```
         
   2. Confirm installation in Cygwin with `$ java -version`
   3. If you've set the environment variable correctly, the output looks something like this:
      1. `java version "1.7.0_45" Java(TM) SE Runtime Environment (build 1.7.0_45-b18) Java HotSpot(TM) Client VM (build 24.45-b08, mixed mode, sharing)`

4. Install AWS Command Line Interface Tools in Cygwin

   ```
   $ curl -O https://bootstrap.pypa.io/get-pip.py
   $ python get-pip.py
   $ pip install awscli
   ```

5. Configure AWS CLI with keys, region, and json output
   1. If necessary, use *$ ec2dre` to list regions
   2. `$ aws configure`
      1. Notably, this would not work unless AWS CLI was installed in Cygwin (as opposed to in Windows)
   3. When you reach the fourth option, output as "json"

6. Once steps 1-5 are complete, running gaming-up.sh and/or gaming-down.sh going forward should only require:
   1. `$ bash "C:\Users\yourfilepathhere\gaming-up/down.sh"`