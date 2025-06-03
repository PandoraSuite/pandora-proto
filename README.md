# Pandora Proto

Pandora Proto is the centralized repository containing all `.proto` definitions for the **Pandora Suite** ecosystem. It is designed to promote consistency, modularity, and ease of integration across all Pandora-related services and client libraries.

This repository is intended **exclusively for developers**, and is meant to be included as a Git submodule within other projects that require gRPC communication with Pandora Core (`pandora-core`) or other Pandora services.

## Overview

All `.proto` files follow a clean modular structure and are maintained using **[Buf](https://buf.build/)** for linting, breaking change detection, and code generation.

### Protocol Buffer Files

#### `api_key.proto`

Defines the RPCs and message types related to validating and consuming API Keys, including:

* `ValidateOnly` and `ValidateAndConsume` services used by external systems to verify key validity
* Structured request/response messages including environment metadata, path, method, and IP address
* Scoped validation support for fine-grained access control

#### `request.proto`

Defines the RPCs and message types related to updating the status of requests, including:

* `SetRequestStatus` service used to update the status of a Request
* Structured request/response messages for status updates

## Usage with Buf

This repo uses Buf for linting and generation. To generate code from the `.proto` files locally, run:

```bash
buf generate
```

Ensure you have `buf` installed and configured properly. See the [Buf CLI installation guide](https://docs.buf.build/installation) for help.

## How to Use in Your Project

To include this repo as a submodule:

```bash
git submodule add https://github.com/PandoraSuite/pandora-proto proto/pandora
```

Then configure your `buf.gen.yaml` to point to the appropriate path within your project (e.g. `proto/pandora/api_key`, `proto/pandora/request`, etc.).

## Related Projects

To view the full implementation of the gRPC server that uses these `.proto` files, refer to the `pandora-core` repository. The server is already implemented and ready:

:point_right: [https://github.com/PandoraSuite/pandora-core](https://github.com/PandoraSuite/pandora-core)

You’ll also find documentation on how to configure and consume the services defined here.

## License

This project is licensed under the terms of the MIT license.
