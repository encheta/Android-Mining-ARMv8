# Android-Mining
Quick installation of mining on Android Phones.

This installation script is experimental and has been adapted from Oink70's original. It has been modified to remove installation of Oink70's public SSH key, as well as redirect it to installing a version of ccminer by simeononsecurity claimed to be even further optimized for most ARMv8 architectures (Cortex models A53, A55, A57, A72, A73, A75, A76, A78c, & A78). This repo is aimed to help users easily compile and test out this fork in an effort to promote further development in the ARM/phone mining space.

I may have also updated the QR and default wallet and pool details to my own. If you're wanting to donate some hashrate to me, don't remember to change the config using the steps below. ;)

## Github cloning and customizing
1. clone this repo to your own github account.
2. change the URL on line 38 of the 'README.md' to reflect your own account.
3. replace `QR/install.png` with your own.
4. change line 41 of 'install.sh' to reflect your own github link.
6. adjust the `config.json` to your address and mining details.
7. optional: change line 20 of your `config.json` to your own LAN IP range.
8. optional: change line 21 of your `config.json` to the LAN IP your phone uses.

## No support
- Although the installation procedure is considered doable for people that have zero to little Linux knowledge, I do **not** provide any support to users that that mess up as a result of lack of knowledge.
- Reading is an dying art. There's no instruction video for people that can't follow instructions step-by-step.

## Prerequisites
- Some fundamental Linux knowledge is *required*. (do an online course!)
- Knowledge about how to operate Linux *screen* is a must.
- Knowledge on *ssh* and *scp* is highly recommended.
- Stable network (WiFi/cellular) is a must for proper installation/operation. Be prepared to troubleshoot and fix them yourself.

## Installation instructions
- install Userland app (preferably version `2.8.3` from appstore or a downloaded apk) on your Android
- select Ubuntu in Userland and supply your login details.
- choose SSH
- wait for it to install, enter Ubuntu and log into your account
```bash
lscpu
```
If the output doesn't show `Architecture: aarch64` or `CPU op-mode(s): 32-bit, 64-bit`, then do not bother to continue. Your phone is not running a 64-bit OS.

```bash
curl -o- -k https://raw.githubusercontent.com/encheta/Android-Mining-ARMv8/main/install.sh | bash
```
For easy access on phones:
![install.sh](QR/install.png)

Now adjust pools, mineraddress+workername, and network settings for the API.
save with `<CTRL>-S` and exit with `<CTRL>-X`
```bash
nano config.json
```

## Usage:
start mining with `~/ccminer/start.sh`

Standard SSH port for Userland is port `2022`.
Optional: create an entry in your SSH config file for each phone:
```
Host Pixel2XL01
    Hostname 192.168.25.81
    Port 2022
    User Pixel2XL01
    IdentityFile ~\.ssh\id-rsa_oink-private
```

Starting the miner:
`~/ccminer/start.sh`

Monitoring the miner:
- `screen -x CCminer`
- exit with `CTRL-a` key combination followed by `d`.

Terminating the miner:
`screen -X -S CCminer quit`

## Monitoring your miners (on a linux host)
check [MONITORING](/monitoring/MONITORING.md).

## Monitoring your miners (Using an Android app)
check [DroidVNC](https://play.google.com/store/apps/details?id=net.christianbeier.droidvnc_ng&hl=en_US&gl=US).

### I accept no warranties or liabilities on this repo. It is supplied as a service.
### This script is Experimental and not yet tested - This is my first public git fork and my coding ability is close to nonexistant. Think of me as the human equivalent of 1000 chimps on keyboards - Use at your own risk!!!
