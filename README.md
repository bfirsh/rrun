# rrun

rrun rsyncs the current directory thens runs a command over ssh.

This seems to be a really common pattern, and I was surprised to find there isn't a good solution to doing this. So, here's a ridiculously simple shell script.

It works a bit like this:

    $ rrun bfirsh-dev python train.py
    Copying current directory...
    ...
    sent 512 bytes  received 48 bytes  373.33 bytes/sec
    total size is 11341  speedup is 20.25

    Running 'python train.py'...
    Choo choo!


    $ rrun bfirsh-dev
    Copying current directory...
    ...
    sent 512 bytes  received 48 bytes  373.33 bytes/sec
    total size is 11341  speedup is 20.25

    Running '$SHELL'...
    ben@bfirsh-dev:~/rexec/myproject$ 

It rsyncs the current directory into `~/rexec/<dirname>`, then runs the command you pass over ssh. That's it really.

## Install

    curl https://raw.githubusercontent.com/bfirsh/rrun/main/rrun > /usr/local/bin/rrun
    chmod +x /usr/local/bin/rrun
