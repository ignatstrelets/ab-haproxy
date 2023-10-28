# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.define "haproxy" do |haproxy|
    haproxy.vm.provider :virtualbox do |v|
      v.name = "haproxy"
      v.memory = "1024"
      v.cpus = "1"
    end
    haproxy.vm.hostname = "haproxy"
    haproxy.vm.network "private_network", ip: "192.168.4.4"
    haproxy.vm.network "forwarded_port", guest: 80, host: 8000
    haproxy.vm.network "forwarded_port", guest: 2812, host: 2812
  end
  config.vm.define "logstash" do |logstash|
    logstash.vm.provider :virtualbox do |v|
      v.name = "logstash"
      v.memory = "1024"
      v.cpus = "1"
    end
    logstash.vm.hostname = "logstash"
    logstash.vm.network "private_network", ip: "192.168.4.5"
    logstash.vm.network "forwarded_port", guest: 9200, host: 9200
  end
  config.vm.define "webui" do |webui|
      webui.vm.provider :virtualbox do |v|
        v.name = "webui"
        v.memory = "1024"
        v.cpus = "1"
      end
      webui.vm.hostname = "webui"
      webui.vm.network "private_network", ip: "192.168.4.6"
      webui.vm.network "forwarded_port", guest: 80, host: 8002
      webui.vm.network "forwarded_port", guest: 5601, host: 5601
      webui.vm.network "forwarded_port", guest: 514, host: 514
    end
end
