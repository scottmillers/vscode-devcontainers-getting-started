# How to configure Visual Studio Code to use Podman for DevContainers

Problem: VSCode needs to be modified to use Podman instead of Docker. 


https://github.com/microsoft/vscode-remote-release/issues/10437

Here are the settings for VSCode.  These settings are stored in 

`C:\Users\SMiller02\AppData\Roaming\Code\User>`


My settings are:
```
{
    "dev.containers.dockerPath": "podman",
    "dev.containers.dockerComposePath": "podman-compose",
    "dev.containers.defaultFeatures": {

    },
    "dev.containers.logLevel": "trace",
    "dev.containers.forwardWSLServices": false
}
```



## Problem (3/26)

This failed on Bioinfromatics-CloudMigration-AWS dev container fails if I add a feature.  The feature cannot be found

```
===========================================================================
Feature       : AWS CLI
Description   : Installs the AWS CLI along with needed dependencies. Useful for
base Dockerfiles that often are missing required install dependencies like gpg.
Id            : ghcr.io/devcontainers/features/aws-cli
Version       : 1.1.0
Documentation : https://github.com/devcontainers/features/tree/main/src/aws-cli
Options       :
    VERSION="latest"
===========================================================================
find: /var/lib/apt/lists/*: No such file or directory
Running apt-get update...
./install.sh: line 57: apt-get: command not found
ERROR: Feature "AWS CLI" (ghcr.io/devcontainers/features/aws-cli) failed to inst
all! Look at the documentation at https://github.com/devcontainers/features/tree
/main/src/aws-cli for help troubleshooting this error.
Error: building at STEP "RUN --mount=type=bind,from=dev_containers_feature_conte
nt_source,source=aws-cli_0,target=/tmp/build-features-src/aws-cli_0 cp -ar /tmp/
build-features-src/aws-cli_0 /tmp/dev-container-features  && chmod -R 0755 /tmp/
dev-container-features/aws-cli_0  && cd /tmp/dev-container-features/aws-cli_0  &
& chmod +x ./devcontainer-features-install.sh  && ./devcontainer-features-instal
l.sh  && rm -rf /tmp/dev-container-features/aws-cli_0": while running runtime: e
xit status 127

[9458 ms] Stop (2718 ms): Run: podman buildx build --load --build-context dev_containers_feature_content_source=C:\Users\SMILLE~1\AppData\Local\Temp\1\devcontainercli\container-features\0.75.0-1743131960109 --build-arg _DEV_CONTAINERS_BASE_IMAGE=mcr.microsoft.com/devcontainers/base:alpine-3.20 --build-arg _DEV_CONTAINERS_IMAGE_USER=root --build-arg _DEV_CONTAINERS_FEATURE_CONTENT_SOURCE=dev_container_feature_content_temp --target dev_containers_target_stage -f C:\Users\SMILLE~1\AppData\Local\Temp\1\devcontainercli\container-features\0.75.0-1743131960109\Dockerfile.extended -t vsc-cloud-finops-cid-d92647fb14b78158fff74115a94bf30b7d5ecbe207a64580b026717a7680cd5e-features c:\Users\SMiller02\AppData\Roaming\Code\User\globalStorage\ms-vscode-remote.remote-containers\data\empty-folder
[9460 ms] Error: Command failed: podman buildx build --load --build-context dev_containers_feature_content_source=C:\Users\SMILLE~1\AppData\Local\Temp\1\devcontainercli\container-features\0.75.0-1743131960109 --build-arg _DEV_CONTAINERS_BASE_IMAGE=mcr.microsoft.com/devcontainers/base:alpine-3.20 --build-arg _DEV_CONTAINERS_IMAGE_USER=root --build-arg _DEV_CONTAINERS_FEATURE_CONTENT_SOURCE=dev_container_feature_content_temp --target dev_containers_target_stage -f C:\Users\SMILLE~1\AppData\Local\Temp\1\devcontainercli\container-features\0.75.0-1743131960109\Dockerfile.extended -t vsc-cloud-finops-cid-d92647fb14b78158fff74115a94bf30b7d5ecbe207a64580b026717a7680cd5e-features c:\Users\SMiller02\AppData\Roaming\Code\User\globalStorage\ms-vscode-remote.remote-containers\data\empty-folder
[9460 ms]     at D6 (c:\Users\SMiller02\.vscode\extensions\ms-vscode-remote.remote-containers-0.406.0\dist\spec-node\devContainersSpecCLI.js:467:1253)
[9460 ms]     at Ix (c:\Users\SMiller02\.vscode\extensions\ms-vscode-remote.remote-containers-0.406.0\dist\spec-node\devContainersSpecCLI.js:467:997)
[9460 ms]     at async H6 (c:\Users\SMiller02\.vscode\extensions\ms-vscode-remote.remote-containers-0.406.0\dist\spec-node\devContainersSpecCLI.js:484:3842)
[9460 ms]     at async BC (c:\Users\SMiller02\.vscode\extensions\ms-vscode-remote.remote-containers-0.406.0\dist\spec-node\devContainersSpecCLI.js:484:4957)
[9460 ms]     at async d7 (c:\Users\SMiller02\.vscode\extensions\ms-vscode-remote.remote-containers-0.406.0\dist\spec-node\devContainersSpecCLI.js:665:202)
[9460 ms]     at async f7 (c:\Users\SMiller02\.vscode\extensions\ms-vscode-remote.remote-containers-0.406.0\dist\spec-node\devContainersSpecCLI.js:664:14804)
[9460 ms]     at async c:\Users\SMiller02\.vscode\extensions\ms-vscode-remote.remote-containers-0.406.0\dist\spec-node\devContainersSpecCLI.js:484:1188
[9478 ms] Stop (6395 ms): Run: C:\Users\SMiller02\AppData\Local\Programs\Microsoft VS Code\Code.exe c:\Users\SMiller02\.vscode\extensions\ms-vscode-remote.remote-containers-0.406.0\dist\spec-node\devContainersSpecCLI.js up --user-data-folder c:\Users\SMiller02\AppData\Roaming\Code\User\globalStorage\ms-vscode-remote.remote-containers\data --docker-path podman --docker-compose-path podman-compose --container-session-data-folder /tmp/devcontainers-bfca07ca-dd26-4250-ad04-799120e3277d1743131953390 --workspace-folder c:\Users\SMiller02\Development\GitHub\cloud-finops-cid --workspace-mount-consistency cached --gpu-availability detect --id-label devcontainer.local_folder=c:\Users\SMiller02\Development\GitHub\cloud-finops-cid --id-label devcontainer.config_file=c:\Users\SMiller02\Development\GitHub\cloud-finops-cid\.devcontainer\devcontainer.json --log-level trace --log-format json --config c:\Users\SMiller02\Development\GitHub\cloud-finops-cid\.devcontainer\devcontainer.json --default-user-env-probe loginInteractiveShell --experimental-lockfile --mount type=volume,source=vscode,target=/vscode,external=true --skip-post-create --update-remote-user-uid-default on --mount-workspace-git-root --include-configuration --include-merged-configuration
[9478 ms] Exit code 1
[9482 ms] Command failed: C:\Users\SMiller02\AppData\Local\Programs\Microsoft VS Code\Code.exe c:\Users\SMiller02\.vscode\extensions\ms-vscode-remote.remote-containers-0.406.0\dist\spec-node\devContainersSpecCLI.js up --user-data-folder c:\Users\SMiller02\AppData\Roaming\Code\User\globalStorage\ms-vscode-remote.remote-containers\data --docker-path podman --docker-compose-path podman-compose --container-session-data-folder /tmp/devcontainers-bfca07ca-dd26-4250-ad04-799120e3277d1743131953390 --workspace-folder c:\Users\SMiller02\Development\GitHub\cloud-finops-cid --workspace-mount-consistency cached --gpu-availability detect --id-label devcontainer.local_folder=c:\Users\SMiller02\Development\GitHub\cloud-finops-cid --id-label devcontainer.config_file=c:\Users\SMiller02\Development\GitHub\cloud-finops-cid\.devcontainer\devcontainer.json --log-level trace --log-format json --config c:\Users\SMiller02\Development\GitHub\cloud-finops-cid\.devcontainer\devcontainer.json --default-user-env-probe loginInteractiveShell --experimental-lockfile --mount type=volume,source=vscode,target=/vscode,external=true --skip-post-create --update-remote-user-uid-default on --mount-workspace-git-root --include-configuration --include-merged-configuration
[9482 ms] Exit code 1

```

This only fails when I add a feature to the devcontainer. Some guidance from this Google search

`podman vscode devcontainer with volume fails with a feature`

When using Podman with VS Code Dev Containers and encountering issues with volumes, especially when incorporating features, ensure proper user mapping with --userns=keep-id and verify the container user is correctly configured in devcontainer.json

3/31/2025

Research
Try to run podman as root

```
>podman machine init # You only need to do this once
>podman machine start
This machine is currently configured in rootless mode. If your containers
require root permissions (e.g. ports < 1024), or if you run into compatibility
issues with non-podman clients, you can switch using the following command:

        podman machine set --rootful
>podman machine stop
>podman machine set --rootful  # make it run as root
>podman machine start 
Starting machine "podman-machine-default"
API forwarding listening on: npipe:////./pipe/docker_engine

Docker API clients default to this address. You do not need to set DOCKER_HOST.
Machine "podman-machine-default" started successfully
```
