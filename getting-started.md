---
layout: blog_section
title: Getting Started
permalink: /getting-started/
---

The CloudRouter project aims to provide a variety of cloud-ready distribution formats, including disk images, Docker images and OSv images. The CloudRouter 1.0 beta release is currently available as a pre-configured disk image. To install it, follow the instructions below.

**Download**

Two CloudRouter 1.0 Beta images are available: minimal and full. The minimal image includes the Fedora 20 base with updates applied and the CloudRouter repo pre-configured. The full image also includes several pre-installed packages to support software-defined interconnect, such as Bird, Quagga, and OpenDaylight.

<table style="border-spacing: 20px; border-collapse: separate;">
    <tbody>
        <tr>
            <th>Version</th>
            <th>x86_64 Image</th>
            <th>Image Checksum</th>
            <th>Manifest</th>
        </tr>
        <tr>
            <td>Minimal</td>
            <td><a href="{{ site.baseurl }}/repo/beta/images/CloudRouter-Beta-Minimal-20150224.x86_64.raw.xz">Download</a> 399 MB</td>
            <td><a href="{{ site.baseurl }}/repo/beta/images/CloudRouter-Beta-Minimal-20150224.checksum.txt">Download</a></td>
            <td><a href="{{ site.baseurl }}/repo/beta/images/CloudRouter-Beta-Minimal-20150224.manifest.txt">Download</a> 6 KB</td>
        </tr>
        <tr>
        <td>Full</td>
            <td><a href="{{ site.baseurl }}/repo/beta/images/CloudRouter-Beta-Full-20150224.x86_64.raw.xz">Download</a> 883 MB</td>
            <td><a href="{{ site.baseurl }}/repo/beta/images/CloudRouter-Beta-Full-20150224.checksum.txt">Download</a></td>
            <td><a href="{{ site.baseurl }}/repo/beta/images/CloudRouter-Beta-Full-20150224.manifest.txt">Download</a> 11 KB</td>
        </tr>
    </tbody>
</table>


**Install**

<ul>
<li>CloudRouter can be run on a variety of cloud hosts. For local testing purposes, 
the KVM hypervisor with virt-manager is recommended. To install the image using virt-manager, follow these steps:</li>
</ul>

* Uncompress the image:

<pre>$ unxz CloudRouter-Beta-Full-20150224.x86_64.raw.xz</pre>

* Verify that the SHA-512 checksum is correct:

<pre>$ sha512sum CloudRouter-Beta-Full-20150224.x86_64.raw.xz
0103ec161bf02f97807c38f832d86bc9196c4a403e0cb5db918303ea6d175e21e437d80644b64670edac7524be7272ed96badfa6db2fb12ec5fac46c5f6841ff  CloudRouter-Beta-Full-20150224.x86_64.raw.xz</pre>

* Create a new virtual machine in virt-manager. When prompted, select the &#8220;Import existing disk image&#8221; option. Select CloudRouter-Beta-20150209.x86_64.raw as the disk image. Alternatively, use virsh as shown in [this video](http://youtu.be/ISUJaYv0hg8).
* Select appropriate memory and CPU resources. 2048MB memory and 2 vCPUs are recommended.
* Start the virtual machine.

At this point you have CloudRouter running, but cannot login. For enhanced security, the CloudRouter image ships without any default credentials. The default &#8220;fedora&#8221; user is inherited from Fedora, but no password is set. To set a password, you must create a metadata ISO image.

* Create a metadata ISO based on the instructions in [this blog post](https://www.technovelty.org//linux/running-cloud-images-locally.html). Alternatively, a pre-built metadata ISO is [available here](http://cloudrouter.org/repo/beta/images/cr-init.iso). This ISO sets the fedora user&#8217;s password to &#8220;CloudRouter&#8221;. **DO NOT** use this ISO in production, it is strictly for test and demonstration purposes.
* In virt-manager, attach the metadata ISO to the CloudRouter VM as a CDROM storage device.
* Reboot your VM and login. Enjoy!

**Next Steps**

CloudRouter 1.0 beta is based on the [Fedora 20 cloud image](https://getfedora.org/en/cloud/), and includes a distribution of OpenDaylight Helium SR2. For information on installing and running OpenDaylight on CloudRouter, see the [Running OpenDaylight](http://wiki.cloudrouter.org/index.php/Running_OpenDaylight) wiki page. For more details on using OpenDaylight, see the upstream [OpenDaylight Getting Started Guide](http://www.opendaylight.org/resources/getting-started-guide).
