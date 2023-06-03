Vagrant.configure("2") do |config|

#  config.vm.provision "file", source: "key/id_rsa.pub", destination: "/home/vagrant/.ssh/"

  config.vm.define "server" do |server|
    server.vm.box = "bento/centos-7.9"
    server.vm.hostname = "server"
    server.vbguest.auto_update = false
    server.vm.network "private_network", ip: "192.168.50.2"
    server.vm.provision "file", source: "key/id_rsa.pub", destination: "/home/vagrant/.ssh/"
    server.vm.provision "shell", inline: <<-SHELL
      cat /home/vagrant/.ssh/id_rsa.pub >> /home/vagrant/.ssh/authorized_keys
#      sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/#g' /etc/ssh/sshd_config
#      systemctl restart sshd.service
    SHELL
  end

end
