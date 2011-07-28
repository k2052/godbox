require "rubygems"
require "json"   

Vagrant::Config.run do |config|   
  config.vm.box         = "base"
  config.vm.box_url     = "/Users/kenerickson/vmimages/lucid32.box"
  
  config.vm.provision :chef_solo do |chef|   
    chef.cookbooks_path = "cookbooks"
    chef.add_recipe("vagrant_main")  
    chef.add_recipe("nginx") 
    chef.add_recipe("git")   
    chef.add_recipe("monit")
    chef.add_recipe("ruby") 
    chef.add_recipe("unicorn")
    chef.add_recipe("redis")    
    # chef.add_recipe("iptables")  
    chef.add_recipe("gems") 
    chef.add_recipe("mongodb")  
    chef.json.merge!(JSON.parse(File.read('dna.json')))
  end        
  
  config.vm.forward_port("web", 80, 8080)
  # config.vm.forward_port("ftp", 21, 4567)
  # config.vm.forward_port("ssh", 22, 2222, :auto => true)
end           