Vagrant.configure("2") do |config|
    config.vm.box = "geerlingguy/centos7"

    config.ssh.insert_key = false

    config.vm.synced_folder ".", "/vagrant", disabled: true

    config.vm.provider :virtualbox do |v|
        v.memory = 256
        v.linked_clone = true
    end

    # App server 1
    config.vm.define "app1" do |app|
        app.vm.hostname = "orc-app1.test"
        app.vm.network :private_network, ip: "192.168.56.10"
    end
    # App server 2
    config.vm.define "app2" do |app|
        app.vm.hostname = "orc-app2.test"
        app.vm.network :private_network, ip: "192.168.56.11"
    end
    # DB Server
    config.vm.define "db1" do |db|
        db.vm.hostname = "orc-db1.test"
        db.vm.network :private_network, ip: "192.168.56.12"
    end
end