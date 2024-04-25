+++
title = "Encrypt and decrypt a file using GPG keys"
date = "2022-10-29"
updated = "2022-12-07"
page_template = "page.html"
draft = false
description = "If you have someone's public gpg key, you can use gnupg to safely encrypt a file and send it to them over an insecure connection (i.e. the internet). They can then use their private key to decrypt the file you sent."
[extra]
opengraph = "/assets/images/blogs/encrypt-and-decrypt-a-file-using-GPG-keys/encrypt-and-decrypt-a-file-using-GPG-keys.jpg"
gotoTop = true
copy_code = true
shareable = true
viewallblogs = true
keywords = "encrypt file using gpg key, encrypt file with gpg key, encrypt file with gpg public key, encrypt using gpg key, encrypt a file using public key, encrypt and decrypt a file in linux, encrypt a file with gpg key, encrypt a file using a public key, use gpg to encrypt a file, encrypt and decrypt a file using gpg key pair authentication , use gpg key to encrypt file, use gpg key to encrypt text, gpg encrypt file, encrypt and decrypt a file using gpg key pair bash, encrypt and decrypt a file using gpg key pair command, encrypt and decrypt a file using gpg key pair cli, encrypt and decrypt a file using gpg key pair centos, encrypt and decrypt a file using gpg key pair download, encrypt and decrypt a file using gpg key pair denied, encrypt and decrypt a file using gpg key pair directory, decrypt gpg key with passphrase, encrypt and decrypt a file using gpg key pair example, encrypt and decrypt a file using gpg key pair empty, encrypt and decrypt a file using gpg key pair file, encrypt and decrypt a file using gpg key pair github, encrypt and decrypt a file using gpg key pair generation, encrypt with gpg key, encrypt and decrypt a file using gpg key pair name, encrypt and decrypt a file using gpg key pair openssl, encrypt and decrypt a file using gpg key pair password, encrypt and decrypt a file using gpg key pair passphrase, encrypt and decrypt a file using gpg key pair paths, encrypt and decrypt a file using gpg key pair pgp, encrypt and decrypt a file using gpg key pair private, encrypt and decrypt a file using gpg key pair public/private, pgp encrypt a file with public key, how to decrypt a file with a public key	, encrypt and decrypt a file using gpg key pair query, encrypt and decrypt a file using gpg key pair question, encrypt and decrypt a file using gpg key pair remote, encrypt and decrypt a file using gpg key pair rhel, encrypt and decrypt a file using gpg key pair redhat, encrypt and decrypt a file using gpg key pair rsa, decrypt gpg rsa key, encrypt and decrypt a file using gpg key pair gpg, encrypt and decrypt a file using gpg key pair script, encrypt and decrypt a file using gpg key pair setup"
+++
If you have someone's public gpg key, you can use gnupg to safely encrypt a file and send it to them over an insecure connection (i.e. the internet). They can then use their private key to decrypt the file you sent.
<!-- more -->

![Encrypt and decrypt a file using gpg keys](/assets/images/blogs/encrypt-and-decrypt-a-file-using-GPG-keys/encrypt-and-decrypt-a-file-using-GPG-keys.jpg)

## How does GPG work?

To start using GPG, you’ll first need to have a GPG key.

A GPG key is what you’ll use to encrypt or decrypt files. It’s also what is used to identity you, with things like your name and email being tied to the key as well.

<br>

GPG keys work by using two files, a private key and a public key. These two keys are tied to each other, and are both needed to use all of GPG’s functionality, notably encrypting and decrypting files.

<br>

When you encrypt a file with GPG, it uses either the private key or the public key. The new, encrypted file can then only be decrypted with the paired alternate public or private key.  
Generally public key is used for encryption and private one for decryption.

<br>

The private key is meant to be stored in a fashion stated directly in its name – privately, and not given out to anyone.

The public key on the other hand is meant to be given to others, or anyone you want to be able to encrypt files to send to you securely.

## Prerequisite

