
## Debug

```shell
helm template charts/general --values examples/full-example.yaml --debug
```

## Lint

```shell
helm lint charts/general --values examples/full-example.yaml
```
## Kube score

[Kube score](https://github.com/zegl/kube-score)

```shell
helm template charts/general --values examples/full-example.yaml | docker run -i -v $(pwd):/project zegl/kube-score:v1.17.0 score --output-format ci -
```

## Unit Testing

We use [Helm Unittest](https://github.com/helm-unittest/helm-unittest) library for unit testing

Install:
```shell
helm plugin install https://github.com/helm-unittest/helm-unittest.git
```

Run:
```shell
helm unittest ./charts/general
```

## Local testing

Testing with KIND

```shell
kind create cluster
```

```shell
helm --kube-context kind-kind upgrade --install nginx charts/general --values examples/nginx.yaml
```