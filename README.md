# Gloo Gateway V2 Reproducer Template

## Installation

In the `./install/install-ggv2-with-helm.sh` script, update the name of the minikube profile in which you want to install the reproducer. This is currently required to upload the appropriate container images into the minikube K8S cluster.

Install Gloo Gateway:
```
cd install
./install-ggv2-with-helm.sh
```

Install the ExtAuth and RateLimit server in the `gloo-gateway-system` namespace:
```
./install-extauth-rl.sh
```

> NOTE
> The Gloo Gateway version that will be installed is set in a variable at the top of the `install/install-gloo-gateway-with-helm.sh` installation script.

## Setup the environment

Run the `install/setup.sh` script to setup the environment:

- Create the required namespaces
- Deploy the Gateway
- Deploy the ExtAuth GatewayExtension
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