# SSHing into kraken

Kraken is our compute VM that is running on Euphrates, the compute server we
bought for the lab on the [ToMCAT](https://ml4ai.github.io/tomcat) grant. It
is fairly capable (~750 GB RAM, 128 cores, two A100 GPUs).

Here are instructions for SSH-ing into Kraken:

1. Generate an SSH key by running the following command (I recommend not requiring a passphrase as it will get old to keep typing it in):

    ssh-keygen -t ed25519

2. Put the following lines in your `~/.ssh/config` file:

    Host *
        ServerAliveInterval 10
        ServerAliveCountMax 3
        ForwardAgent yes

    Host kraken
        HostName kraken.sista.arizona.edu

3. Copy your SSH key to kraken by running the following command:

    ssh-copy-id kraken

Then, test whether you can ssh into kraken by running the following command:

    ssh kraken
