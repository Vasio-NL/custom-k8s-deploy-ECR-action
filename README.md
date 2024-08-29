## Kubernetes deploy action

This Github Action deploys images from Amazon ECR to a kubernetes cluster.
This action is intended to be used with the custom [build and push to ECR action.](https://github.com/Vasio-NL/custom-build-and-push-ECR-action)

Fetches the latest version of the given image from a kubernetes configmap, then gets the image from Amazon ECR and pushes it to the kubernetes cluster.


### For developers: Updating the action
When making changes, make sure to tag new versions so they can be used in Github workflows. The action uses semantic versioning.

To tag the version (v1.0.3 in the example):

`git tag v1.0.3`

also update the major version tag (v1 in the example):

`git tag v1 -f`

When finished tagging, make sure to push the tags:

`git push --tags -f`
