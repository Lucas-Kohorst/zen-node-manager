# Ansible Installer

This is an ansible setup that will allow you to deploy as many zen nodes as you would like simultaneously. This is something that I wanted as dealing with multiple nodes individually would be an absolute nightmare

## Getting started

Install ansible on your system. The below `apt-get` assumes you are on an Ubuntu machine but you can do a quick google to find out how to install ansible on your OS.

```
apt-get install ansible
git clone https://github.com/adiman9/zen-node-manager.git
cd zen-node-manager/ansible/
```

Configure the hosts file with a list of all the (sub)domains for your zen nodes. You can take a look at `hosts.example` to see what the file should look like.

The below is an example

```
# Parameters passed to all hosts
[all:vars]
email=test@example.com
region=eu

[zen-nodes]
node.example.com fqdn=node.example.com stakeaddr=test nodetype=secure
node2.example.com fqdn=node3.example.com stakeaddr=test nodetype=secure
node3.example.com fqdn=node2.example.com stakeaddr=test nodetype=secure
```

Now run the installer, this will install the nodes on all of your listed hosts.

```
ansible-playbook -i hosts main.yml
```

When the installation completes, all your installed nodes details will be stored in /tmp/zen-node-results

```
cat /tmp/zen-node-results
```

It will list results similar to this:

```
localhost:

Shield Address:
zcNBdJxZnhTZMdiSQABYiW1wY2A8Swrq8TsauYLiyaShKD91GrZvn1dqAkhZ8USmAHoKNxhokeoYJZwJAtKjyeWN4BMNM6v

Balance:
  transparent: 0.00
  private: 0.00
  total: 0.00
```

Now send 0.05ZEN to the shield addresses on the nodes that currently have 0 balance.

### Upgrading

The installer has a handy way to update all of your zen-nodes:

```
ansible-playbook -i hosts upgrade.yml
```

This will upgrade restart the required services.

### Status

You may check the status of your nodes anytime with the command:

```
ansible-playbook -i hosts status.yml
```

This will report the node name, shield address, balance and current block.
