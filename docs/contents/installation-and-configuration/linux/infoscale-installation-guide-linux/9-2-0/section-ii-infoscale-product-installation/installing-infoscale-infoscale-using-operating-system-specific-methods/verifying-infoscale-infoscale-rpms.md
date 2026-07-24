<?xml version="1.0" encoding="utf-8"?><?workdir /opt/aem/launcher/profiles/ditamaps/ditamap8329419222281724652/PDFProject/contents/installation-and-configuration/linux/infoscale-installation-guide-linux/9-2-0/section-ii-infoscale-product-installation/installing-infoscale-infoscale-using-operating-system-specific-methods?><?workdir-uri file:/opt/aem/launcher/profiles/ditamaps/ditamap8329419222281724652/PDFProject/contents/installation-and-configuration/linux/infoscale-installation-guide-linux/9-2-0/section-ii-infoscale-product-installation/installing-infoscale-infoscale-using-operating-system-specific-methods/?><?path2project ../../?><?path2project-uri ../../?><?path2rootmap-uri ../../?><topic xmlns:ditaarch="http://dita.oasis-open.org/architecture/2005/" xmlns:dita-ot="http://dita-ot.sourceforge.net/ns/201007/dita-ot" class="- topic/topic " ditaarch:DITAArchVersion="1.2" domains="(topic hi-d) (topic ut-d) (topic indexing-d) (topic hazard-d) (topic abbrev-d) (topic pr-d) (topic sw-d) (topic ui-d)" id="verifying-infoscale-infoscale-rpms"><title class="- topic/title ">Verifying InfoScale InfoScale RPMs</title><body class="- topic/body "><p class="- topic/p ">InfoScale RPMs include digital signatures that are used to verify their authenticity. If you want to install the RPMs manually, you must first import the keys.</p><p class="- topic/p ">To import keys</p><ol class="- topic/ol "><li class="- topic/li "><p class="- topic/p ">Import the InfoScale GPG key to verify InfoScale packages:</p></li></ol><p class="- topic/p "><codeph class="+ topic/ph pr-d/codeph "># rpm --import RPM-GPG-KEY-veritas-infoscale7</codeph></p><ol class="- topic/ol "><li class="- topic/li "><p class="- topic/p ">Display the list of InfoScale keys installed for RPM verification:</p></li></ol><p class="- topic/p "><codeph class="+ topic/ph pr-d/codeph "># rpm -q gpg-pubkey --qf '%{name}-%{version}-%{release} --&gt;%{summary}\n' | grep InfoScale</codeph></p><ol class="- topic/ol "><li class="- topic/li "><p class="- topic/p ">Display the fingerprint of the InfoScale key file:</p></li></ol><p class="- topic/p "><codeph class="+ topic/ph pr-d/codeph "># gpg --quiet --with-fingerprint ./RPM-GPG-KEY-InfoScale-infoscale7</codeph></p><p class="- topic/p ">Sample output:</p><codeblock class="+ topic/pre pr-d/codeblock " xml:space="preserve" outputclass="txt">Key fingerprint = C031 8CAB E668 4669 63DB  C8EA 0B0B C720 A17A 604B</codeblock><p class="- topic/p ">To display details about the installed InfoScale key file</p><ul class="- topic/ul "><li class="- topic/li "><p class="- topic/p ">Use the <codeph class="+ topic/ph pr-d/codeph ">rpm -qi</codeph> command followed by the output from the previous command:</p></li></ul><p class="- topic/p "><codeph class="+ topic/ph pr-d/codeph "># rpm -qi &lt;gpg-pubkey-file&gt;</codeph></p><p class="- topic/p ">Alternatively, you can use the following command:</p><p class="- topic/p "><codeph class="+ topic/ph pr-d/codeph "># rpm -qi </codeph>rpm -q gpg-pubkey --qf '%{name}-%{version}-%{release} --&gt; %{summary}\n' | awk '/Veritas/ { print $1 }'``To check the GnuPG signature of an RPM file</p><ul class="- topic/ul "><li class="- topic/li "><p class="- topic/p ">After importing the builder's GnuPG key, run the following command:<codeph class="+ topic/ph pr-d/codeph "># rpm -K &lt;rpmPackageName&gt;</codeph>If the signature of the package is verified, and it is not corrupt, the following message is displayed:```txt
md5 gpg OK</p></li></ul><codeblock class="+ topic/pre pr-d/codeblock " xml:space="preserve" outputclass="txt">To verify the signature for all InfoScale InfoScale RPMs
-  Run the following command:``# for i in *.rpm; do rpm -K $i; done``Sample outptut:```txt
VRTSamf-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSaslapm-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTScavf-7.4.2.0000-GENERIC.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTScps-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSdbac-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSdbed-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSdocker-plugin-1.4-Linux.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSfssdk-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSgab-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSglm-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSgms-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSllt-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSodm-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSperl-5.30.0.0-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSpython-3.7.4.1-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSsfcpi-7.4.2.0000-GENERIC.noarch.rpm: rsa sha1 (md5) pgp md5 OK
VRTSsfmh-7.4.2.0000_Linux.rpm: rsa sha1 (md5) pgp md5 OK
VRTSspt-7.4.2.0000-RHEL7.noarch.rpm: rsa sha1 (md5) pgp md5 OK
VRTSvbs-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSvcs-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSvcsag-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSvcsea-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSvcsnr-7.4.2.0000-GENERIC.noarch.rpm: rsa sha1 (md5) pgp md5 OK
VRTSvcswiz-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSveki-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSvlic-4.01.74.004-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSvxfen-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSvxfs-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK
VRTSvxvm-7.4.2.0000-RHEL7.x86_64.rpm: rsa sha1 (md5) pgp md5 OK</codeblock></body></topic>