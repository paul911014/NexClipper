# Install NexClipper with HELM

## Install helm

```sh
$ curl https://raw.githubusercontent.com/helm/helm/master/scripts/get > get_helm.sh
$ chmod 700 get_helm.sh
$ ./get_helm.sh
```

> create service account and clusterrolebinding

```sh
$ kubectl -n kube-system create sa tiller
$ kubectl create clusterrolebinding tiller --clusterrole cluster-admin --serviceaccount=kube-system:tiller
```

> install tiller

```sh
$ helm init --service-account tiller
```

## Install chart

> update chart list

```sh
$ helm repo update
```

> download helm chart of NexClipper

```sh
$ git clone ...
```

> install the chart 

```sh
$ helm install <tgz name>
```
or
```sh
$ helm install --name <anything you want> <tgz name>
```

## Uninstall chart

```sh
$ helm ls
$ helm delete <chart name>
```

## Configuration

The following table lists the configurable parameters of the NexClipper chart and their default values.

|           Parameter                  |              Description                       |         Default               |
|--------------------------------------|------------------------------------------------|-------------------------------|
| `hostPath.influx`                    | Hostpath of influx                             | `/nfs/influxdb`               |
| `hostPath.mysql`                     | Hostpath of mysql                              | `/nfs/mysql`                  |
| `agent_endpoint.master`              | IP address of master node                      | `10.0.0.2`                    |
| `agent_endpoint.port`                | Port to use of master node                     | `32100`                       |
| `cluster.masterip`                   | IP address of master node                      | `10.0.0.2`                    |
| `cluster.masterport`                 | Port to use of master node                     | `6443`                        |
