# Installation of the WAF node from DEB or RPM packages on Azure

This quick guide provides the steps to install the WAF node from the source packages on a separate Azure instance. By following this guide, you will create an instance from the supported operating system image and install the Wallarm WAF node on this operating system.

!!! warning "The instructions limitations"
    These instructions do not cover the configuration of load balancing and WAF node autoscaling. If setting up these components yourself, we recommend that you review the [Azure instructions](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/tutorial-load-balancer).

## Requirements

* Active Azure subscription
* Access to the account with the **Administrator** or **Deploy** role and two‑factor authentication disabled in the Wallarm Console for the [EU Cloud](https://my.wallarm.com/) or [US Cloud](https://us1.my.wallarm.com/)

## WAF node installation options

Since the WAF node operates as the web server or API gateway module, web server or API gateway packages should be installed on the operating system along with the WAF node packages.

You can select the web server or API gateway that is the most suitable for your application architecture from the following list:

* [Install the WAF node as the NGINX Stable module](#installing-the-waf-node-as-the-nginx-stable-module)
* [Install the WAF node as the NGINX Plus module](#installing-the-waf-node-as-the-nginx-plus-module)
* [Install the WAF node as the Kong module](#installing-the-waf-node-as-the-kong-module)

## Installing the WAF node as the NGINX Stable module

To install the WAF node as the NGINX Stable module in the Azure instance:

1. Create an Azure instance from the operating system image supported by Wallarm following the [Azure instructions](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-portal):

    * Debian 9.x Stretch
    * Debian 10.x Buster
    * Ubuntu 16.04 Xenial
    * Ubuntu 18.04 Bionic
    * CentOS 7.x
    * CentOS 8.x
2. Connect to the created instance following the [Azure instructions](https://docs.microsoft.com/en-us/azure/bastion/bastion-connect-vm-ssh).
3. In the instance, install the packages of NGINX Stable and Wallarm WAF node following the [Wallarm instructions](../../../waf-installation/nginx/dynamic-module.md).

To install the postanalytics module in a separate instance, please repeat steps 1-2 and install the postanalytics module following the [Wallarm instructions](../../../admin-en/installation-postanalytics-en.md).

## Installing the WAF node as the NGINX Plus module

To install the WAF node as the NGINX Plus module in the Azure instance:

1. Create an Azure instance from the operating system image supported by Wallarm following the [Azure instructions](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-portal):

    * Debian 9.x Stretch
    * Debian 10.x Buster
    * Ubuntu 16.04 Xenial
    * Ubuntu 18.04 Bionic
    * CentOS 7.x
    * CentOS 8.x
2. Connect to the created instance following the [Azure instructions](https://docs.microsoft.com/en-us/azure/bastion/bastion-connect-vm-ssh).
3. In the instance, install the packages of NGINX Plus and Wallarm WAF node following the [Wallarm instructions](../../../waf-installation/nginx/dynamic-module.md).

To install the postanalytics module in a separate instance, please repeat steps 1-2 and install the postanalytics module following the [Wallarm instructions](../../../admin-en/installation-postanalytics-en.md).

## Installing the WAF node as the Kong module

To install the WAF node as the Kong module in the Azure instance:

1. Create an Azure instance from the operating system image supported by Wallarm following the [Azure instructions](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-portal):

    * Debian 9.x Stretch
    * Ubuntu 16.04 Xenial
    * Ubuntu 18.04 Bionic
    * CentOS 7.x
2. Connect to the created instance following the [Azure instructions](https://docs.microsoft.com/en-us/azure/bastion/bastion-connect-vm-ssh).
3. In the instance, install Kong of version 1.4.3 or lower following the [Kong instructions](https://konghq.com/get-started/#install).
4. In the instance, install the packages of Wallarm WAF node following the [Wallarm instructions](../../../admin-en/installation-kong-en.md).

To install the postanalytics module in a separate instance, please repeat steps 1-2 and install the postanalytics module following the [Wallarm instructions](../../../admin-en/installation-postanalytics-en.md).
