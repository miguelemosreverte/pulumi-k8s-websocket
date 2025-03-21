# k8s-websocket
Kubernetes | Websocket

### HOW TO RUN LOCAL
`minikube start --driver=docker`

`sh script.local.deploy.sh`

```
sh script.local.deploy.sh
Building Docker image...
[+] Building 1.9s (11/11) FINISHED                                                                                                          docker:desktop-linux
 => [internal] load build definition from Dockerfile                                                                                                        0.0s
 => => transferring dockerfile: 148B                                                                                                                        0.0s
 => [internal] load metadata for docker.io/library/node:14                                                                                                  1.4s
 => [auth] library/node:pull token for registry-1.docker.io                                                                                                 0.0s
 => [internal] load .dockerignore                                                                                                                           0.0s
 => => transferring context: 2B                                                                                                                             0.0s
 => [1/5] FROM docker.io/library/node:14@sha256:a158d3b9b4e3fa813fa6c8c590b8f0a860e015ad4e59bbce5744d2f6fd8461aa                                            0.0s
 => => resolve docker.io/library/node:14@sha256:a158d3b9b4e3fa813fa6c8c590b8f0a860e015ad4e59bbce5744d2f6fd8461aa                                            0.0s
 => [internal] load build context                                                                                                                           0.1s
 => => transferring context: 1.05MB                                                                                                                         0.1s
 => CACHED [2/5] WORKDIR /app                                                                                                                               0.0s
 => CACHED [3/5] COPY package*.json ./                                                                                                                      0.0s
 => CACHED [4/5] RUN npm install                                                                                                                            0.0s
 => [5/5] COPY . .                                                                                                                                          0.1s
 => exporting to image                                                                                                                                      0.2s
 => => exporting layers                                                                                                                                     0.1s
 => => exporting manifest sha256:f2352894c06f43918db2187ce0bfcec96d749f588e562388ecb1a39120112531                                                           0.0s
 => => exporting config sha256:295da454e1049d51325ff728db4cf25171318ed0886edc8e5b2d96174d28f6f4                                                             0.0s
 => => exporting attestation manifest sha256:120a2178c7690ea71c6c34ff93fd14efe94322691247eb849d9b065dd97c557c                                               0.0s
 => => exporting manifest list sha256:cb7d14691ac028ac581c4686977fa2eecf980fea9bcfde1159653e5b6325d485                                                      0.0s
 => => naming to docker.io/library/chat-app:v1                                                                                                              0.0s
 => => unpacking to docker.io/library/chat-app:v1                                                                                                           0.1s
Loading image into Minikube...
Applying Kubernetes manifests...
deployment.apps/chat-app unchanged
service/chat-app unchanged
Waiting for deployment to be ready...
deployment "chat-app" successfully rolled out
Getting service URL...
http://127.0.0.1:55566
❗  Because you are using a Docker driver on darwin, the terminal needs to be open to run it.

```

