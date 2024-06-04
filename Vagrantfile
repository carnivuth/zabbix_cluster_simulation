Vagrant.configure('2') do |config|
  config.vm.box = 'ubuntu/jammy64'
  config.ssh.insert_key = true

  # bootstrap node of cluster
  config.vm.define 'zabbix-server' do |machine|
    machine.vm.hostname = 'zabbix-server'
    machine.vm.network 'forwarded_port', id: 'ssh', host: 2221, guest: 22
    machine.vm.network 'forwarded_port', id: 'zabbix-console', host: 8888, guest: 80
    machine.vm.network 'private_network', virtualbox__intnet: 'zabbix-cluster', ip: '10.0.0.10'
  end

  # clients
  config.vm.define 'monitored-node-1' do |machine|
    machine.vm.hostname = 'monitored-node-1'
    machine.vm.network 'forwarded_port', id: 'ssh', host: 2222, guest: 22
    machine.vm.network 'private_network', virtualbox__intnet: 'zabbix-cluster', ip: '10.0.0.20'
    machine.vm.disk :disk, name: 'storage-1', size: '10GB'
  end
  config.vm.define 'monitored-node-2' do |machine|
    machine.vm.hostname = 'monitored-node-2'
    machine.vm.network 'forwarded_port', id: 'ssh', host: 2223, guest: 22
    machine.vm.network 'private_network', virtualbox__intnet: 'zabbix-cluster', ip: '10.0.0.30'
    machine.vm.disk :disk, name: 'storage-2', size: '10GB'
  end
  config.vm.define 'monitored-node-3' do |machine|
    machine.vm.hostname = 'monitored-node-3'
    machine.vm.network 'forwarded_port', id: 'ssh', host: 2224, guest: 22
    machine.vm.network 'private_network', virtualbox__intnet: 'zabbix-cluster', ip: '10.0.0.40'
    machine.vm.disk :disk, name: 'storage-4', size: '10GB'
  end
end
