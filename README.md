# Getting Started

Inside ansible vm

```
git clone --depth 1 --branch v2.18.0 https://github.com/kubernetes-sigs/kubespray.git

cd kubespray

sudo pip3 install -r requirements.txt

ansible-playbook -i /vagrant/inventory/inventory.ini  --become --become-user=root cluster.yml
```
