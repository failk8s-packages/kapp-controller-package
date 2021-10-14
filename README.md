# kapp-controller-package

This package provides kapp-controller functionality using [kapp-controller](https://carvel.dev/kapp-controller/docs/latest/).

## Components

* kapp-controller

## Configuration

The following configuration values can be set to customize the kapp-controller installation.

### Global

| Value | Required/Optional | Description |
|-------|-------------------|-------------|
| `namespace` | Optional | The namespace in which to deploy kapp-controller. |

## Usage Example

This walkthrough guides you through using kapp-controller...

__NOTE__: `develop` version of the package needs to comply with semver, hence the package will be versioned as `0.0.0+develop`

## Test in minikube

Start minikube:
```
minikube start
```

Install this version of kapp-controller:
```
ytt --data-values-file src/example-values/minikube.yaml -f target/bundle/config | kubectl apply -f -
```

## Test in TCE or TKG
This package can be used to replace kapp-controller in Tanzu Community Edition or Tanzu Kubernetes Grid.
[Follow instructions here](https://tanzucommunityedition.io/docs/latest/upgrade-kapp-controller/)

## Develop checklist

1. Update your [config.json](./config.json) with the package info
2. Add [overlays](./src/bundle/config/overlays/) and [values](./src/bundle/config/values.yaml)
3. Test your bundle: `ytt --data-values-file src/example-values/minikube.yaml  -f target/bundle/config` providing a sample values file from [example-values](./src/examples-values/)
4. Build your bundle `./hack/build.sh`
5. Add it to the [failk8s-repo](https://github.com/failk8s-packages/failk8s-repo) and publish the new repo and test the package from there, or [test with local files](./target/test)

**NOTE**: `develop` versions will not be image locked and will have a version of 0.0.0+develop to comply with semver.