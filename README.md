# microk8s-on-multipass

This project is the simplest way to provision a Kubernetes cluster.  It uses Multipass to launch a VM in your computer, then MicroK8s to deploy a single-node Kubernetes cluster on it. 
1) Install Multipass in your machine
2) "Git clone" this project
3) In the project folder, run `multipass launch --name highlander --cloud-init ./cloud-init-microk8s.yaml --cpus 4 --memory 4G --disk 10G`
4) Log to your VM with `multipass shell highlander` then start playing with `k` kubectl commands like `k get namespaces`.
   
 Check other nice commands too: 
 - `multipass launch`
 - `multipass list`
 - `multipass shell <name>`
 - `multipass delete <name>`
 - `multipass purge <name>`
