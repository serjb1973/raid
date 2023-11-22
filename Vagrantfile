# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "generic/centos7"
  (2..6).each do |i|
    config.vm.disk :disk, size: "250MB", name: "disk-#{i}"
  end
  config.vm.provision "shell", run: "once",  inline: <<-SHELL
    sudo yum install -y mdadm 
    sudo mdadm --create --verbose /dev/md0 -l 5 -n 5 /dev/sd{b,c,d,e,f}
    sudo mkdir /etc/mdadm
    sudo bash -c 'echo "DEVICE partitions" > /etc/mdadm/mdadm.conf'
    sudo bash -c "mdadm --detail --scan --verbose | awk '/ARRAY/ {print}' >> /etc/mdadm/mdadm.conf"
    sudo parted -s /dev/md0 mklabel gpt
    for i in $(seq 0 20 80); do
      sudo bash -c 'parted /dev/md0 mkpart primary ext4 '$i'% '`expr $i + 20`'%'
    done
    for i in $(seq 1 5); do 
      sudo mkfs.ext4 /dev/md0p$i; 
    done
    sudo mkdir -p /mnt/part{1,2,3,4,5}
    for i in $(seq 1 5); 
    do 
     sudo mount /dev/md0p$i /mnt/part$i; 
     sudo bash -c 'echo "/dev/md0p'$i' /mnt/part'$i'  ext4 defaults" >> /etc/fstab'
    done
  SHELL
end
