# kapp-controller imgkpg bundle
This repository provides the source to a imgpkg bundle for kapp-controller

## Image location
This image can be located in:

```
quay.io/failk8s/kapp-controller:v0.22.0
```

## Versions

- v0.20.0
- v0.21.0
- v0.22.0


## Build the image

- Download a new kapp-controller release file into [kapp-controller.yaml](./base-files/kapp-controller.yaml) from [kapp-controller releases page](https://github.com/vmware-tanzu/carvel-kapp-controller/releases)

- Test
  ```
  ytt -f .
  ```
- Update image reference, build and push the bundle
  ```
  kbld -f . --imgpkg-lock-output .imgpkg/images.yml
  imgpkg push --file-exclusion README.md --file-exclusion .git -b quay.io/failk8s/kapp-controller:v0.22.0 -f .
  ```

