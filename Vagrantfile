Vagrant.configure('2') do |config|
  config.vm.box = 'ubuntu/xenial64'
  config.vm.box_check_update = true

  config.vm.provider 'virtualbox' do |vb|
    vb.gui = false
    vb.memory = '2048'
  end

  # Mount scratch directory and Chef cookbook(s).
  config.vm.synced_folder '../ogawa', '/opt/ogawa'

  # Bus the provisioning cookbook to the machine.
  config.vm.provision 'file', source: './om-env-ogawa', destination: '/var/tmp/provisioning/'

  # Provision the VM with Chef.
  config.vm.provision 'shell', path: 'deploy-local.sh'
end
