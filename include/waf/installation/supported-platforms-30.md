| Platform                                                                                               | Installation options                  |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------- |
| NGINX `stable` installed on the 64-bit operating system from the list:<ul><li>Debian 9.x (stretch)</li><li>Debian 10.x (buster)</li><li>Ubuntu 18.04 LTS (bionic)</li><li>Ubuntu 20.04 LTS (focal)</li><li>CentOS 7.x</li><li>CentOS 8.x</li><li>Amazon Linux 2</li></ul> | <ul><li>[Module for NGINX `stable` from the NGINX repository](../waf-installation/nginx/dynamic-module.md)</li><li>[Module for NGINX `stable` from the Debian/CentOS repository](../waf-installation/nginx/dynamic-module-from-distr.md)</li></ul>                                                                                                                                              |
| NGINX Plus                                                                                             | <ul><li>[Module for NGINX Plus](../waf-installation/nginx-plus.md)</li></ul>                                                                                                        |
| Docker                                                                                                 | <ul><li>[Docker container with NGINX modules](../admin-en/installation-docker-en.md)</li><li>[Docker container with Envoy modules](../admin-en/installation-guides/envoy/envoy-docker.md)</li></ul>           |
| Kubernetes platform version 1.20 and lower                                                                              | <ul><li>[NGINX Ingress controller](../admin-en/installation-kubernetes-en.md)<br>You can deploy the Ingress controller on the Konvoy by D2IQ (formerly Mesosphere). The instructions mentioned above are suitable if you are deploying the Ingress controller with integrated Wallarm WAF services on the Konvoy. However, you may want to look at the [D2IQ's installation instructions](https://docs.d2iq.com/ksphere/konvoy/partner-solutions/wallarm/).</li><li>[Sidecar container](../admin-en/installation-guides/kubernetes/wallarm-sidecar-container.md)</li></ul>                                                                                                                                         |
| Cloud platforms                                                                                        | <ul><li>[AWS image](../admin-en/installation-ami-en.md)</li><li>[Google Cloud Platform image](../admin-en/installation-gcp-en.md)</li><li>[Yandex.Cloud image](../admin-en/installation-guides/install-in-yandex-cloud.md)</li></ul>                                                                                                                                              |
| Kong 1.4.3 and lower installed on the 64-bit operating system from the list:<br><ul><li>Debian 9.x (stretch)</li><li>Ubuntu 18.04 LTS (bionic)</li><li>CentOS 7.x</li></ul>                                            | <ul><li>[Module for Kong](../admin-en/installation-kong-en.md)</li></ul>                                                                                                                                         |