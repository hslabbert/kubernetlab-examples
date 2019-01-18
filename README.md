# KUBERNETES ALL THE NETLABS!!!

"kubernetlab" is basically just running
[vrnetlab](https://github.com/plajjan/vrnetlab) on Kubernetes.  There really
isn't a whole bunch of magic required, just tying together services,
deployments, and vrnetlab containers in a kubernetes-y way.

Ideally this ~must~ ~should~ might get fleshed out to suck in your inventory
(Ansible, $other) and use that to determine the hosts to spin up as well as the
links between nodes and then do any or all of:

* generate a dot graph for the deployment to use as the reference point
* spit out the needed yaml for deployments, services, etc.
* actually push the deployments to a k8s API endpoint of your choosing

For now, basic examples are provided with nxosv.  I can't distribute packaged
nxosv containers, so fix-up the docker registry path in the manifests as needed
until I get around to making helm-type things happen.

The network-policy.yaml manifest is optional if you need/want to isolate your
kubernetlab namespace from the rest of the world.  I've found this to be helpful
in cases where I want to test out deployments/scenarios using device names from a
real/live environment but obviously want to avoid accidentally reaching out from
inside the kubernetlab environment to the "real world".
