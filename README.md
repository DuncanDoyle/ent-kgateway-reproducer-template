# Solo Enterprise for Kgateway Reproducer Template

## Installation

In the `./install/install-ent-kgateway-with-helm.sh` script, update the name of the minikube profile in which you want to install the reproducer. This is currently required to upload the appropriate container images into the minikube K8S cluster.

Install Solo Enterprise for Kgateway:
```
cd install
./install-ent-kgateway-with-helm.sh
```

## Setup the environment

Run the `install/setup.sh` script to setup the environment:

- Create the required namespaces
- Deploy the Gateway
- Deploy the HTTPBin application
- Deploy the Reference Grants
- Deploy the HTTPRoute (K8S Gateway API)
- Deploy the AuthConfig and GlooTrafficPolicy

```
./setup.sh
```

## Access the HTTPBin application


```
./curl-request.sh
```

or

```
curl -v -H "Authorization: basic $(echo -n 'user:password' | base64)" http://api.example.com/get
```