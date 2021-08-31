#tafchain

Install and deploy nodes.
This article describes how to install and deploy TAF Chain nodes.

--Prerequisites
This article describes how to install and deploy TAF Chain nodes. TAF Chain needs to be installed on a Linux server and supports Ubuntu 18.04 or later.
The recommended hardware configuration for the testnet is 8 GB memory, 4 CPU cores, and 200 GB hard disk.

--Resource description
tafSoftware_0.0.1.deb TAF Chain node program installation file. Download link: https://github.com/tafchain/tafchain/releases/tag/v0.0.1/tafSoftware_0.0.1.deb

genesis.json Program configuration file. Download link: https://github.com/tafchain/tafchain/releases/tag/v0.0.1/genesis.json

start.sh Script file. Download link: https://github.com/tafchain/tafchain/releases/tag/v0.0.1/start.sh

--Software Installation
Download the deb installation file of TAF Chain and install it, taking the Ubuntu system as an example.

    wget https://github.com/tafchain/tafchain/releases/tag/v0.0.1/tafSoftware_0.0.1.deb
    sudo dpkg -i tafSoftware_0.0.1.deb
    
The default installation path of the program is "/usr/tafsys/0.0.1/bin". Add the environment variables to the system.

    vi  /etc/profile
    export PATH=$PATH:/usr/tafsys/0.0.1/bin
    source  /etc/profile

--Join the network
Download the genesis.json file and start.sh script file to the current working directory

    wget https://github.com/tafchain/tafchain/releases/tag/v0.0.1/genesis.json 
    wget https://github.com/tafchain/tafchain/releases/tag/v0.0.1/start.sh

Run start.sh to join the network.

    chmod +x start.sh
    ./start.sh
    
The start.sh script specifies the startup parameters of the program:

p2p-peer-address
Specify a known network node and configure a private network as required.

    Parameter format: -- p2p-peer-address ip :port
    ip ： address
    port ： Port number

    Example:
        --p2p-peer-address 121.41.193.65:9010

signature-provider
Specify the public key of the representative node. You can add this parameter if you want to be the representative node.

    Parameter format:-- signature-provider publickey=KEY:privatekey
    publickey： public key
    privatekey： private key

    Example:
    -- signature-providerTAF5EfU2fDgHZTNwPhuoHJgKcrNJ3PbyaYMHMrgMnBpVffWjgeJjX=KEY:5HxK6mfoNr1pbnbYs1AmsKjavJQaoxiNVUdeJD6ZPFZkQvGcZVM

--Run tafclient to test data.

    tafclient query bcinfo
    Sample data:

    {  
        "server_version": "0955c540",  
        "chain_id": "2e9e10619a96d5181cc0d85f7067e9f844b3da08c6263c53578d85e92c7a3c84",  
        "head_block_num": 190078,  
        "last_irreversible_block_num": 189990,  
        "last_irreversible_block_id": "0002e62695f98d2682a1b3d0ee0034ca2a9f8202400f34899ede14059c436ee2",  
        "head_block_id": "0002e67effc6d68c6fea82c5f5598f90de0f654d0a9c23b457ede6dde06aa9c5",  
        "head_block_time": "2021-08-18T06:12:37.500",  
        "head_block_maker": "T1hNQ2VW9rowZkdhyWem74MfUeEADN4h",  
        "virtual_block_cpu_limit": 1000000000,  
        "virtual_block_net_limit": 1048576000,  
        "block_cpu_limit": 1000000,  
        "block_net_limit": 1048576,  
        "server_version_string": "0.0.1-0955c540a027cdc7c1d771788bc6e09b0dcb1bc2",  
        "fork_db_head_block_num": 190078,  
        "fork_db_head_block_id": "0002e67effc6d68c6fea82c5f5598f90de0f654d0a9c23b457ede6dde06aa9c5",  
        "server_full_version_string": "0.0.1-0955c540a027cdc7c1d771788bc6e09b0dcb1bc2"  
    }

--Representative Node

To become a representative node, perform the following steps:

1. Create an account as a node account
2. Register as a representative node
3. Delegate source include bandwidth and CPU

