---
title: "Installers"
keywords: workspace, runtime, recipe, docker, stack, installers, agents
tags: [workspace, runtime, docker, kubernetes]
sidebar: user_sidebar
permalink: installers.html
folder: workspaces
---

{% include links.html %}

## What Are Installers?

Installers are scripts that are injected into machines in a runtime and get executed there to:

1. Prepare environment and download dependencies for particular software or tool
2. Install chosen software and dependencies
3. Launch software and tools in a certain way (arguments, mode etc) that provide extra functionality for a workspace

Installers are typically language servers and tools that provide features like ssh access to a workspace machine etc. You can find a complete list of available installers in workspace details, Installers tab.

```
"installers": [
    "org.eclipse.che.exec",
    "org.eclipse.che.terminal",
    "org.eclipse.che.ws-agent",
    "org.eclipse.che.ssh"
        ]
```

## How Installers Work?

Installers scripts are saved into a configuration file that a [bootstrapper](what_are_workspaces.html#bootstrapper) uses to execute its jobs. An installer script is a bash script that works exactly the same way it'd work in your local Linux environment. Che server then checks if the process that an installer has launched is alive.

There are installers that activate special agents like workspace agent, terminal and exec agent. For example, if a workspace agent fails to start, the workspace will be considered as started but the IDE won't be usable. Exec agent failure will result in unavailability of commands widget.

## Enable and Disable Installers

Installers are can be enabled/disabled in User Dashboard per machine, or directly in workspace machine configuration. When an installer is enabled, bootstrapper executes an installer script after the workspace has started.

{% include image.html file="workspaces/installers.png" %}
