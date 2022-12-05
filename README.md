# zpe_tailscale
This repo guides you to install tailscale on NodegridOS

# Open console session on Nodegrid

Navigate to the root shell

    shell sudo su -
    
    wget https://pkgs.tailscale.com/stable/tailscale_1.32.2_386.tgz
    
    # if you get an error about certificates use
    
    wget https://pkgs.tailscale.com/stable/tailscale_1.32.3_386.tgz --no-check-certificate
    
    
Unpack the archive

    tar xvf tailscale_1.32.2_386.tgz
    
Navigate to taislcale folder
    
    cd tailscale_1.32.2_386/
    
To start tailscale service
    
    sudo ./tailscaled --state=tailscaled.state &
    
    sudo ./tailscale up &
    
<img width="993" alt="Screen Shot 2022-11-02 at 11 14 57" src="https://user-images.githubusercontent.com/103506681/199435507-537ac656-025b-4827-bbb5-16aec2716e58.png">

After running tailscale service you need visit the URL that tailscaled service created.

To authenticate yourself by 3 options. (Microsoft, Google, Github)

If you want to run tailscale service when the device boots up.

Place this script to the directory as /home/root/tailscale.sh

    #!/bin/bash
    #start tailscale
    /home/root/tailscale_1.32.2_386/tailscaled &

Also we need to place init.d script to /etc/init.d as blah

    #! /bin/sh
    # /etc/init.d/blah
    #

    # Some things that run always
    touch /var/lock/blah
    /home/root/tailscale_1.32.2_386/tailscaled &

    # Carry out specific functions when asked to by the system
    case "$1" in
      start)
        echo "Starting script blah "
        echo "Could do more here"
        /home/root/tailscale_1.32.2_386/tailscale up
        ;;
      stop)
        echo "Stopping script blah"
        echo "Could do more here"
        /home/root/tailscale_1.32.2_386/tailscale stop
        ;;
      *)
        echo "Usage: /etc/init.d/blah {start|stop}"
        exit 1
        ;;
    esac

    exit 0

Once you've saved your file into the correct location make sure that it's executable by running

    chmod 755 /etc/init.d/blah

Then you need to add the appropriate symbolic links to cause the script to be executed when the system goes down, or comes up.

The simplest way of doing this is to use the Debian-specific command update-rc.d
    
    update-rc.d blah defaults
    
    

    
