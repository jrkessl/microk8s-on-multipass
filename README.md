
# microk8s-on-multipass

This project is the simplest way to provision a Kubernetes cluster.  It uses Multipass to launch a VM (virtual machine) in your computer, then MicroK8s to deploy a single-node Kubernetes cluster on it. 
1) Install Multipass in your machine
2) Download this project and get into its folder
3) In the project folder, run `multipass launch --name highlander --cloud-init ./cloud-init-microk8s.yaml --cpus 4 --memory 4G --disk 10G`  

If you get an error like `launch failed: KVM support is not enabled on this machine.` it's because virtualization is often disabled from the factory in a new laptop or motherboard. After enabling it once for your computer, you don't need to worry about it any more. Google "how to enable virtualization" and your computer model / motherboard model for instructions on enabling virtualization.

4) Log to your VM with `multipass shell highlander` then start playing with `k` kubectl commands like `k get namespaces`.
   
 Check other useful Multipass commands to work with your VMs: 
 - `multipass launch` to just launch a VM with default settings
 - `multipass list` to list your VMs
 - `multipass shell <name>` to log into a VM
 - `multipass delete <name>` to delete a VM
 - `multipass purge` to get rid of your deleted VMs
 - `microk8s config > ~/.kube/config` to generate the kubeconfig file for other apps (such as Helm, K9s) to access your cluster.
 - `multipass mount <local folder> <instance>:<target folder>` To mount a folder from your computer (`local folder`) into the filesystem of your VM. For `instance` put the name of the VM you created. In this example, the name would be `multipass`. 
 - `microk8s enable metallb` to enable metallb add-on. It will allow you to create working load balancers. While enabling metallb, it will ask for an IP range. In this example, the IP range would be `172.22.208.91-172.22.208.100`.
