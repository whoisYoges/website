+++
title = "Create and delete GPG keypair | Introduction to GnuPG "
date = "2022-10-30"
updated = "2022-12-07"
page_template = "page.html"
draft = false
description = "GnuPG, popularly known as GPG, is an extremely versatile tool, being widely used as the industry standard for encryption of things like emails, messages, files, or just anything you need to send to someone securely."
[extra]
opengraph = "/assets/images/blogs/create-and-delete-gpg-key-pair/Gnupg.png"
gotoTop = true
copy_code = true
shareable = true
keywords = "create delete and share gpg key pair, create gpg key pair, create gpg rsa key-pair, gpg delete key pair, create gpg signing key, create gpg keyring, delete gpg key pair, create delete and share gpg key pair aws, create delete and share gpg key pair authentication, create delete and share gpg key pair aws cli, create delete and share gpg key pair and password, create delete and share gpg key pair and csr, create delete and share gpg key pair and certificate, create delete and share gpg key pair and try again, gpg create private and public key, gpg create key pair, gpg create a key, create delete and share gpg key pair by default, create delete and share gpg key pair bitbucket, create delete and share gpg key pair best practices, create delete and share gpg key pair between regions, create delete and share gpg key pair boto3, gpg delete-keys, gpg delete secret key, create delete and share gpg key pair command line, create delete and share gpg key pair cli, create delete and share gpg key pair cloudformation, create delete and share gpg key pair credentials, create delete and share gpg key pair change, create delete and share gpg key pair download, create delete and share gpg key pair denied, create delete and share gpg key pair details, create delete and share gpg key pair does not exist, create delete and share gpg key pair does not work, create delete and share gpg key pair download again, delete gpg secret key, delete gpg keys, gpg create default secret key, gpg create detached signature, create delete and share gpg key pair example, create delete and share gpg key pair ec2, create delete and share gpg key pair error, create delete and share gpg key pair empty, create delete and share gpg key pair ec2 instance, gpg create encryption key, gpg create new key pair, edit gpg key, create delete and share gpg key pair failed, create delete and share gpg key pair file, create delete and share gpg key pair from aws, create delete and share gpg key pair for ec2 instance, create delete and share gpg key pair fingerprint, gpg delete key from keyring, create delete and share gpg key pair github, create delete and share gpg key pair gitlab, create delete and share gpg key pair git, create delete and share gpg key pair greyed out, create delete and share gpg key pair gcp, create delete and share gpg key pair generation, create delete and share gpg key pair generation algorithm, create delete and share gpg key pair generation linux, gpg delete private key, create delete and share gpg key pair how, create delete and share gpg key pair hash, create delete and share gpg key pair help, create delete and share gpg key pair htaccess, create delete and share gpg key pair has failed, create delete and share gpg key pair in linux, create delete and share gpg key pair in mac, create delete and share gpg key pair in windows, create delete and share gpg key pair id, create delete and share gpg key pair in aws, create delete and share gpg key pair java, create delete and share gpg key pair jenkins, create delete and share gpg key pair json, create delete and share gpg key pair jwt, create delete and share gpg key pair javascript, gpg delete keys, gpg decrypt and delete original file, create delete and share gpg key pair key, create delete and share gpg key pair kubernetes, create delete and share gpg key pair key pair, create delete and share gpg key pair keychain, create delete and share gpg key pair linux, create delete and share gpg key pair locally, create delete and share gpg key pair linux command line, create delete and share gpg key pair mac, create delete and share gpg key pair macos, gpg delete a key, create delete and share gpg key pair name, create delete and share gpg key pair not working, create delete and share gpg key pair not found, create delete and share gpg key pair name ec2, create delete and share gpg key pair new, create delete and share gpg key pair on mac, create delete and share gpg key pair openssl, create delete and share gpg key pair online, create delete and share gpg key pair on windows, create delete and share gpg key pair on ec2 instance, share gpg key, how to delete a gpg key, create delete and share gpg key pair password, create delete and share gpg key pair python, create delete and share gpg key pair private key, create delete and share gpg key pair permission, create delete and share gpg key pair public key, create delete and share gpg key pair putty, create delete and share gpg key pair pem, creating delete and share gpg key pair perfect, pgp delete key pair, create delete and share gpg key pair questions, create delete and share gpg key pair quizlet, create delete and share gpg key pair quora, create delete and share gpg key pair qradar, create delete and share gpg key pair qr, create delete and share gpg key pair remote, create delete and share gpg key pair reddit, create delete and share gpg key pair rotation, create delete and share gpg key pair region, create delete and share gpg key pair rsa, create delete and share gpg key pair rsa key-pair, gpg create rsa key, create delete and share gpg key pair ssh, create delete and share gpg key pair script, create delete and share gpg key pair s3, create delete and share gpg key pair ssl, create delete and share gpg key pair ssh key, create delete and share gpg key pair salesforce, create delete and share gpg key pair ssh-keygen, gpg create secret key, create delete and share gpg key pair terraform, create delete and share gpg key pair to private key, create delete and share gpg key pair to ec2 instance, create delete and share gpg key pair to instance, creating delete and share gpg key pair the perfect, create delete and share gpg key pair ubuntu, create delete and share gpg key pair using cli, create delete and share gpg key pair using ssh, create delete and share gpg key pair using openssl"
toc = "<p><a href='#introduction-to-gnupg'>Introduction to GnuPG</a></p><p><a href='#prerequisite'>Prerequisite</a></p><p><a href='#generating-a-gpg-key-pair'>Generating a GPG key pair</a></p><p><a href='#sharing-your-public-key'>Sharing your public key</a></p><p><a href='#deleting-the-needless-key'>Deleting needless key</a></p><h3>Also Read</h3><hr><p><a href='/blog/encrypt-and-decrypt-a-file-using-gpg-keys'>How to encrypt and decrypt any message and files using gpg key pair?</a></p>"
+++
GnuPG, popularly known as GPG, is an extremely versatile tool, being widely used as the industry standard for encryption of things like emails, messages, files, or just anything you need to send to someone securely.
<!-- more -->

