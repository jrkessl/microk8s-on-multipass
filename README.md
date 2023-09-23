comandos:
sudo snap install multipass

multipass launch --name my-server --cloud-init ./cloud-init-microk8s.yaml --cpus 4 --memory 4G --disk 10G