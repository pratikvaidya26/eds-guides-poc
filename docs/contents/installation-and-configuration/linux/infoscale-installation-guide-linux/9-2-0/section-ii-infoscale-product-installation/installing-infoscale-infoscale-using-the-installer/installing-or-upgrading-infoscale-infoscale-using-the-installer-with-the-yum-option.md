<?xml version="1.0" encoding="utf-8"?><?workdir /opt/aem/launcher/profiles/ditamaps/ditamap8329419222281724652/PDFProject/contents/installation-and-configuration/linux/infoscale-installation-guide-linux/9-2-0/section-ii-infoscale-product-installation/installing-infoscale-infoscale-using-the-installer?><?workdir-uri file:/opt/aem/launcher/profiles/ditamaps/ditamap8329419222281724652/PDFProject/contents/installation-and-configuration/linux/infoscale-installation-guide-linux/9-2-0/section-ii-infoscale-product-installation/installing-infoscale-infoscale-using-the-installer/?><?path2project ../../?><?path2project-uri ../../?><?path2rootmap-uri ../../?><topic xmlns:ditaarch="http://dita.oasis-open.org/architecture/2005/" xmlns:dita-ot="http://dita-ot.sourceforge.net/ns/201007/dita-ot" class="- topic/topic " ditaarch:DITAArchVersion="1.2" domains="(topic hi-d) (topic ut-d) (topic indexing-d) (topic hazard-d) (topic abbrev-d) (topic pr-d) (topic sw-d) (topic ui-d)" id="installing-or-upgrading-infoscale-infoscale-using-the-installer-with-the--yum-option"><title class="- topic/title ">Installing or upgrading InfoScale InfoScale using the installer with the -yum option</title><body class="- topic/body "><p class="- topic/p ">Starting with InfoScale 8.0, you can use yum commands with Common Product Installer and install or upgrade InfoScale 8.0 running on Red Hat and Oracle Linux.</p><p class="- topic/p ">Yum is a command-line package management tool that you can use for installing, updating, removing, and managing the InfoScale package. Yum performs dependency resolution when install, update, and remove the InfoScale package. Yum can also manage the package from installed repositories in the system or from the InfoScale .rpm packages. The following new options are supported for the installation and upgrade of InfoScale:</p><ul class="- topic/ul "><li class="- topic/li "><p class="- topic/p ">-yum</p></li><li class="- topic/li "><p class="- topic/p ">-matrixpath</p></li><li class="- topic/li "><p class="- topic/p ">-upgradestart</p></li><li class="- topic/li "><p class="- topic/p ">-upgradestop</p><lq class="- topic/lq "><p class="- topic/p "><b class="+ topic/ph hi-d/b ">Note:</b> The new installer options are supported only with InfoScale 8.0. You can perform upgrades from an earlier version to 9.2.0. The supported versions for upgrades are 7.4.1, 7.4.2, and 8.0.</p></lq></li></ul><p class="- topic/p ">Before you begin</p><p class="- topic/p ">Before you begin the configuration of yum, and installation or upgrade of InfoScale, ensure that you:</p><ul class="- topic/ul "><li class="- topic/li "><p class="- topic/p ">Deploy InfoScale in a development or UAT environment first, which is as similar to your production environment as possible. Perform tests in that environment and ensure that there is no incompatibility with your current deployment.</p></li><li class="- topic/li "><p class="- topic/p ">Perform necessary backups and snapshots of your production system and establish a rollback plan.</p></li></ul><p class="- topic/p ">Installation or upgrade</p><p class="- topic/p ">There are two ways of yum based installation or upgrade. You can either use the -yum option with installer, or use direct/manual yum method.</p><p class="- topic/p ">Using the yum option with installer</p><p class="- topic/p ">The following is the syntax and examples for installing InfoScale using the yum installer option. After running any of the following yum installation commands, select the  Install a product  or  Upgrade a product  option from the menu displays by installer script.</p><p class="- topic/p ">Syntax:</p><p class="- topic/p "><codeph class="+ topic/ph pr-d/codeph ">./installer -yum [repo_name | repo_url]</codeph></p><p class="- topic/p ">Example for yum installation with repository name:</p><p class="- topic/p "><codeph class="+ topic/ph pr-d/codeph ">./installer -yum repo-Infoscale92</codeph></p><p class="- topic/p ">Example for yum installation using repository URL:````./installer -yum http://xyz.com/rhel8_x86_64/rpms/``Notes:</p><ul class="- topic/ul "><li class="- topic/li "><p class="- topic/p ">If a repository URL is passed as an argument with the -yum option, you do not need to set the yum repository manually. The CPI installer creates the repository on each node. The repository URL is the base URL that you specify in the repository file while configuring yum repository, and the values for the base URL attribute begins with http://, ftp:/, file:///, or sftp:/</p></li><li class="- topic/li "><p class="- topic/p ">If a repository name is passed as an argument with the -yum option, the CPI installer assumes that the repository is already configured and enabled on the node, hence, you need not to configure the repository. If a repository name is used and the repository has not yet been configured, then the CPI installer exits with an appropriate error.</p></li></ul><p class="- topic/p ">Using -yum and -patch_path options together with -matrixpath</p><p class="- topic/p ">The following is the syntax and examples for performing patch installation or patch upgrade along with GA upgrade of InfoScale with RPM files:</p><lq class="- topic/lq "><p class="- topic/p "><b class="+ topic/ph hi-d/b ">Note:</b> After running any of the following yum installation commands, select the Install a product or upgrade a product option from the menu displayed by installer script.</p></lq><p class="- topic/p ">Syntax:<codeph class="+ topic/ph pr-d/codeph ">./installer -yum [repo_name | repo_url] -patch_path [repo_name | repo_url] -matrixpath</codeph>Example for performing patch installation or patch upgrade<codeph class="+ topic/ph pr-d/codeph ">./installer -yum repo-Infoscale92 -patch_path repo-Infoscale92P -matrixpath /root/patch_matrix</codeph>When you run this command, you need to enter the release matrix data path in the command. You must use the matrixpath option when there is no SORT connectivity on a machine and the -yum and -patch_path options are used together. As installer has pre-checks on the release matrix data, if a correct release matrix data path is not provided, the patch installation or patch upgrade may fail.</p><p class="- topic/p ">Direct or manual yum installation</p><p class="- topic/p ">Ensure that you set the yum repository manually on each node of the cluster before running the yum install command.</p><p class="- topic/p ">For more details on Installing InfoScale InfoScale using yum, refer to the topic:</p><p class="- topic/p ">To install InfoScale RPMs using manual yum method</p><ol class="- topic/ol "><li class="- topic/li "><p class="- topic/p ">Specify each RPM name and its yum equivalent. For example:<codeph class="+ topic/ph pr-d/codeph "># yum install VRTSvlic VRTSperl ... VRTSsfcpi</codeph>1.  Specify all the InfoScale InfoScale RPMs using RPM glob. For example:<codeph class="+ topic/ph pr-d/codeph "># yum install 'VRTS*</codeph>'</p></li><li class="- topic/li "><p class="- topic/p ">Specify the group name if a group is configured for InfoScale InfoScale's RPMs.</p><lq class="- topic/lq "><p class="- topic/p "><b class="+ topic/ph hi-d/b ">Note:</b> Ensure that the specified name is consistent with the one in the xml file. For example, consider the group name usage as ENTERPRISE92: # yum install @ENTERPRISE92 or # yum groupinstall -y ENTERPRISE92.</p></lq></li></ol><p class="- topic/p ">Using Direct or manual yum upgrade</p><p class="- topic/p ">You can upgrade InfoScale by manually configuring yum repositories on each node of a cluster, and then run the yum upgrade command. You need to use the upgradestop and upgradestart options for manual yum upgrade. The following are the syntax and examples:</p><p class="- topic/p ">Syntax for upgradestop:<codeph class="+ topic/ph pr-d/codeph ">/opt/VRTS/install/installer -upgradestop</codeph>Use the upgradestop option before you begin to upgrade InfoScale using the yum upgrade command. This command performs required pre-upgrade checks and backups all the configuration files before the upgrade.</p><p class="- topic/p ">Syntax for upgradestart:<codeph class="+ topic/ph pr-d/codeph ">/opt/VRTS/install/installer -upgradestart</codeph>Use the upgradestart option to start the services after upgrading InfoScale rpms using yum such as starting CVM agents, registering extra types.cf files, and updating protocol version.</p><p class="- topic/p ">To upgrade InfoScale using yum</p><ol class="- topic/ol "><li class="- topic/li "><p class="- topic/p ">Disable all the service groups on a cluster.</p></li><li class="- topic/li "><p class="- topic/p ">Unmount the file system which is not under the VCS control.</p></li><li class="- topic/li "><p class="- topic/p ">Use the following command to disable the dmp native support:<codeph class="+ topic/ph pr-d/codeph "># vxdmpadm settune dmp_native_support=off</codeph>1.  Stop the installer to stop all the services as follows:<codeph class="+ topic/ph pr-d/codeph "># ./installer -upgradestop</codeph>&gt; <b class="+ topic/ph hi-d/b ">Note:</b> The base version for upgradestop is 8.0. You cannot perform direct yum upgrade from earlier versions of InfoScale to 8.0 or later using upgradestop. You may use -stop option with installer, post running./installer -stopcommand. Ensure that all the modules and services are stopped usinglsmodandsystemctlstatus commands and verify the status before proceeding with yum upgrade.</p></li><li class="- topic/li "><p class="- topic/p ">Copy the<codeph class="+ topic/ph pr-d/codeph ">infoscale92.repo</codeph>to<codeph class="+ topic/ph pr-d/codeph ">/etc/yum.repos.d/</codeph>on the YUM client machine from the installation media, or you can manually create the<codeph class="+ topic/ph pr-d/codeph ">.repo file</codeph>using the following steps:</p></li></ol><p class="- topic/p ">i. Create<codeph class="+ topic/ph pr-d/codeph ">.repo</codeph>file using any editor <xref class="- topic/xref " keyref="vi,vim or nano"><?ditaot usertext?></xref> as shown below:<codeph class="+ topic/ph pr-d/codeph "># vi /etc/yum.repos.d/Infoscale92.repo</codeph>ii. After executing the above command insert the following values in the .repo file as follows:```txt
<xref class="- topic/xref " keyref="repo-InfoScale92"><?ditaot usertext?></xref>
name=Repository for InfoScale InfoScale 92
baseurl=file:///\&lt;image_dir\&gt;/rpms/
enabled=1
gpgcheck=1
gpgkey=file:///\&lt;image_dir\&gt;/rpms/RPM-GPG-KEY-veritas-infoscale7</p><codeblock class="+ topic/pre pr-d/codeblock " xml:space="preserve" outputclass="txt">Note: The values for the baseurl attribute can start with``http://, ftp://, or file://.``The URL you choose needs to be able to access the repodata directory. It also needs to access all the InfoScale InfoScale RPMs in the repository that you create or update.
iii. Save and exit the text editor

