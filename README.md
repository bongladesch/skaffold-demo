# skaffold-demo

This project shows a demo how you can use Skaffold for a local and CI/CD development flow.
It uses Docker to build images, the sync functionality to keep sources in sync during dev mode and Kustomize for deployment configuration.

If you want to learn more about Skaffold, please visit its website: https://kustomize.io/ .

This project uses Quarkus, the Supersonic Subatomic Java Framework.
If you want to learn more about Quarkus, please visit its website: https://quarkus.io/ .

## Prerequisites

The following tools must be installed before running this demo:

* `kubectl`
* `skaffold`

Also, you need to a remote k8s cluster (e.g. Minikube, AKS, EKS etc.) and configure your `kubectl` to this cluster.

In order to build and push on a remote k8s cluster you need to store your local and authenticated Docker config.json as a Secret in the namespace `build`:

```shell script
kubectl -n build create secret generic docker-config --from-file=/path/to/your/config.json
```

## Running the application in dev mode

You can run your application in dev mode that enables live coding with Skaffold on a remote cluster using:
```shell script
skaffold dev -p dev
```

> **_NOTE:_** The application will be available at: http://localhost:8080/hello

> **_NOTE:_**  Quarkus now ships with a Dev UI, which is available in dev mode only at http://localhost:8080/q/dev/

## Packaging and deploying the application to STAGE

The application can be packaged and deployed to stage using:

```shell script
skaffold run -p stage
```

> **_Note:_** Ensure the environment variable `VERSION` is set to the desired Docker image tag

> **_Note:_** The application is now available at http://localhost/hello

> **_Note:_** You can provide the option `--tail` to follow the logs of the deployment.

## Related Guides

- Skaffold: [Guides](https://skaffold.dev/docs/workflows/)
- Kustomize: [Guides](https://kubectl.docs.kubernetes.io/)
- Quarkus [Guides](https://quarkus.io/guides/)
