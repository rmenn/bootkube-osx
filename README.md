# bootkube-osx
Coreos kubernetes cluster with bootkube

#### Instructions
- Grab the bootkube 0.12.0 verstion [here][1]
- Install `corectl` and `qcow-tool` both available via brew
- start `corectld start`
- download desired coreos image `corectl pull -c stable -v 1465.6.0`
- Render `./bootkube render --asset-dir local-cluster --api-servers=https://master-1.coreos.local:6443 --etcd-servers=https://master-1.coreos.local:2379 --network-provider=experimental-canal`
- Start `./bootkube-up local-cluster`
- use `corectl ps` grab the IP for the master-1 and update `/etc/hosts` ( have not figured out why the corectl dns resolution does not work )

#### Caveats

- Changing the api server name in the render command will require edits to bootkube-up
- CPU, Memory and Disk size of coreos is hardcoded
- ~~This uses the self-hosted etcd~~
- Volume for each coreos is at 6GB, which is again hardcoded
- etcd runs as single node on master-1

[1]:https://github.com/kubernetes-incubator/bootkube/releases/download/v0.12.0/bootkube.tar.gz