&gt; **Note:** If you copy the .repo file directly from installation media then you need to update the 'baseurl' and 'gpgkey' entry in/etc/yum.repos.d/Infoscale92.repofor yum repository directory using any text editor.

1.  Run the following commands to refresh the yum repository:

    -``# yum repolist``-``# yum updateinfo``-``# yum grouplist``1.  Run the following command to upgrade InfoScale InfoScale product:``# yum upgrade VRTS*``If OS upgrade is involved and a reboot is required, then upgrade both OS and IS at the same time :``# yum upgrade &lt;--releasever=&lt;version&gt;&gt;``1.  Repeat steps 5 to 8 on each node of the cluster.
1.  After completing all above steps, run the following command to manually generate installer scripts for configuration.``# /opt/VRTS/install/bin/UXRT92/add_install_scripts``1.  Run the following command to manually install the``VRTSrest``package on all the cluster nodes.``# yum install VRTSrest``1.  Run the following command to start:``# /opt/VRTS/install/installer -upgradestart``After successful completion of yum upgrade ensure that cluster is up and running. You may verify the CVM protocol version using``vxdctl protocolversion``command and VCS protocol version as follows:``/opt/VRTS/bin/haclus -value ProtocolNumber``&gt; **Note:** Ensure that you set the yum repository manually on each node of the cluster before running the yum install and upgrade command.

