[waf-mode-instr]:                   ../admin-en/configure-wallarm-mode.md
[logging-instr]:                    ../admin-en/configure-logging.md
[proxy-balancer-instr]:             ../admin-en/using-proxy-or-balancer-en.md
[process-time-limit-instr]:         ../admin-en/configure-parameters-en.md#wallarm_process_time_limit
[allocating-memory-guide]:          ../admin-en/configuration-guides/allocate-resources-for-waf-node.md
[enable-libdetection-docs]:         ../admin-en/configure-parameters-en.md#wallarm_enable_libdetection

# Updating the running Docker NGINX- or Envoy-based image

These instructions describe the steps to update the running Docker NGINX- or Envoy-based image to the version 3.0.

!!! warning "Using credentials of already existing WAF node"
    We do not recommend to use the already existing WAF node of the previous version. Please follow these instructions to create a new WAF node of the version 3.0 and deploy it as the Docker container.

!!! warning "Breaking changes and skipping partner WAF node update"
    * The WAF node 3.0 is **totally incompatible with previous WAF node versions**. Before updating the modules up to 3.0, please carefully review the list of [WAF node 3.0 changes](what-is-new.md) and consider a possible configuration change.
    * We do NOT recommend updating [partner WAF node](../partner-waf-node/overview.md) up to version 3.0, since most changes will be fully supported only in partner WAF node [3.2](versioning-policy.md#version-list).

## Requirements

--8<-- "../include/waf/installation/requirements-docker.md"

## Step 1: Inform Wallarm technical support that you are updating WAF node modules

Please inform [Wallarm technical support](mailto:support@wallarm.com) that you are updating WAF node modules up to 3.0 and ask to enable new IP lists logic for your Wallarm account. When new IP lists logic is enabled, please open the Wallarm Console and ensure that the section [**IP lists**](../user-guides/ip-lists/overview.md) is available.

## Step 2: Download the updated WAF node image

=== "NGINX-based image"
    ``` bash
    docker pull wallarm/node:3.0.0-2
    ```
=== "Envoy-based image"
    ``` bash
    docker pull wallarm/envoy:3.0.0-1
    ```

## Step 3: Stop the running container

```bash
docker stop <RUNNING_CONTAINER_NAME>
```

## Step 4: Run the container using the updated image

1. Migrate whitelists and blacklists configuration from previous WAF node version to 3.0 following the [instructions](migrate-ip-lists-to-node-3.md).
2. Run the container using the updated image. You can pass the same configuration parameters that were passed when running a previous image version except for the `WALLARM_ACL_ENABLE` variable.

    There are two options for running the container using the updated image:

    * **With the environment variables** specifying basic WAF node configuration
        * [Instructions for the NGINX-based Docker container →](../admin-en/installation-docker-en.md#run-the-container-passing-the-environment-variables)
        * [Instructions for the Envoy-based Docker container →](../admin-en/installation-guides/envoy/envoy-docker.md#run-the-container-passing-the-environment-variables)
    * **In the mounted configuration file** specifying advanced WAF node configuration
        * [Instructions for the NGINX-based Docker container →](../admin-en/installation-docker-en.md#run-the-container-mounting-the-configuration-file)
        * [Instructions for the Envoy-based Docker container →](../admin-en/installation-guides/envoy/envoy-docker.md#run-the-container-mounting-envoyyaml)

## Step 5: Test the WAF node operation

--8<-- "../include/waf/installation/test-waf-operation-no-stats.md"

## Step 6: Delete the WAF node of the previous version

If the deployed image of the version 3.0 operates correctly, you can delete the WAF node of the previous version in the Wallarm Console → **Nodes** section.