- A computer with `gnupg` installed on it.
- A GPG key pair  
[Don't know how to create one? Read this first.](/blog/create-your-gpg-key-pair)

## Encryption using a public GPG key

### Save the public key in a file, say `yoges_pubgpg.asc`

Contents inside `yoges_pubgpg.asc` should seem something like below:

<pre class="overflowy imagecode"><code class="imagecode">-----BEGIN PGP PUBLIC KEY BLOCK-----<br>
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

### Add the public GPG key to your keyring

<div class="highlight">
<pre><code id="addpubgpgkey">gpg --import yoges_pubgpg.asc
</code>
<button id="addpubgpgkeybtn" type="button" onclick="copyCode('addpubgpgkey','addpubgpgkeybtn')" value="click">Copy</button>
</pre>
</div>

<pre class="imagecode"><code class="imagecode">$ gpg --import yoges_pubgpg.asc
gpg: key 33C05B4624890348: public key "yogesh (just a test key) &lt;castor@whoisyoges.eu.org&gt;" imported
gpg: Total number processed: 1
gpg:               imported: 1
</code></pre>

### Signing a Public Key

If you want to keep a file away from prying eyes and ensure that it comes from the person it says it comes from and that it has not be altered, you can sign the file using your private key and encrypt it using the recipient’s public key. The recipient can then decrypt it using his private key and verify the signature using the sender’s public key.

#### Check recipient's public key

<div class="highlight">
<pre><code id="chkpubgpgkey">gpg --list-public-keys
</code>
<button id="chkpubgpgkeybtn" type="button" onclick="copyCode('chkpubgpgkey','chkpubgpgkeybtn')" value="click">Copy</button>
</pre>
</div>

<pre class="imagecode"><code class="imagecode">$ gpg --list-public-keys
/home/useless/.gnupg/pubring.kbx
--------------------------------------------
pub   rsa4096 2022-10-29 [SC]
      D8C96133251FFDCC8ACFE645AC5C5F04930D8ACF
uid           [ultimate] Castor (Trusted GPG Key of Castor from https://castorIsDead.xyz; send map of hidden treasure to castor!) &lt;whoisYoges@castorIsDead.xyz&gt;
sub   rsa4096 2022-10-29 [E]<br>
pub   rsa4096 2022-10-30 [SC] [expires: 2022-11-01]
      036A752DE9DF5516B33E87BE33C05B4624890348
uid           [ unknown] yogesh (just a test key) &lt;castor@whoisyoges.eu.org&gt;
sub   rsa4096 2022-10-30 [E] [expires: 2022-11-01]
</code></pre>

The `[ultimate]` one is your personal key. And the other `[unknown]` is the public key you just added.

#### Sign the public key with your GPG key

<div class="highlight">
<pre><code id="signpubgpgkey">gpg --sign-key &lt;id&gt;
</code>
<button id="signpubgpgkeybtn" type="button" onclick="copyCode('signpubgpgkey','signpubgpgkeybtn')" value="click">Copy</button>
</pre>
</div>

<pre class="imagecode"><code class="imagecode">$ gpg --sign-key 036A752DE9DF5516B33E87BE33C05B4624890348<br>
pub  rsa4096/33C05B4624890348
     created: 2022-10-30  expires: 2022-11-01  usage: SC
     trust: unknown       validity: unknown
sub  rsa4096/58A64F87EEA58B99
     created: 2022-10-30  expires: 2022-11-01  usage: E
[ unknown] (1). yogesh (just a test key) &lt;castor@whoisyoges.eu.org&gt;<br><br>
pub  rsa4096/33C05B4624890348
     created: 2022-10-30  expires: 2022-11-01  usage: SC
     trust: unknown       validity: unknown
 Primary key fingerprint: 036A 752D E9DF 5516 B33E  87BE 33C0 5B46 2489 0348<br>
     yogesh (just a test key) &lt;castor@whoisyoges.eu.org&gt;<br>
This key is due to expire on 2022-11-01.
Are you sure that you want to sign this key with your
key "Castor (Trusted GPG Key of Castor from https://castorIsDead.xyz; send map of hidden treasure to castor!) &lt;whoisYoges@castorIsDead.xyz&gt;" (AC5C5F04930D8ACF)<br>
Really sign? (y/N) y
</code></pre>

And then you'll be prompted to enter your GPG key password, enter that and the key is signed.  
After signing the public key, the `[unknown]` key is signed and shown as `[ full ]`.

<pre class="imagecode"><code class="imagecode">$ gpg --list-public-keys
pub   rsa4096 2022-10-29 [SC]
      D8C96133251FFDCC8ACFE645AC5C5F04930D8ACF
uid           [ultimate] Castor (Trusted GPG Key of Castor from https://castorIsDead.xyz; send map of hidden treasure to castor!) &lt;whoisYoges@castorIsDead.xyz&gt;
sub   rsa4096 2022-10-29 [E]<br>
pub   rsa4096 2022-10-30 [SC] [expires: 2022-11-01]
      036A752DE9DF5516B33E87BE33C05B4624890348
uid           [  full  ] yogesh (just a test key) &lt;castor@whoisyoges.eu.org&gt;
sub   rsa4096 2022-10-30 [E] [expires: 2022-11-01]
</code></pre>

### Encrypt the file you're sending, using the public GPG key:

In this example `message.txt` is the secret text message, `message.txt.gpg` is the encrypted file and `castor@whoisYoges.eu.org` is the email address from the receiver's public key. The encrypted file can be named whatever you like.

<div class="highlight">
<pre><code id="secmsgpgpinc">gpg --encrypt --output message.txt.gpg --recipient castor@whoisYoges.eu.org message.txt
</code>
<button id="secmsgpgpincbtn" type="button" onclick="copyCode('secmsgpgpinc','secmsgpgpincbtn')" value="click">Copy</button>
</pre>
</div>

<pre class="imagecode"><code class="imagecode">$ gpg --encrypt --output message.txt.gpg --recipient castor@whoisYoges.eu.org message.txt
gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   1  signed:   1  trust: 0-, 0q, 0n, 0m, 0f, 1u
gpg: depth: 1  valid:   1  signed:   0  trust: 1-, 0q, 0n, 0m, 0f, 0u
gpg: next trustdb check due at 2022-11-01
</code></pre>

Now you can send the encrypted file (`message.txt.pgp`) to the recipient. It is even safe to upload the file/s to a public file sharing service and tell the recipient to download them from there.

## Decrypting using private GPG key

Here the encrypted file is message.txt.pgp and the decrypted file will be named message.txt

<div class="highlight">
<pre><code id="decpgpkey">gpg --decrypt --output message.txt message.txt.pgp
</code>
<button id="decpgpkeybtn" type="button" onclick="copyCode('decpgpkey','decpgpkeybtn')" value="click">Copy</button>
</pre>
</div>

<pre class="imagecode"><code class="imagecode">$ gpg --decrypt --output message.txt message.txt.gpg 
gpg: encrypted with 4096-bit RSA key, ID 58A64F87EEA58B99, created 2022-10-30
      "yogesh (just a test key) &lt;castor@whoisyoges.eu.org&gt;"
</code></pre>

## Deleting public keys from keyring

Assuming you don't need the key any more and wish to delete it:

#### list the available keys for the respective user

<div class="highlight">
<pre><code id="listpubgpgkeytodel">gpg --list-public-keys
</code>
<button id="listpubgpgkeytodelbtn" type="button" onclick="copyCode('listpubgpgkeytodel','listpubgpgkeytodelbtn')" value="click">Copy</button>
</pre>
</div>

<pre class="imagecode"><code class="imagecode">$ gpg --list-public-keys
pub   rsa4096 2022-10-29 [SC]
      D8C96133251FFDCC8ACFE645AC5C5F04930D8ACF
uid           [ultimate] Castor (Trusted GPG Key of Castor from https://castorIsDead.xyz; send map of hidden treasure to castor!) &lt;whoisYoges@castorIsDead.xyz&gt;
sub   rsa4096 2022-10-29 [E]<br>
pub   rsa4096 2022-10-30 [SC] [expires: 2022-11-01]
      036A752DE9DF5516B33E87BE33C05B4624890348
uid           [  full  ] yogesh (just a test key) &lt;castor@whoisyoges.eu.org&gt;
sub   rsa4096 2022-10-30 [E] [expires: 2022-11-01]
</code></pre>

#### Delete the unrequired key

<div class="highlight">
<pre><code id="delunrequiredpgpkey">gpg --batch --delete-keys --yes &lt;id&gt;
</code>
<button id="delunrequiredpgpkeybtn" type="button" onclick="copyCode('delunrequiredpgpkey','delunrequiredpgpkeybtn')" value="click">Copy</button>
</pre>
</div>

<pre class="imagecode"><code class="imagecode">$ gpg --batch --delete-keys --yes 036A752DE9DF5516B33E87BE33C05B4624890348
</code></pre>

#### Verify the deletion

<div class="highlight">
<pre><code id="verifygpgkeydelition">gpg --list-public-keys
</code>
<button id="verifygpgkeydelitionbtn" type="button" onclick="copyCode('verifygpgkeydelition','verifygpgkeydelitionbtn')" value="click">Copy</button>
</pre>
</div>

<pre class="imagecode"><code class="imagecode">$ gpg --list-public-keys
pub   rsa4096 2022-10-29 [SC]
      D8C96133251FFDCC8ACFE645AC5C5F04930D8ACF
uid           [ultimate] Castor (Trusted GPG Key of Castor from https://castorIsDead.xyz; send map of hidden treasure to castor!) &lt;whoisYoges@castorIsDead.xyz&gt;
sub   rsa4096 2022-10-29 [E]

</code></pre>