Yum install or upgrade with response files

Yum based install or upgrade can be performed using either menu driven program or response-file.

**Table:**

| Variable | Description | List or Scalar | Mandatory or Optional |
| --- | --- | --- | --- |
| CFG{opt}{yum} | The -yum option is used to define the yum repository path or the repository name to be used for performing yum-based tasks. This option is supported on Red Hat Linux and Oracle Linux only. | Scalar | Optional |
| CFG{opt}{matrixpath} | The -matrixpath option is used to accept a user-specified release matrix data path. | Scalar | Optional |
| CFG{opt}{upgradestop} | The -upgradestop option stops all the drivers and the processes. This option is supported only on Red Hat Linux and Oracle Linux. | Scalar | Optional |
| CFG{opt}{upgradestart} | The -upgradestart option starts all drivers and processes of a product where product is upgraded using yum. The option is supported only on Red Hat Linux and Oracle Linux. | Scalar | Optional |

The following are the sample response files:

Installation using -yum with reponame:```txt
\#
\# Configuration Values:
\#
our %CFG;
$CFG{accepteula}=1;
```txt

```txt

    $CFG{opt}{install}=1;
$CFG{opt}{yum}="repo-InfoScale92";
$CFG{prod}="ENTERPRISE92";
$CFG{systems}=[ "dl380g10-10-vip17" ];

1;

```txt

