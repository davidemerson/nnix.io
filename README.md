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

### Note: you'll have to deploy a couple TXT records as directed by Certbot for this.

## clone the repo
git clone 

## move the nginx conf
sudo cp nginx.conf /etc/nginx/nginx.conf

## clone go-ssb-room
git clone https://github.com/ssb-ngi-pointer/go-ssb-room.git

## build go-ssb-room
cd go-ssb-room/cmd/server
go build

## copy binary to /usr/bin
sudo cp server /usr/bin/ssb-server

## involke ssb-server
sudo ssb-server -https-domain nnix.io -lishttp localhost:3005

###
next up, make that first user, and figure out how to get to the web interface, since you can't open another host on the same domain
###
