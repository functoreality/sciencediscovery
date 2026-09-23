# Security and trust

ScienceDiscovery is a locally run, single-user workspace. It is not a multi-user production service.

## Default exposure and access

In binary and local mode, the adapter and API bind to loopback by default. Docker listens on `0.0.0.0:4310` inside its container, while Compose publishes that port to host loopback by default. Access uses one bearer token and there is no TLS termination. Exposing an interface to another network is an explicit deployment choice for a trusted, secured network. Keep the `Open to sign in` URL and local service access token private.

## Execution boundary

Python, R, and shell commands run in a fail-closed platform sandbox: Bubblewrap on Linux and Seatbelt in macOS local source mode. The sandbox isolates the visible filesystem to the Session workspace and uses a configured network policy. It does not make every product component sandboxed. The control API, adapter, JiuwenSwarm, PDF worker, and outbound model or provider calls are trusted control-plane operations outside that sandbox.

For the implementation and operational limits, see [Sandbox execution](../developer-docs/sandbox-execution.md).
