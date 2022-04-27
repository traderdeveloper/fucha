# Masternode Setup  
# Step by step guide
 

Requirements: 	

1.) for 1 Masternode you need a wallet with 1000 FUCHA Coins (1 additional coin you need for fees!)
2.) VPS for example on vultr or any other vps services or Pecunia  

Feel free to use our reflinks to signup: 
vultr: <a href="https://www.vultr.com/?ref=8913368"><img src="https://www.vultr.com/media/banners/banner_468x60.png" width="468" height="60"></a>

 
## start in the wallet 
in wallet: Open Debug console: 

```bash
createmasternodekey
```

<table>
<tr><td>example</td></tr>
<tr><td>alias= MN1</td></tr>
<tr><td>6Vju9Mbsez7qKunvV7WzJVMLKTLnk2pLZNrnAcyRJZG3XE3iH58</td></tr>
</table>

```bash
getnewaddress "masternode1"  
```

<table>
<tr><td>example</td></tr>
<tr><td>FNaF43HxGicz1pCoE2ezM7hMWYSQmRLFZ3</td></tr>
</table>

send exact 1000 Coins to the address (confirmation need: 20) 


# Installation: for Security use SSH on your vps!!

# Start install the requirements on VPS:

```bash
sudo apt-get update && sudo apt-get upgrade -y
```
```bash
sudo apt-get upgrade -y
```
```bash
sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils python3 libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-test-dev libboost-thread-dev libboost-all-dev libboost-program-options-dev libminiupnpc-dev libzmq3-dev libprotobuf-dev protobuf-compiler unzip software-properties-common cmake -y
```
```bash
sudo add-apt-repository ppa:bitcoin/bitcoin
```
You will be prompted with "Enter". press enter

```bash
sudo apt-get update && sudo apt-get install libdb4.8-dev libdb4.8++-dev -y
```

download the wallet-client, tx and daemon file

```bash

wget https://github.com/traderdeveloper/fucha/releases/download/2000/fucha2000-linux-daemon.zip
```
fillout the password of your username and press enter


```bash
unzip fucha2000-linux-daemon.zip
```
```bash
sudo chmod +x fuchad
```
```bash
sudo chmod +x fucha-tx
```
```bash
sudo chmod +x fucha-cli
```
```bash
sudo mv fuchad fucha-cli fucha-tx /usr/bin/
```
```bash
sudo apt-get install libdb4.8-dev libdb4.8++-dev -y
```
```bash
mkdir $HOME/.fucha
```
```bash
nano $HOME/.fucha/fucha.conf
```

copy this with your details in th conf. file (choose only another good rpcuser and a very good password, you need your masternode genkey from wallet and the ip address of the vps server)
```bash
#----
rpcuser=rpc_userchooseagoodone
rpcpassword=chooseagoodpassword
rpcallowip=127.0.0.1
#----
listen=1
server=1
daemon=1
maxconnections=256
#----
externalip=IP-address
masternode=1
masternodeprivkey=MASTERNODE-GENKEY-from-debugconsole

addnode=95.179.210.251
addnode=155.138.145.134
addnode=70.34.211.78
#----
```
save this file by pressing CONTROL+O and press enter
close this file by pressing CONTROL+X

# start the vps server with

```bash
fuchad
```
if everything is fine: you get an output: fucha server starting




### back in wallet
 
go to debug console

```bash
getmasternodeoutputs
```
<table>
<tr><td>example</td></tr>
 <tr><td>{</td></tr>
<tr><td>    "txhash": "92b73f399eb6ca01fdea7e49b52194fa8d0774fea05f70268e8e78f286c2948a", </td></tr>
<tr><td>     "outputidx": 0 {</td></tr>
<tr><td>   }</td></tr>
</table>


# Configure masternode.conf file (look at the example in file), reopen wallet and start masternode in debug console

<table>
<tr><td>example for masternode in masternode.conf file </td></tr>
<tr><td>mn1 IP_OF_THE_SERVER:18145 MASTERNODE_GENKEY TX_HASH TX_OUTPUTS</td></tr>
<tr><td>mn1 123.45.67.89:18145 652FzuBw4v6ijn8fPw8843oh1NmSWBDpSLR1nipyCxkU73auGBx 92b73f399eb6ca01fdea7e49b52194fa8d0774fea05f70268e8e78f286c2948a 0</td></tr>
</table>

save file, reopen wallet and start in debug console !

```bash
startmasternode alias lockwallet "Alias"
```
