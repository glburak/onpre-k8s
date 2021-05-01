  
ENV['VAGRANT_NO_PARALLEL'] = 'yes'

  

Vagrant.configure(2) do |config|
  
  
  
  MasterCount = 2
  # Kubernetes Master Node
  (1..MasterCount).each do |i|
  config.vm.define "master#{i}" do |kmaster|
    kmaster.vm.box = "generic/ubuntu2004"
    kmaster.vm.hostname = "master#{i}"
    kmaster.vm.network "public_network", ip: "192.168.1.10#{i}"
    kmaster.vm.provider "virtualbox" do |v|
      v.name = "master#{i}"
      v.memory = 2048
      v.cpus = 2
      
      v.customize ["modifyvm", :id, "--audio", "none"]
    end
 
  end
end
  NodeCount = 2


  # Kubernetes Worker Nodes
  (1..NodeCount).each do |i|
    
    config.vm.define "worker#{i}" do |workernode|
      workernode.vm.box = "generic/ubuntu2004"
      workernode.vm.hostname = "worker#{i}"
      workernode.vm.network "public_network", ip: "192.168.1.10#{i+MasterCount}"
      workernode.vm.provider "virtualbox" do |v|
        v.name = "worker#{i}"
        v.memory = 4096
        v.cpus = 2
        
        v.customize ["modifyvm", :id, "--audio", "none"]
      end
      
    end
  end

end