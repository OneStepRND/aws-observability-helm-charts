## Why

This is used by the backend EKS cluster on terraform.

Had to use patched version to fix https://github.com/aws-observability/helm-charts/issues/113

OneStep fork merges https://github.com/aws-observability/helm-charts/pull/78 into the upstream tag amazon-cloudwatch-observability-3.2.0 and creates tag amazon-cloudwatch-observability-3.2.0-patched

## How to publish a version

```bash
GIT_REF=amazon-cloudwatch-observability-3.2.0-patched
git checkout $GIT_REF
helm dependency update charts/amazon-cloudwatch-observability
helm package charts/amazon-cloudwatch-observability
git checkout gh-pages
helm repo index . --url https://onesteprnd.github.io/aws-observability-helm-charts
git add .
git commit -m "GH pages: added version to $GIT_REF"
git push origin gh-pages
```