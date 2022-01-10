# Getting Started

Inside ansible vm (`vagrant ssh ansible`)

```bash
git clone --depth 1 --branch v2.18.0 https://github.com/kubernetes-sigs/kubespray.git

cd kubespray

sudo pip3 install -r requirements.txt

ansible-playbook -i /vagrant/inventory/inventory.ini  --become --become-user=root cluster.yml
```

Inside ctrl-node-00 vm (`vagrant ssh ctrl-node-00`)

```bash
sudo su
kubectl apply -f /vagrant/manifests
kubectl get pods -o wide # to see the IPs
```
