# external-sfsturbo

Scalable File Service (EFS) provides completely hosted sharable file storage for Elastic Cloud Servers (ECSs)
on Flexible Engine Cloud.
Compatible with the Network File System protocol, EFS is expandable to petabytes, features high performance,
and seamlessly handles data-intensive and bandwidth-intensive applications.

This repository hosts external sfsturbo provisioner for Kubernetes.

## Getting Started on Kubernetes

### Config

Default configuration file path:
```
/etc/config/cloud.conf
```
If you want to change the configuration file path
```
vi ./deploy/sfsturbo-provisioner/kubernetes/statefulset.yaml
```
and replace ```/etc/config/cloud.conf``` with your Cloud Config file in the line 79 of statefulset.yaml and replace the path ```/etc/config``` with your Cloud Config directory in the line 82 of statefulset.yaml.

#### configuration file format:
```
[Global]
auth-url=https://iam.{region}.prod-cloud-ocb.orange-business.com/v3
tenant-id=xxx
domain-name=xxx
username=xxx
password=xxx
region=xxx
type=(STANDARD/PERFORMANCE)
```
Description of configuration items：

To obtain the information, log in to your Flexible Engine account and choose My Credential -> API Credentials in the upper right corner.
```
tenant-id -> Project ID
domain-name -> 	Public_IES_x00454388
username -> IAM User Name
password -> password
region -> Project Name
type -> Select STANDARD or PERFORMANCE
```

### Deploy

```
kubectl create -f ./deploy/sfsturbo-provisioner/kubernetes/statefulset.yaml
```

Different than SFS, SFS turbo is not provisionned immediately but needs around 5 miuntes for getting the instance ready.

### Usage

```
kubectl create -f ./examples/sfsturbo-provisioner/kubernetes/example.yaml
```

## License

See the [LICENSE](LICENSE) file for details.