![Encrypt and decrypt a file using gpg keys](/assets/images/blogs/create-and-delete-gpg-key-pair/Gnupg.png)

<div class="blogcontents">

## Introduction to GnuPG

[GnuPG](https://gnupg.org) is a hybrid encryption software module that uses [OpenPGP](https://www.openpgp.org) at its core. PGP stands for Pretty Good Privacy. It is a tool for secure communication that provides authentication and cryptographic privacy for data communication.

GPG uses public key encryption wherein you create a key pair: one private or secret key you keep to yourself and one public key you share with your correspondents or the world. The important part of this two-key system is that neither key can be calculated by having the other. They are each an independent and necessary part of the system and are based upon solid mathematical foundations.

## Prerequisite

- A computer with `gnupg` installed on it.  
Download and install the [latest version of the GPG command line tools](https://gnupg.org/download/index.html) for your operating system if you haven't yet.

## Generating a GPG key pair

To start working with GPG you need to create a key pair for yourself.

- Use gpg with the --full-generate-key option to create a key pair.
- With this option, gpg creates and populates the ~/.gnupg directory if it does not exist.

<div class="highlight">
<pre><code id="gengpgkeypair">gpg --full-generate-key
</code>
<button id="gengpgkeypairbtn" type="button" onclick="copyCode('gengpgkeypair','gengpgkeypairbtn')" value="click">Copy</button>
</pre>
</div>

<pre class="overflowy imagecode"><code class="imagecode">$ gpg --full-generate-key
gpg (GnuPG) 2.2.39; Copyright (C) 2022 g10 Code GmbH
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.<br>
gpg: directory '/home/castor/.gnupg' created
gpg: keybox '/home/castor/.gnupg/pubring.kbx' created
Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
  (14) Existing key from card
Your selection? 1
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (3072) 4096
Requested keysize is 4096 bits
Please specify how long the key should be valid.
         0 = key does not expire
      &lt;n&gt;  = key expires in n days
      &lt;n&gt;w = key expires in n weeks
      &lt;n&gt;m = key expires in n months
      &lt;n&gt;y = key expires in n years
Key is valid for? (0) 2
Key expires at Tue 01 Nov 2022 09:29:11 AM +0545
Is this correct? (y/N) y<br>
GnuPG needs to construct a user ID to identify your key.<br>
Real name: yogesh
Email address: castor@whoisyoges.eu.org
Comment: just a test key
You selected this USER-ID:
    "yogesh (just a test key) &lt;castor@whoisyoges.eu.org&gt;"<br>
Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: /home/castor/.gnupg/trustdb.gpg: trustdb created
gpg: directory '/home/castor/.gnupg/openpgp-revocs.d' created
gpg: revocation certificate stored as '/home/castor/.gnupg/openpgp-revocs.d/036A752DE9DF5516B33E87BE33C05B4624890348.rev'
public and secret key created and signed.<br>
pub   rsa4096 2022-10-30 [SC] [expires: 2022-11-01]
      036A752DE9DF5516B33E87BE33C05B4624890348
uid                      yogesh (just a test key) &lt;castor@whoisyoges.eu.org&gt;
sub   rsa4096 2022-10-30 [E] [expires: 2022-11-01]

</code></pre>

## Sharing your public key

You need to share your public key so that people can encrypt and send any message and files to you which can be decrypted using only your private key.

### List the key pair

<div class="highlight">
<pre><code id="listurpubkeytoshare">gpg --list-keys
</code>
<button id="listurpubkeytosharebtn" type="button" onclick="copyCode('listurpubkeytoshare','listurpubkeytosharebtn')" value="click">Copy</button>
</pre>
</div>

<pre class="imagecode"><code class="imagecode">$ gpg --list-keys
/home/castor/.gnupg/pubring.kbx
--------------------------------
pub   rsa4096 2022-10-30 [SC] [expires: 2022-11-01]
      036A752DE9DF5516B33E87BE33C05B4624890348
uid           [ultimate] yogesh (just a test key) &lt;castor@whoisyoges.eu.org&gt;
sub   rsa4096 2022-10-30 [E] [expires: 2022-11-01]

</code></pre>

### Getting your public key

<div class="highlight">
<pre><code id="shareurpubkey">gpg --armor --export &lt;id&gt;
</code>
<button id="shareurpubkeybtn" type="button" onclick="copyCode('shareurpubkey','shareurpubkeybtn')" value="click">Copy</button>
</pre>
</div>

<pre class="overflowy imagecode"><code class="imagecode">$ gpg --armor --export 036A752DE9DF5516B33E87BE33C05B4624890348
-----BEGIN PGP PUBLIC KEY BLOCK-----<br>
mQINBGNd8zcBEACpJLknkdJmlJ9FWnyc6W/mMBuv/DD9ECF4DB45+2mFhPc21bYW
nKHZosvtmwBIYHArU6xlHkaOlL2K3Rda7zzwRXB+LzQNqWv0GxN2ukzbS3yixGBg
s8yDTa4SM1KFBXuLe6j+x0t0/M7p4yD0tTtK1zCIheel2pkWZ8djHqzvboj34ZN9
5nlxTKSTDbsPOOrrD9Y9nM/RVKdkklHT1esWc25i9rSHwJ0ds0F3F17mCIt+rRpl
tm2vTD7Ml5Le5cR8FAz/VBhSltDANtWjr4PtUncuwlUU9wFu6zUGMxzsoxLUXkZp
bB+geMhnbE8Sk1kyYILExaoLcQZ9GmsmBwYc7n1lgWCCNdwuVh26CgQu2Y96VTaC
/lJMe+j/HlkZKgZwPJd8JL7kxCvL3zYCsnJ4KPTMxUpgSp5JaUOGm5+mNsR2O98u
EC8LGU5TplfE7TEsr7IvNH5Dq+XQHaTv54iOJyUDICZMmQyp32nhc7LAvWzRsxDU
Axsx2lsJzrZC/SkD7Kd7gZPGyA0i3KHNDWqq8YbGFIAv3uv+pvw26WKjvTLgm1d5
5oKEYOGEJa/LZAco3O2Mbl7sKMB7bpFcV4Q3Ff26rsp7oSCxU4C66pSdZdpAEQSY
nnoCsmTtNUIVbyNU9S5lwOwQrWX7IOcfTuGALNq1yW7LnOZimKoGblCBxQARAQAB
tDN5b2dlc2ggKGp1c3QgYSB0ZXN0IGtleSkgPGNhc3RvckB3aG9pc3lvZ2VzLmV1
Lm9yZz6JAlQEEwEIAD4WIQQDanUt6d9VFrM+h74zwFtGJIkDSAUCY13zNwIbAwUJ
AAKjAAULCQgHAgYVCgkICwIEFgIDAQIeAQIXgAAKCRAzwFtGJIkDSLgsEACRqvg6
2Bcglte32vQNz5tHWqqKmmtSuJsXaxgIYjg+eKvkJrRW3QLK+YpiHYvyTDZLjq0/
VCFbCL3We9CFr3fgdXP1t0svhkidzHyyoe9WihMvxSVqnNKz1kU2NSldsoNmn32p
VeXOFRI84uCbWFa/XMwMryJkOagQQkveK4uTbULjzcSaOGILJEQY6kjo9cQAoPHX
G9gdfva4Ik8cITVRvS6jISEDPF4atHsiOJ/RDUlVhPLdoWpgfmaJgAybLHbOEfJb
i/jxz4TCvR/q9z7yT5Znc9R8yHgrU2EKoK5rj0bmmCpYH/eYDkehId07on8/XXxh
VC15ydz1RqQzLcEx8ZUMRZ4nqW+6TfIrv4lyvVi2eJbodc0iKqTL7blFaWA3bvHu
X6ZPm+C3MzUP2tt3gvWrkfDJrn536Xrjt8r2P0W4BFT7tBiFFp4UNUxeS+ghVlJl
zkMvvgccpEpn2HHHU8BLMgdtPHKtLmJXNLK44cgXBb/lhS8DCusnzKB9dSFUliTS
WuC/ZUMgUFjL2TrnLbsUdQiSIwYsascqoCArcAd2++FBYTrD2yswv6ir+FzEUqjW
KPa76oCrDgD34aG4nJa67xjXWVnahg87SljxP3d3S/6q0+4RYC+I7uMmGeTxzdnZ
WAVL/7vFq7Hbmgvpx3YJj9LRJwQYUiQZpK+rDrkCDQRjXfM3ARAAo0Mlc25OPWJE
lQr/rEmCRTh5z8GejVPN4JL7rv2sqe+rctHxbjvofwH35ThInGfuq6Noq4l6r40F
yHIUuib0MZZLTAifgZGS5YyNlB54x258JdcY5C6eENaV9G5Gqz3UpMdXOs/jxzmh
h3sPKLhFiDhRAylj2o78BZdIPsxGa7xNn0/HLkdJ7zwyUGaoMwM+Ps3xHEA8kfA7
daCHhkzCx4G8PGs2LXNkSMW51Km0ZCE9gyk1COL2TxCaniCy9PxcIbGd/SZYUf89
5RAXz7aBtPIYt1OhXAItvM+b00XLBxxGtRIb1Nyo7pwbqT72dIPXiMPBf0OK7Vbq
JDUFiCIRsKTolUm2MCOcboGhgBxfR6uIUMOKXY2d3aer/7UkWHe/6y7+sGHkWBaf
MUjqbAMPDBjKk2b6OodalQr8oyxZ79d5z2D4gBooxKpJA2NS5UOUaLBPtB83POfw
5otQJk2RlnlWmV6MVQolwg+IXiRZQVkzJ0mazZ6eEwP/EcZPpXur8LT6W2mo+rN2
g8qC2nCRZUQ842PoNi9L5ug1fRsaiTYhC4pXUppBbY3Sp8GFuTxP9FhWhK2j2sX2
xdDRmqDWePjimPZ4tzBBQalCLj0kuO8PtfChuWXk2Ro/hEg59mPxOTR9uyLtZrPF
wOM7KIgPondEa/lYP9JFoaTCm3ktGi8AEQEAAYkCPAQYAQgAJhYhBANqdS3p31UW
sz6HvjPAW0YkiQNIBQJjXfM3AhsMBQkAAqMAAAoJEDPAW0YkiQNIYl4P/0yIj7WK
hNyJtgKHv5QMEtbD3lL6IPNcUnEddbrCDuQD+/CCb02Af9IG5wwuPlSIpBa2Nh4r
NZrTkcPVitqaRdNPVTAeCFXGNnY+vMzbGBYHh+ajX6/b1YCmNKtTC37FH8G6GAOl
Hvi1xYhP/jFNoX5ftkVNU6MJi2bfJx98jRSYk/fhjAc/bG7YpLR/4B/U7/4Q4YAF
u+OrrJOeYRz7OfuBaFBIO2E34nDyd6hxdjR6fOThidlyzPOgkOEc6OB3R/IeKN69
i0ASLp/SJSpL25FE2r1olrxR8FMZnnAMe10T8fE5oRtKR5crmq58SdKQSW6DFh6O
FcL/2LOLDJn7Dazto/pvgFVF9kJ89bZhcJdyVaUkP5T6W3qW7nSNvkKCfBI+shUT
gvSue/AqzhCTh4pXR9xO7SYNbXku9J1h0VXNpmH3U2z4GODhYzeeq1+e1QmOFVCR
zRb/45/Tf4WT/rHMfFzCOzmLW9IsH8k8yfi6gxmOEdRHOIqLqmf9Dgc2+KKnPWhO
NodtiJD3ZN1f3krdy22bAIzOlfm5cb7hWoUBcRWqk76ZWcmIndffl2cc8MFaFcV3
GNyVJ+vbeBq1mCC/pQPqxwmkvwOmywdu9dDUoXH7+S4EXtwPDSlbS3bQBU1KqSMr
igXd7Kt4qERYzmc1NLbHG7/H/DV6KyxuJ4dJ
=oYnT
-----END PGP PUBLIC KEY BLOCK-----
</code></pre>

Just copy the output starting from `-----BEGIN PGP PUBLIC KEY BLOCK-----` to `-----END PGP PUBLIC KEY BLOCK-----` and send it to anyone who need to send you an encrypted message.

## Deleting the needless key

Assuming you don't need the keys anymore or if the key has been expired and you wish to delete it, here's the procedure:

### Delete secret/private key

First we should list if there are any secret keys available for the respective user and delete it if exists before deleting the public key.

#### Checking private/secret key

<div class="highlight">
<pre><code id="listseckeyfordel">gpg --list-secret-keys
</code>
<button id="listseckeyfordelbtn" type="button" onclick="copyCode('listseckeyfordel','listseckeyfordelbtn')" value="click">Copy</button>
</pre>
</div>

<pre class="imagecode"><code class="imagecode">$ gpg --list-secret-keys
/home/castor/.gnupg/pubring.kbx
--------------------------------
sec   rsa4096 2022-10-30 [SC] [expires: 2022-11-01]
      036A752DE9DF5516B33E87BE33C05B4624890348
uid           [ultimate] yogesh (just a test key) &lt;castor@whoisyoges.eu.org&gt;
ssb   rsa4096 2022-10-30 [E] [expires: 2022-11-01]

</code></pre>

#### Deleting private/secret key

<div class="highlight">
<pre><code id="delsecgpgkey">gpg --batch --delete-secret-keys --yes &lt;id&gt;
</code>
<button id="delsecgpgkeybtn" type="button" onclick="copyCode('delsecgpgkey','delsecgpgkeybtn')" value="click">Copy</button>
</pre>
</div>

<pre class="imagecode"><code class="imagecode">$ gpg --batch --delete-secret-keys --yes 036A752DE9DF5516B33E87BE33C05B4624890348
</code></pre>

#### Verify the private key deletion

<div class="highlight">
<pre><code id="verifysecgpgkeydln">gpg --list-secret-keys
</code>
<button id="verifysecgpgkeydlnbtn" type="button" onclick="copyCode('verifysecgpgkeydln','verifysecgpgkeydlnbtn')" value="click">Copy</button>
</pre>
</div>

The deleted secret key shouldn't exist anymore.

<pre class="imagecode"><code class="imagecode">$ gpg --list-secret-keys

</code></pre>

### Delete public key

#### Checking available public key/s

<div class="highlight">
<pre><code id="listpubgpgkeytodel">gpg --list-keys
</code>
<button id="listpubgpgkeytodelbtn" type="button" onclick="copyCode('listpubgpgkeytodel','listpubgpgkeytodelbtn')" value="click">Copy</button>
</pre>
</div>

<pre class="imagecode"><code class="imagecode">$ gpg --list-keys
/home/castor/.gnupg/pubring.kbx
--------------------------------
pub   rsa4096 2022-10-30 [SC] [expires: 2022-11-01]
      036A752DE9DF5516B33E87BE33C05B4624890348
uid           [ultimate] yogesh (just a test key) &lt;castor@whoisyoges.eu.org&gt;
sub   rsa4096 2022-10-30 [E] [expires: 2022-11-01]

</code></pre>

#### Deleting public key

<div class="highlight">
<pre><code id="delpubgpgkey">gpg --batch --delete-keys --yes &lt;id&gt;
</code>
<button id="delpubgpgkeybtn" type="button" onclick="copyCode('delpubgpgkey','delpubgpgkeybtn')" value="click">Copy</button>
</pre>
</div>

<pre class="imagecode"><code class="imagecode">$ gpg --batch --delete-keys --yes 036A752DE9DF5516B33E87BE33C05B4624890348

</code></pre>

#### Verify the public key deletion

<div class="highlight">
<pre><code id="verifypubgpgkeydln">gpg --list-keys
</code>
<button id="verifypubgpgkeydlnbtn" type="button" onclick="copyCode('verifypubgpgkeydln','verifypubgpgkeydlnbtn')" value="click">Copy</button>
</pre>
</div>

The deleted public key shouldn't exist anymore. If you have more than one key, the remaining keys will be shown.

<pre class="imagecode"><code class="imagecode">$ gpg --list-keys
gpg: checking the trustdb
gpg: no ultimately trusted keys found

</code></pre>
</div>