# HokStack Helm Repository

![HokStack](https://raw.githubusercontent.com/hokstack/hok-helm/master/images/cover.png)


### Adding Hadoop on Kubernetes repository
```
$ helm repo add hok https://charts.hokstack.io
```

### Update procedure

To update simply update your helm repositories and check the latest version

```
$ helm repo update
```
### Repo search

You can then check for the latest version by searching your Helm repositories for the HokStack

```
$ helm search hok 
```

### Rollout for first team with default values

You can then check for the latest version by searching your Helm repositories for the HokStack

```
$ helm install hok/hokstack --name hok-team1 --set teamname=team1 --namespace team1
```

### Rollout for second team with default values

You can then check for the latest version by searching your Helm repositories for the HokStack

```
$ helm install hok/hokstack --name hok-team2 --set teamname=team2 --set metacontroller.crds.create=false --namespace team2
```

### Remove hadoop-on-kubernetes

Remove OneAgent custom resources and clean-up all remaining OneAgent Operator specific objects:

```
$ helm remove <release name> -n <namespace>
```


For more details on installing HokStack please see the [hok-helm readme](https://github.com/hokstack/hok-helm/blob/master/README.md).
