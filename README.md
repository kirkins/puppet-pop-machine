# Puppet Deployment for IoT Pop Machines

## puppet-docker-stack

Docker-Compose setup for Puppet, PuppetDb, and 2 GUI applications
for monitoring. 

## external-node-classifier

This script will be placed on the puppet server and determines
how nodes will be classified.

## control-repo

Each branch on this repo contains the code a specific configuration.

For example if we wanted to have seperate configurations for coke &
pepsi based pop machines, we would create a branch for each.

The external node classifier determines which branch to apply to a
node which is checking in.

## control-repo-globals

When making a branch for each configuration type in the control-repo
you often have configurations, modules, or files you want to be accessible by
all branches. To simplify the process we've placed these in a seperate
repo

## pop-machine-gui

This is a very simple GUI that will represent the pop machine. I will
have it running on a raspberry pi with touch screen. Inventory for each
pop type will be recorded each time a button is pressed.

The raspberry pi will be running puppet agent and check into the puppet
server on regular intervals. From the puppet server we will be able to
monitor revenue, inventory, and the gereral state of the linux system
running the machine.

The GUI will be used to demonstrate the switching of a machine from one
configuration group to another. For example serving a new mountain dew
type on a select group of machines.


### Note on webhooks

Another good addition to this setup is the use of adnanh/webhook
it's Go based executable that allows you to map endpoints on a port
to bash commands. 

You should have webhooks connecting control-repo and control-repo-globals
to the puppet server.

https://github.com/adnanh/webhook
