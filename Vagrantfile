Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "forwarded_port", guest: 5432, host: 5432
  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.provider "virtualbox" do |vb|
    vm.name = "gcs"
    vb.gui = false
    vb.memory = "1024"
    vb.cpus = 2
  end

  config.vm.define "db" do |db|
    db.vm.box = "postgresql"
  end

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y vim git
    sudo apt-get install -y python-pip python-dev libpq-dev postgresql postgresql-contrib
    sudo pip install django flake8 psycopg2
    sudo apt-get install -y postgresql
    sudo su - postgres -c "psql -f /vagrant/db-config.sql"
    sudo su - postgres -c 'echo "host all all 192.168.1.10/24 trust" >> /etc/postgresql/9.3/main/pg_hba.conf'
    sudo su - postgres -c "echo listen_addresses=\\'*\\' >> /etc/postgresql/9.3/main/postgresql.conf"
    sudo service postgresql restart
  SHELL

end