![image](https://github.com/user-attachments/assets/40678070-4a4f-4636-ae34-c3d27ff39345)


`sh script.local.teardown.sh`

```
sh script.local.teardown.sh
Deleting Kubernetes resources...
service "chat-app" deleted
deployment.apps "chat-app" deleted
Removing Docker image from Minikube...
85d2c0713386
Untagged: chat-app:v1
Deleted: sha256:65fd22c19056e9a78124d5affb2a609576ffca9d17c1882b1fce36eb7af9ba4c
Deleted: sha256:5e4ed9414b44971b20efb49a876303c7f1fdd2117055bc77f4e71627c5d1c12a
Deleted: sha256:b6513484eda5cc26841625b4cc2846a341716b27cae3c19b349cc0d0bdc3ca5c
Deleted: sha256:d3af7c2fd3c8781ef9a071e19ff9585563549a066a6b21b0fa2e5d87a241d5b9
Deleted: sha256:a9130e43d44421561a5e4c9c1782046c93dc7b58bfd57d29c52db8d8af29f2a3
Deleted: sha256:f69d6bf00a1c472f6472be8eba1d3dc396b816d688baa60dbad81240a5f14c43
Deleted: sha256:5b6a27cef4553269c42631db5e9653eceb4766a6d8370cb3dbf1b4d29e3180bc
Deleted: sha256:02cbdc3d81cb2a7d947c13d6698e06b70d16dad3a04f2519256f79b891e8ddd8
Deleted: sha256:6107490ef2a1e69410254464af66ddd0311b4d6334d9d65190ceb95ae9cc9d64
Deleted: sha256:fbdf3ab94318785d8321f27ec857e75b4d7113642e5956548428e4218fbef7a9
Deleted: sha256:80bdb74df15a59fa9577d151dde713466a08830a37c4c4351dc329e196205ac0
Deleted: sha256:f1d41a64e19a07475d4aadc7d5a3dcfe0d5c8c72fab4895acc29578c78284c7f
Deleted: sha256:32a2a6e1d286c920e403f1606cbf11c296467e34e19d53900dd82a8197349266
Deleted: sha256:173621e7addd9a122d7aa8c00c6741b6b4426b7b76d65cd26e33c42defc8f4d9
Teardown complete.
```


##### HOW TO RUN REMOTE

`sh script.remote.deploy.gcloud.sh`

```
terraform apply
data.google_client_config.default: Reading...
module.gke.data.google_container_engine_versions.region: Reading...
module.gke.data.google_compute_zones.available[0]: Reading...
data.google_client_config.default: Read complete after 0s [id=projects/developer-test-02/regions/us-central1/zones/]
module.gke.data.google_compute_zones.available[0]: Read complete after 1s [id=projects/developer-test-02/regions/us-central1]
module.gke.data.google_container_engine_versions.zone: Reading...
module.gke.data.google_container_engine_versions.region: Read complete after 1s [id=2025-01-21 05:53:56.104834 +0000 UTC]
module.gke.data.google_container_engine_versions.zone: Read complete after 1s [id=2025-01-21 05:53:56.583857 +0000 UTC]

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # helm_release.nginx_ingress will be created
  + resource "helm_release" "nginx_ingress" {
      + atomic                     = false
      + chart                      = "ingress-nginx"
      + cleanup_on_fail            = false
      + create_namespace           = true
      + dependency_update          = false
      + disable_crd_hooks          = false
      + disable_openapi_validation = false
      + disable_webhooks           = false
      + force_update               = false
      + id                         = (known after apply)
      + lint                       = false
      + manifest                   = (known after apply)
      + max_history                = 0
      + metadata                   = (known after apply)
      + name                       = "nginx-ingress"
      + namespace                  = "ingress-nginx"
      + pass_credentials           = false
      + recreate_pods              = false
      + render_subchart_notes      = true
      + replace                    = false
      + repository                 = "https://kubernetes.github.io/ingress-nginx"
      + reset_values               = false
      + reuse_values               = false
      + skip_crds                  = false
      + status                     = "deployed"
      + timeout                    = 300
      + verify                     = false
      + version                    = "4.7.1"
      + wait                       = true
      + wait_for_jobs              = false
    }

  # kubernetes_deployment.websocket_demo will be created
  + resource "kubernetes_deployment" "websocket_demo" {
      + id               = (known after apply)
      + wait_for_rollout = true

      + metadata {
          + generation       = (known after apply)
          + labels           = {
              + "app" = "websocket-demo"
            }
          + name             = "websocket-demo-deployment"
          + namespace        = "default"
          + resource_version = (known after apply)
          + uid              = (known after apply)
        }

      + spec {
          + min_ready_seconds         = 0
          + paused                    = false
          + progress_deadline_seconds = 600
          + replicas                  = "1"
          + revision_history_limit    = 10

          + selector {
              + match_labels = {
                  + "app" = "websocket-demo"
                }
            }

          + template {
              + metadata {
                  + generation       = (known after apply)
...

Outputs:

ingress_controller_ip = "35.239.177.203"
ingress_demo_url = "http://35.239.177.203/"
kubeconfig_path = "kubeconfig.yaml"
kubectl_command = "gcloud container clusters get-credentials my-gke-cluster --region us-central1 --project developer-test-02"
```


![Screenshot 2025-01-21 at 07 10 54](https://github.com/user-attachments/assets/8e80557e-da7b-4d71-8cde-a9a8ea0c7e8b)

`sh script.remote.teardown.sh`

```
...
```

`kubectl --kubeconfig=./kubeconfig.yaml get pods`
