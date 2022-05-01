# nnix.io scuttlebutt

Messaging fit for your journey around the Chagos Archipelago.

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

## install nginx, git, certbot and go
sudo yum install git go certbot


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