Installation using -yum with repo URL:```txt
#

## Configuration Values

#
our %CFG;

$CFG{accepteula}=1;

```txt
```txt

$CFG{opt}{install}=1;
$CFG{opt}{yum}="http://xyz.com/rhel8_x86_64/rpms/";
$CFG{prod}="ENTERPRISE92";
$CFG{systems}=[ "dl380g10-10-vip17" ];

1;

```txt
Installation using -yum, -matrixpath and -patch_path:```txt
\#
\# Configuration Values:
\#
our %CFG;

$CFG{accepteula}=1;
```txt

```txt

$CFG{opt}{install}=1;
$CFG{opt}{matrixpath}="/root/patch_matrix/";
$CFG{opt}{patch_path}="repo-InfoScale92P";
$CFG{opt}{yum}="repo-InfoScale92";
$CFG{prod}="ENTERPRISE92";
$CFG{systems}=[ "dl380g10-10-vip17" ];

1;

```txt

&gt; **Note:** For all upgrade operations, you need to enter the newly added options wherever required. Rest of the configuration values are same as per traditional installation and upgrade.

Upgradestop before manual yum upgrade:```txt
#

## Configuration Values

#
our %CFG;

$CFG{opt}{gco}=1;
$CFG{opt}{stop}=1;
$CFG{opt}{upgradestop}=1;
$CFG{opt}{vr}=1;
$CFG{prod}="ENTERPRISE92";
$CFG{systems}=[ "dl380g10-10-vip17","dl380g10-10-vip18" ];
$CFG{vcs_allowcomms}=1;

1;

```txt
Upgradestart after manual yum upgrade:```txt

\#
\# Configuration Values
\#
our %CFG;

$CFG{opt}{gco}=1;
$CFG{opt}{start}=1;
$CFG{opt}{upgradestart}=1;
$CFG{opt}{vr}=1;
$CFG{prod}="ENTERPRISE92";
$CFG{systems}=[ "dl380g10-10-vip14" ];
$CFG{vcs_allowcomms}=1;

1;</codeblock><p class="- topic/p ">More Information</p><p class="- topic/p "><xref class="- topic/xref " href="../installing-infoscale-infoscale-using-operating-system-specific-methods/installing-infoscale-using-yum.md" dita-ot:orig-format="markdown" format="dita" type="topic"><?ditaot usertext?>Installing InfoScale using yum</xref></p></body></topic>