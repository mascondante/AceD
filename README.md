# GLPM
Shell script to install a [GLPM Masternode](http://glacierplatform.io/) on a Linux server running Ubuntu 16.04.  
This will require a VPS, [CryptoSharks](https://github.com/cryptosharks131/) (creator of the original script) uses [Vultr](https://www.vultr.com/?ref=7310394).  The $5/mo server size will suffice.  
This script will install **GLPM v1.0**.
***

## Installation:
Log into the server using ssh (Putty for windows or terminal for Mac users) and run the following commands:
```
wget -q https://raw.githubusercontent.com/mascondante/AceD/master/glpm_install.sh
bash glpm_install.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the GLPM Core Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **10000** **GLPM** to **MN1**.
4. Wait for 15 confirmations.
5. Go to **Tools -> "Debug console - Console"**
6. Type the following command: **masternode outputs**
7. Go to  ** Tools -> "Open Masternode Configuration File"
8. Add the following entry:
```
Alias Address Privkey TxHash Output_index
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6** 
* Output index:  **Second value from Step 6** It can be **0** or **1**
9. Click OK and exit the Wallet.
10. Open GLPM Core Wallet, go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again.
10. Click **Start All** or **Start Alias**
11. If you are not able to see your **Masternode**, try to close and open your desktop wallet.
***

## Usage:
```
GLPM-cli getinfo
GLPM-cli masternode status
GLPM-cli mnsync status
```
Also, if you want to check/start/stop **GLPM** , run one of the following commands as **root**:
```
systemctl status GLPM #To check the service is running.
systemctl start GLPM #To start AceD service.
systemctl stop GLPM #To stop AceD service.
systemctl is-enabled GLPM #To check whetether AceD service is enabled on boot or not.
```
***

## Updating GLPM
The first line (rm glpm_update.sh) is not required the very first time you update the node and will return an error if you run it.  This is fine, continue with the update script.
```
rm glpm_update.sh*
wget -q https://raw.githubusercontent.com/mascondante/AceD/master/glpm_update.sh
bash glpm_update.sh
```
***

## Sentinel (IGNORE: This is not yet required!)

**Sentinel** is installed in **/sentinel** and added to **crontab** file.  
Sentinel log file is **/root/.GLPM2/sentinel.log**  
Test the config by running the following commands:
```
cd /sentinel
./venv/bin/py.test ./test
SENTINEL_DEBUG=1 ./venv/bin/python bin/sentinel.py
```
***

## Donations:  

Any donation is highly appreciated.  Donation addresses have not changed. CryptoSharks will receive the donation as he created the scripts. This is simply a GLPM adaptation.

**AceD**: AUxZpb1BpczT4pzfN7fYh6HxKEvwPL2SxK  
**BTC**: 1FJvtLBszQgY2eKBawov48RwSYy2yqEvn1  
**ETH**: 0x39acE9917e25E2A04643d30319cF34449A72441B  
**LTC**: LR1Mmchr6Zz1vj51xecTiEdS1WHfJTVg5t
