$install_docker = <<INSTALL_DOCKER
echo Installing docker
curl -sSL --retry 5 --retry-delay 10 https://releases.rancher.com/install-docker/1.12.6.sh| sh
echo 'DOCKER_OPTS="-H 0.0.0.0:2376 -H unix:///var/run/docker.sock"'>>/etc/default/docker
service docker restart
sudo usermod -aG docker ubuntu
INSTALL_DOCKER

Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: $install_docker
  config.vm.network "forwarded_port", guest: 2376, host: 2376
  config.vm.box= "ubuntu/trusty64"
  config.vm.box_url = "ubuntu/trusty64"
end
