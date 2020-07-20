Vagrant.configure("2") do |config|
  config.vm.box = "StefanScherer/windows_10"

  # Bridge to the main network
  config.vm.network "public_network", bridge: "en0"

  config.vm.provider "vmware_fusion" do |v|
    v.gui = true
    # Enable "Enable hypervisor applications in this virtual machine"
    # Allows VirtualBox to run in the VMWare host
    # v.vhv.enable = "TRUE"
  end

  # config.vm.provision "gitconfig", type: "file", source: "~/.gitconfig", destination: "$HOME/.gitconfig"
  # config.vm.provision "id_rsa", type: "file", source: "~/.ssh/id_rsa", destination: "$HOME/.ssh/id_rsa"
  # config.vm.provision "id_rsa_pub", type: "file", source: "~/.ssh/id_rsa.pub", destination: "$HOME/.ssh/id_rsa.pub"
  # config.vm.provision "known_hosts", type: "file", source: "~/.ssh/known_hosts", destination: "$HOME/.ssh/known_hosts"

  # RunOnce provisioners
  # Must be Administrator for this next command
  config.vm.provision "locale", type: "shell", inline: "C:/vagrant/Scripts/set-local-time.ps1", args: "C:\vagrant\Scripts\UKRegion.xml", run: "once", privileged: true
  config.vm.provision "choco", type: "shell", inline: "Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))", run: "once", privileged: true
  config.vm.provision "vcredist-all", type: "shell", inline: "choco install vcredist-all --yes", run: "never", privileged: true
  config.vm.provision "vcredist2012", type: "shell", inline: "choco install vcredist2012 --yes", run: "never", privileged: true
  config.vm.provision "python354", type: "shell", inline: "choco install python --version=3.5.4 --yes", run: "never", privileged: true
  config.vm.provision "vscode", type: "shell", inline: "choco install vscode --yes", run: "never", privileged: true
  config.vm.provision "wireshark", type: "shell", inline: "choco install winpcap wireshark --yes", run: "never", privileged: true


  # Its easy to just do: vagrant powershell -c "c:/vagrant/update.ps1 -scheduletime 20191119T121000"
  # config.vm.provision "download", type: "shell", inline: "c:/vagrant/update.ps1", args: ENV['SHELL_ARGS'], run: "never"
end