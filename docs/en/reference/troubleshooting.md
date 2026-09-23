# Troubleshooting and FAQ

This page covers runtime problems after installation. For a first run in binary, local, or Docker mode, see the [deployment guide](../getting-started/deployment.md).

## A model request fails

Check **System configuration** for the provider base URL, API key, and selected task model. A local service access token signs in to ScienceDiscovery; it is not a model API key. See [Runtime behavior](runtime-behavior.md#models).

## A permission card stops work

Review the requested action before approving it. Persistent grants are managed under **System configuration → Permissions**. Enabling a connector does not authorize its execution. See [permissions and reviewer](runtime-behavior.md#permissions-and-reviewer).

## A connector or proxy cannot connect

Check the server or provider settings first. For MCP authentication and connection diagnostics, use [Configure custom MCP servers](../how-to/configure-custom-mcp.md). For model, web, and MCP proxy traffic, use [Configure the network proxy](../how-to/configure-network-proxy.md).

## A run times out or needs to stop

Use **Stop run** to cancel a current run. Configure product wall-clock limits under **System configuration → Timeouts**. See [timeouts and run status](runtime-behavior.md#timeouts-and-run-status).

## Where does my data live?

Projects, Sessions, workspaces, credentials, and service environments live under the data directory. Its default is `.sciencediscovery-data` in local mode and `./data` for Docker. A local ScienceMemory backend stores its graph separately under `~/.science-agent/memory-graph`. See [Storage layout](configuration.md#storage-layout). Deleting a Project or Session is permanent; back up every data location you need first.
