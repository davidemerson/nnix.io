# nnix.io scuttlebutt

Messaging fit for your journey around the Chagos Archipelago.

        __ _.--..--._ _
     .-' _/   _/\_   \_'-.
    |__ /   _/\__/\_   \__|
       |___/\_\__/  \___|
              \__/
              \__/
               \__/
                \__/
             ____\__/___
       . - '             ' -.
      /                      \

## launch an EC2 t4g.nano
- running amazon linux 64-bit arm
- 30GB gp2 storage on the root volume

## acquire an Elastic IP, if you don't have a free one already.

## associate the Elastic IP with the instance you launched just now.

## set your A record to the Elastic IP in question

## log in (ssh) to the EC2 you just made

## edit hostname
sudo nano /etc/hostname
sudo reboot

## install basic updates
sudo yum update

## install nginx from linux-extras
sudo amazon-linux-extras install nginx1

## install epel
sudo amazon-linux-extras install epel

## install nginx, git, certbot-nginx and go
sudo yum install git go certbot-nginx

## run certbot
sudo certbot certonly --manual --server https://acme-v02.api.letsencrypt.org/directory \
  --preferred-challenges dns-01 \
  -d 'nnix.io' -d '*.nnix.io'

Note: you'll have to deploy a couple TXT records as directed by Certbot for this.

## clone the repo

## move the nginx conf

###
you got interrupted here where you were going to make a repo and clone that to the host for nginx configs before you build out go-ssb-room

oh, and add that damn key to lastpass
###



## clone go-ssb-room
git clone https://github.com/ssb-ngi-pointer/go-ssb-room.git

## build go-ssb-room
cd go-ssb-room/cmd/server
go build

## copy binary to /usr/bin
sudo cp server /usr/bin/ssb-server