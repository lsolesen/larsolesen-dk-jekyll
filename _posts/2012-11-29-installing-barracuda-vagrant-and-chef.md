---
title: "Installing barracuda with vagrant and chef"
permalink: /content/installing-barracuda-vagrant-and-chef
language: da
tags:
  - boa
  - vagrant
  - chef
last_modified_at: 2012-11-29T15:32:45Z
---

Earlier I wrote [how you could easily install Barracuda](/node/357) on a VM created by Vagrant. I investigated a bit further because I have two development machines, so I wanted to replicate the environment with less hazzle on the second machine.

Enter chef
----------

With chef you can automate a lot of the settings. Like Vagrant, chef also uses Ruby as it's language. Luckily it is not too hard to grasp coming from php.

I created cookbooks/boa/recipes/default.rb with the following content ([notice the unauthorized use of the boa installer](http://drupal.org/node/1849604)):

```
Chef::Log.debug("Running barracuda recipe")

remote_file "/tmp/BOA.sh" do
  source "http://files.aegir.cc/BOA.sh.txt"
  mode 00755
end

execute "/tmp/BOA.sh" do
  creates "/usr/local/bin/boa"
end

execute "Run the BOA Installer o1" do
  command "boa in-stable local lars@email.dk aegir.local o1 mini"
end

execute "Run the BOA Installer o2" do
  command "boa in-stable local lars@email.dk aegir.local o2 mini"
end

execute "Run the BOA Installer o3" do
  command "boa in-stable local lars@email.dk aegir.local o3 mini"
end

(1..3).each do |boa_user|

  user "o#{boa_user}" do
    supports :manage_home => true
    home "/data/disk/o#{boa_user}"
    shell "/bin/bash"
  end

  directory "/data/disk/o#{boa_user}/.ssh" do
    owner "o#{boa_user}"
    group "users"
    mode 00700
    recursive true
  end

  execute "Add ssh key to user" do
    command "ssh-keygen -b 4096 -t rsa -N \"\" -f /data/disk/o#{boa_user}/.ssh/id_rsa"
    creates "/data/disk/o#{boa_user}/.ssh/id_rsa"
  end

  directory "/data/disk/o#{boa_user}/static" do
    owner "o#{boa_user}"
    group "users"
    mode 00755
    recursive true
  end

end

# Rebuild VirtualBox Guest Additions
# https://vagrantup.com/v1/docs/troubleshooting.html
execute "Rebuild VirtualBox Guest Additions" do
  command "sudo /etc/init.d/vboxadd setup"
end
```

When you have run that, I have a server setup with Barracuda and three octopus instances for my development purposes.

Mounting drives
---------------

To mount drives, I add the following to my Vagrantfile.

```
config.vm.share_folder "platforms-o1", "/data/disk/o1/static", "~/workspace/platforms", :extra => "dmode=777,fmode=777"
config.vm.share_folder "platforms-o2", "/data/disk/o2/static", "~/workspace/platforms", :extra => "dmode=777,fmode=777"
config.vm.share_folder "platforms-o3", "/data/disk/o3/static", "~/workspace/platforms", :extra => "dmode=777,fmode=777"
```

Now the drives has been mounted to the octopus users home directory. However, I am still [struggling with having the correct permissions given to the folders](https://github.com/lsolesen/boa-vagrant/issues/2).

I have shared the entire code at [github.com/lsolesen/boa-vagrant](http://github.com/lsolesen/boa-vagrant).
