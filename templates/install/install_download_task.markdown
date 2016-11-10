<!--Multi-tasks can be used to introduce a process where each child task is required, or to group a set of similar tasks.-->

## Download and Verify Puppet Enterprise Installation Package

The following explains how to download and verify the Puppet Enterprise installation package.

The lastest versions of Puppet Enterprise are available for download from our website. The downloads include the full PE installation tarball and a GPG signature (.asc) file to verify authenticity. 

### Download Puppet Enterprise

The following steps explain how to download PE. PE is distributed in packages specific to your OS version and architecture.

1. Choose the appropriate tarball to [Download](http://info.puppetlabs.com/download-pe.html) the current version of Puppet Enterprise. 

   |      Filename ends with...        |                     Will install on...                       |
|-----------------------------------|-----------------------------------------------------|  |
| `-el-<version and arch>.tar.gz`      | RHEL, CentOS, Scientific Linux, or Oracle Linux  |
| `-ubuntu-<version and arch>.tar.gz`  | Ubuntu LTS                                       |
| `-sles-<version and arch>.tar.gz`    | SLES                                             |

2. Continue to the next task to verify the installation package.
   

### Verify the installation package

The following explains how to import the Puppet public key and run a cryptographic verification of the PE installation package you downloaded. 

Before you begin:

You'll need to have GnuPG installed. You'll also need the GPG signature (.asc file) that you downloaded with the PE installation package.

1. Import the Puppet public key.

   ~~~
   wget -O - https://downloads.puppetlabs.com/puppet-gpg-signing-key.pub | gpg --import
   ~~~
   
2. Print the fingerprint of the Puppet key.

   ~~~
   gpg --fingerprint 0x7F438280EF8D349F
   ~~~
   
   You should see an exact match of the fingerprint of our key, which is printed on the verification.
   
   ~~~
   Primary key fingerprint: 6F6B 1550 9CF8 E59E 6E46  9F32 7F43 8280 EF8D 349F
   ~~~
   
3. Verify the release signature of the installation package.

   ~~~
   $ gpg --verify puppet-enterprise-<version>-<platform>.tar.gz.asc
   ~~~
   
   The result should be similar to the following:
   
   ~~~
   gpg: Signature made Tue 18 Sep 2016 10:05:25 AM PDT using RSA key ID EF8D349F
   gpg: Good signature from "Puppet, Inc. Release Key (Puppet, Inc. Release Key)"
   ~~~
   
   **Note:** When you verify the signature but do not have a trusted path to one of the signatures on the release key, you will see a warning similar to the following:
   
   ~~~
   Could not find a valid trust path to the key.
        gpg: WARNING: This key is not certified with a trusted signature!
        gpg:          There is no indication that the signature belongs to the owner.
   ~~~
   
   This warning is generated because you have not created a trust path to certify who signed the release key; it can be ignored.

* * *