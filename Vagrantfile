require 'json'

load 'config.rb'

CLUSTER = JSON.parse(File.read('cluster.json'))

Vagrant.configure('2') do |config|
  CLUSTER.each do |machine|
    config.vm.define machine['name'] do |c|
      c.vm.box = "coreos-%s" % $update_channel
      c.vm.box_url = "https://storage.googleapis.com/%s.release.core-os.net/amd64-usr/%s/coreos_production_vagrant.json" % [$update_channel, $image_version]
      c.vm.hostname = machine['name']
      c.vm.provider 'virtualbox' do |vb|
        vb.name = machine['name']
        vb.memory = $memory
        vb.cpus = $cpu
        vb.gui = $gui
      end
      c.vm.network 'private_network', ip: machine['ip']

      c.vm.synced_folder '.', '/vagrant', disabled: true

      c.ssh.insert_key = false
      c.ssh.forward_agent = true

      c.vm.provision :file, :source => "user-data", :destination => "/tmp/vagrantfile-user-data"
      c.vm.provision :shell, :inline => "mv /tmp/vagrantfile-user-data /var/lib/coreos-vagrant/", :privileged => true

    end
  end
end
