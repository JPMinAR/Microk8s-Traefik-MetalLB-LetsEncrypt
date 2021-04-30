# Microk8s-Traefik-MetalLB-LetsEncrypt on a Raspberry Pi Cluster

## Installing microk8s as a HA cluster
So we can used snap I'm using Ubuntu 20.04 as the Raspberry Pi operating system. For instructions on how to build the cluster and add nodes see the instructions [on the Ubuntu site](https://ubuntu.com/tutorials/how-to-kubernetes-cluster-on-raspberry-pi#1-overview). It is key you set the [cgroup flag](https://microk8s.io/docs/install-alternatives#heading--arm) for microk8s to run properly.

`sudo snap install microk8s --classic --channel=latest/stable`

Note: In order to use the add-on version of Traefik you need to be at least on channel 1.20+

so if you are already running microk8s at minimum you need the following upgrade

`sudo snap refresh microk8s --classic --channel=1.20/stable`

The tutorital above doesn't go through a few housekeeping item like adding users to the microk8s group and permissions so maybe revisit thost items [here before continuing](https://microk8s.io/docs).

You will need to add at least 3 nodes to have a HA cluster you can find the latest documentation including the newly added _failure domains_ [on the microk8s site here](https://microk8s.io/docs/high-availability).

## Enable Helm3
So we'll need Helm for some items later so let's knock it out now.

`microk8s enable helm3`

