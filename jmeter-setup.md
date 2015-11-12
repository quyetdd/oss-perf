This page describes how to install JMeter.

0. <a href="#Provision">Provision JMeter slave machine</a>
0. <a href="#GrantAccess">Grant Access to server</a>
0. <a href="#AccessMachine">Access JMeter slave machine</a>
0. <a href="#Installation">Install jmeter</a>
0. <a href="#InitialRun"> Invoke JMeter UI</a>
1. <a href="#Addons">Install add-ons</a>
0. <a href="#TestFolder">Create run assets folder</a>
0. Ensure enough disk space is available.
1. Periodic archival and clean-up.


<hr />

<a id="Provision">
## Provision JMeter slave machines</a>
JMeter can be made available several ways:

   * Locally on a laptop after direct install, as explained below.
   * Locally running within a virual container such as Vagrant on a laptop.
   * In a PaaS (Platform as a service) cloud under Docker control.
   * In a SaaS service such as what <a target="_blank" href="http://blazemeter.com/">Blazmeter.com</a> provides.

Whereever they are, machines need significant network bandwidth and memory.

Usually several JMeter servers need to be used to generate enough load to stress out an application infrastructure.
So Puppet scripts are useful to save time and avoid mistakes, thus reducing troubleshooting frustrations.

<a id="GrantAccess">
## Grant Access to server</a>

0. The server needs to be setup with LDAP.
1. The SSH certificate for userids need to be installed on the server.
2. Group permissions need to be assigned to each user accessing the machine.


<a id="AccessMachine">
## Access JMeter slave machine</a>
0. If you don't have a SSH UI program,
   open a terminal and type the ip address. For example:

   ```
   ssh 10.28.99.99
   ```

  NOTE: The -X (X11) is not specified because iteraction with the server is not via a UI, only via command-line.

0. If the server is setup with LDAP, input your password.

   
<a id="Installation">
## Installation</a>
On a Mac, use Homebrew:
   
   ```
   brew install jmeter
   ```

On Windows, use Chocolatey:
   
   ```
   cinst jmeter
   ```

On a server, the easiest way is to run JMeter within Docker using
https://hub.docker.com/r/cirit/jmeter/
based on 
https://github.com/cagdascirit/docker-jmeter

<a target="_blank" href="https://plus.google.com/114432111742231285408/posts">
kowalcjZero</a> created a 
<a target="_blank" href="https://www.youtube.com/watch?v=RWkJl4OXTJI&list=PLAUamg5VPF5HAxDQlDVItNLfTBNzhpnW4">
series of videos</a> on JMeter in AWS EC2 and Vagrant box.

On a machine with Node, JMeter can be installed using NPM (Node Package Manager) via a Grunt task:

   * https://www.npmjs.com/package/grunt-jmeter

On Ubunto, see this 7-minute video (from Oct. 2014) about using apt-get:

   * https://www.youtube.com/watch?v=8_lEdaIUZRU

On a CentOS (Linux) machine, see https://www.centos.org/docs/5/html/yum/ (Yellow Update Modified) package manager for Centos.

0. Position to the folder under where JMeter will reside:

   ```
   cd /usr/local/bin
   pwd
   ls
   ```

   Files and folders already there include:
   `chattr.sh  chkwinbind.sh  rename2  showip.sh  winbash`
   
0. Use an internet browser to go to the URL listing bineary installers to download:

   ```
   http://jmeter.apache.org/download_jmeter.cgi
   ```
   
