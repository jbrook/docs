## Generating SSH Keys

To generate an SSH key pair open the application settings, pipeline settings or
organization settings and click the `+ Generate SSH key` link. From the
dialog you can choose a name for you SSH key and the number of bits to use to
generate it. Wercker will generate the key for you in the background and create
two environment variables.

![SSH key generation dialog](/images/creating-ssh-keys_1.png)

> Note: The private key will be made protected so you cannot read it back. The
> public key should be copied to the destination.

### <a name="manually-adding-key" class="anchor"></a>Manually adding an SSH key

Alternatively you can create an SSH key manually by generating it locally and
copying the private key as an environment variable. The environment variable
*must* end with `_PRIVATE`. For instance if you wanted to manually add a
`BITBUCKET` ssh key create a new environment variable called
`BITBUCKET_PRIVATE`. It is also strongly recommended that you mark the private
key `protected`.

![Manually added SSH key](/images/creating-ssh-keys_2.jpg)

[Read more on using SSH Key pairs &rsaquo;](/docs/ssh-keys/using-ssh-keys.html)

