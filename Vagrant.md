## Create VM
```bash
#  Initialize Vagrant with a Vagrantfile and ./.vagrant directory, using no specified base image. Before you can do vagrant up, you'll need to specify a base image in the Vagrantfile.
vagrant init
# Initialize Vagrant with a specific box. To find a box, go to the public Vagrant box catalog. When you find one you like, just replace it's name with boxpath. For example, vagrant init ubuntu/trusty64.
vagrant init <boxpath>
```

## Run VM
```bash
## Starts vagrant environment (also provisions only on the FIRST vagrant up)
vagrant up
## Resume a suspended machine (vagrant up works just fine for this as well)
vagrant resume
## Forces reprovisioning of the vagrant machine
vagrant provision
## Restarts vagrant machine, loads new Vagrantfile configuration
vagrant reload
## Restart the virtual machine and force provisioning
vagrant reload --provision
```

## Stop VM
```bash
## Stops the vagrant machine
vagrant halt
## Suspends a virtual machine (remembers state)
vagrant suspend
```

## Cleaning up VM
```bash
## Stops and deletes all traces of the vagrant machine
vagrant destroy
## Stops and deletes all traces of the vagrant machine without confirmation
vagrant destroy -f
```

## Manage Boxes
```bash
## See a list of all installed boxes on your computer
vagrant box list
## Download a box image to your computer
vagrant box add <name> <url>
## Check for updates vagrant box update
vagrant box outdated
## Deletes a box from the machine
vagrant boxes remove <name>
## Packages a running virtualbox env in a reusable box
vagrant package
```

## Saving Progress
```bash
## Allows us to save so that we can rollback at a later time (-- vm-name is often default)
vagrant snapshot save [options] [vm-name] <name>
```

## Tips
```bash
## Get the vagrant version
vagrant -v
## Outputs status of the vagrant machine
vagrant status
## Outputs status of all vagrant machines
vagrant global-status
## Same as above, but prunes invalid entries
vagrant global-status --prune
## Use the debug flag to increase the verbosity of the output
vagrant provision --debug
## Yes, vagrant can be configured to deploy code!
vagrant push
## Runs vagrant up, forces provisioning and logs all output to a file
vagrant up --provision | tee provision.log
```