0. Right-click under Binaries to obtain the URL to download (*.zip):

   ![jmeter-download-link](https://cloud.githubusercontent.com/assets/300046/11106627/633db242-888c-11e5-9325-46f7e00a4514.png)

   
0. Create a curl command to download the JMeter zip file:

   ```
   curl -o apache-jmeter-2.13.zip  http://mirrors.koehn.com/apache//jmeter/binaries/apache-jmeter-2.13.zip
   ```
   
   Wait under the download summary shows 100%:
   
   ```
     % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 35.9M  100 35.9M    0     0  1727k      0  0:00:21  0:00:21 --:--:-- 1895k
   ```
   
0. Unzip apache-jmeter-*.zip:

   ```
   unzip apache-jmeter-2.13.zip
   ```

0. Move the files to the JMeter folder:

   ```
   mv apache-jmeter-2.13.zip
   ```

<a id="InitialRun">
### Invoke JMeter UI</a>
To verify whether the program was installed in a way that can be invoked, invoke it:

0. Position the present active directory to JMeter's bin folder:

  ```
  cd bin
  ```

0. Invoke the shell command:

  ```
  sh jmeter
  ```

  The first time response:
  
  ```
java.util.prefs.FileSystemPreferences$1 run
INFO: Created user preferences directory.
  ```
  

  If this appears:
  
  ```
An error occurred: 
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
  ```
  
  Type this on the main display before trying again:

  ``
export DISPLAY=:0.0
  ```
  
  An error occurred: Can't connect to X11 window server using ':0.0' as the value of the DISPLAY variable.
  
   NOTE: JMeter runs from the terminal window. Destroy the terminal window and JMeter GUI will go away too.

<a id="TestFolder">
## Create run assets folder</a>
0. To ensure that jmeter can be invoked from this data folder, add it to the end of the server's program path:

   ```
   echo $PATH
   ```
   
   The response are paths separated by a colon:
   
   `/usr/lib64/qt-3.3/bin:/usr/local/bin:/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/sbin:/home/CONCUR/wmar/bin`

0. Since root access is necessary:

   ```
   su
   ```

0. Add the JMeter path obtained in the previous step:

   ```
   echo 'pathmunge /usr/local/bin/jmeter' > /etc/profile.d/custompath.sh
   ```

0. Make the new file executable:

   ```
   chmod +x /etc/profile.d/custompath.sh
   ```
   
0. Type this command, including the period and space, to reload profile settings and add the directory to the path:
   
   ```
   . /etc/profile
   ```

0. If you don't already have one, create a workspace folder (and not necessary named ws under Users home):

   ```
   cd ~/
   pwd
   mkdir ws
   cd ws
   ```

0. Under the workspace folder, create a folder to all jmeter tests:

   ```
   mkdir jmeter
   cd jmeter
   ```

0. Verify:

   ```
   cd ~/ws/jmeter
   ls
   ```

0. Verify jmeter can be invoked from a data folder:

   ```
   jmeter -version
   ```

```
log_file=jmeter.log java.io.FileNotFoundException: jmeter.log (Permission denied)
[log_file-> System.out]
2015/11/11 14:29:25 INFO  - jmeter.util.JMeterUtils: Setting Locale to en_US 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: Loading user properties from: /usr/local/Cellar/jmeter/2.13/libexec/bin/user.properties 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: Loading system properties from: /usr/local/Cellar/jmeter/2.13/libexec/bin/system.properties 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: Copyright (c) 1998-2015 The Apache Software Foundation 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: Version 2.13 r1665067 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: java.version=1.8.0_60 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: java.vm.name=Java HotSpot(TM) 64-Bit Server VM 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: os.name=Mac OS X 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: os.arch=x86_64 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: os.version=10.10.5 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: file.encoding=UTF-8 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: Default Locale=English (United States) 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: JMeter  Locale=English (United States) 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: JMeterHome=/usr/local/Cellar/jmeter/2.13/libexec 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: user.dir  =/usr/local/bin 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: PWD       =/usr/local/bin 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: IP: 10.2.41.166 Name: 15mbp-10681 FullName: 10.2.41.166 
2015/11/11 14:29:25 INFO  - jmeter.gui.action.LookAndFeelCommand: Using look and feel: com.apple.laf.AquaLookAndFeel [Mac OS X, System] 
2015/11/11 14:29:25 INFO  - jmeter.JMeter: Loaded icon properties from org/apache/jmeter/images/icon.properties 
2015/11/11 14:29:27 INFO  - jmeter.engine.util.CompoundVariable: Note: Function class names must contain the string: '.functions.' 
2015/11/11 14:29:27 INFO  - jmeter.engine.util.CompoundVariable: Note: Function class names must not contain the string: '.gui.' 
2015/11/11 14:29:27 INFO  - jmeter.util.BSFTestElement: Registering JMeter version of JavaScript engine as work-round for BSF-22 
2015/11/11 14:29:28 INFO  - jmeter.protocol.http.sampler.HTTPSamplerBase: Cannot find .className property for htmlParser, using default 
2015/11/11 14:29:28 INFO  - jmeter.protocol.http.sampler.HTTPSamplerBase: Parser for text/html is  
2015/11/11 14:29:28 INFO  - jmeter.protocol.http.sampler.HTTPSamplerBase: Parser for application/xhtml+xml is  
2015/11/11 14:29:28 INFO  - jmeter.protocol.http.sampler.HTTPSamplerBase: Parser for application/xml is  
2015/11/11 14:29:28 INFO  - jmeter.protocol.http.sampler.HTTPSamplerBase: Parser for text/xml is  
2015/11/11 14:29:28 INFO  - jmeter.protocol.http.sampler.HTTPSamplerBase: Parser for text/vnd.wap.wml is org.apache.jmeter.protocol.http.parser.RegexpHTMLParser 
2015/11/11 14:29:28 INFO  - jmeter.gui.util.MenuFactory: Skipping org.apache.jmeter.protocol.http.control.gui.WebServiceSamplerGui 
2015/11/11 14:29:28 INFO  - jmeter.gui.util.MenuFactory: Skipping org.apache.jmeter.protocol.http.modifier.gui.ParamModifierGui 
2015/11/11 14:29:28 INFO  - jorphan.exec.KeyToolUtils: keytool found at 'keytool' 
2015/11/11 14:29:28 INFO  - jmeter.protocol.http.proxy.ProxyControl: HTTP(S) Test Script Recorder SSL Proxy will use keys that support embedded 3rd party resources in file /usr/local/Cellar/jmeter/2.13/libexec/bin/proxyserver.jks 
2015/11/11 14:29:28 INFO  - jmeter.samplers.SampleResult: Note: Sample TimeStamps are START times 
2015/11/11 14:29:28 INFO  - jmeter.samplers.SampleResult: sampleresult.default.encoding is set to ISO-8859-1 
2015/11/11 14:29:28 INFO  - jmeter.samplers.SampleResult: sampleresult.useNanoTime=true 
2015/11/11 14:29:28 INFO  - jmeter.samplers.SampleResult: sampleresult.nanoThreadSleep=5000 
```


<a id="Addons">
## Add-ons</a>
For easier invocation, the
<a target="_blank" href="https://wiki.jenkins-ci.org/display/JENKINS/Performance+Plugin">
Performance Plugin</a> from https://github.com/jenkinsci/performance-plugin.

For managed devops:
https://xebialabs.com/community/webinars/dzone-presents-seamless,-scalable-test-management-using-jenkins-and-xebialabs-software/

   * Xebialabx.com
   * https://www.youtube.com/channel/UC3XtKwSYyeQfGirLL_IW_Qw

<a id="JMeterGlobals">
## Global Properties</a>
0. To verify where Jmeter is installed:

   ```
   which jmeter
   ```
   
   The response (on a Mac):
   
   `/usr/local/bin/jmeter`
   
   Alternately, if this appears:
   
   `/usr/bin/which: no jmeter in (/usr/lib64/qt-3.3/bin:/usr/local/bin:/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/sbin:/home/CONCUR/wmar/bin)`

0. In the bin folder where Jmeter was installed:

   ```
   cd /usr/local/bin
   ```

0. Use a text editor to open file **jmeter.properties**.

   PROTIP: If github is used, this file should be copied from github to the installer.

0. Specify settings as appropriate:

   * **remote_hosts** - remote JMeter hosts, separated by commas.
   * **not_in_menu**	- With the help of this you can customize your JMeter by allowing only those components to display which you want to by listing their classname or their class label.
   * **user.properties** - Addition JMeter properties are contained in this file and are added before the -q and -J options are processed and after the initial property file.
   * **xml.parser** - The default value is: org.apache.xerces.parsers.SAXParser. An implementation can be specified as XML parser.
   * **search_paths** - lists of paths to search JMeter add-on classes by JMeter such as additional samplers which is in addition to the jars kept in  lib/ext directory.
   * **system.properties**	- additional system properties added before the -S and -D options are processed.
   * **user.classpath**	- The path to be searched for utility classes by JMeter in addition to jars kept in lib directory.
   * **ssl.provider** - If built-in Java implementation are not provided, the class can be specified by you for your SSL implementation.

