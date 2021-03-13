1. Before run this script docker, kubectl and kind command should avialble on your local machine. To install these command please follow the below link.\
https://vineetcic.medium.com/set-up-local-kubernetes-cluster-with-kind-single-node-as-well-as-multi-node-6eb3573a5132 \
Run the script multi-node.sh under cluster directory in Local machine.
2. This script will take mode the 5 minutes to set up a cluster.
3. You can view the docker container running through the dokcer ps command : $ docker ps
4. View the three running nodes with kubectl commads: $kubect get nodes
5. We can modify /etc/hosts on the host to direct traffic to the kind cluster’s ingress controller. We’ll need to get the IP address of our kind node’s Docker container first by running:
docker container inspect $(docker ps -a | awk '{print $NF}' | grep control-plane) --format '{{ .NetworkSettings.Networks.kind.IPAddress }}'
Then add an entry to /etc/hosts with the IP address found that looks like:
172.18.0.2 php.cluster.in
Finally, we can curl php.cluster.in:
curl hphp.cluster.in

6. Kubeconfig File Locaion: ~/.kube/config
