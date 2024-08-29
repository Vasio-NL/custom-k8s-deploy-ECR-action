## Kubernetes deploy action

This Github Action deploys images from Amazon ECR to a kubernetes cluster.
This action is intended to be used with the custom [build and push to ECR action.](https://github.com/Vasio-NL/custom-build-and-push-ECR-action)

Fetches the latest version of the given image from a kubernetes configmap, then gets the image from Amazon ECR and pushes it to the kubernetes cluster.

### Example usage

The following is an example release job:

```
  release:
    runs-on: ubuntu-latest
    needs: [ build-app ]
    environment: ${{ github.ref_name }}
    steps:
      - uses: Vasio-NL/custom-k8s-deploy-ECR-action@v1
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          container-repository-name: vasio
          kube-config-base64: ${{ secrets.KUBE_CONFIG_B64 }}
```

The container repository name is the name that is prefixed to the image name. An example image:

`1234567890.dkr.ecr.eu-west-1.amazonaws.com/vasio/cool-project:latest`

In this example, the container repository name is `vasio` and the image name is `cool-project`.

### For developers: Updating the action
When making changes, make sure to tag new versions so they can be used in Github workflows. The action uses semantic versioning.

To tag the version (v1.0.3 in the example):

`git tag v1.0.3`

also update the major version tag (v1 in the example):

`git tag v1 -f`

When finished tagging, make sure to push the tags:

`git push --tags -f`
