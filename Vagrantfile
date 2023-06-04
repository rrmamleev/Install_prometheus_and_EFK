Vagrant.configure("2") do |config|

#  config.vm.provision "file", source: "key/id_rsa.pub", destination: "/home/vagrant/.ssh/"

  config.vm.define "host" do |host|
    host.vm.box = "ubuntu/focal64"
    host.vm.hostname = "host"
    host.vbguest.auto_update = false
    host.vm.network "private_network", ip: "192.168.50.2"
    host.vm.provision "file", source: "key/id_rsa.pub", destination: "/home/vagrant/.ssh/"
    host.vm.provision "shell", inline: <<-SHELL
      cat /home/vagrant/.ssh/id_rsa.pub >> /home/vagrant/.ssh/authorized_keys
#      sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/#g' /etc/ssh/sshd_config
#      systemctl restart sshd.service
    SHELL
    host.vm.provision "ansible" do |ansible|
        ansible.playbook = "playbook.yaml"
    end
  end

end
