# zpe_tailscale
This repo guides you to install tailscale on NodegridOS

# Open console session on Nodegrid

Navigate to the root shell

    shell sudo su -
    
    wget https://pkgs.tailscale.com/stable/tailscale_1.32.2_386.tgz
    
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

    This will be added later

  


    
    

    
