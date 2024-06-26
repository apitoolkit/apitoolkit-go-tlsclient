<div align="center">

![APItoolkit's Logo](https://github.com/apitoolkit/.github/blob/main/images/logo-white.svg?raw=true#gh-dark-mode-only)
![APItoolkit's Logo](https://github.com/apitoolkit/.github/blob/main/images/logo-black.svg?raw=true#gh-light-mode-only)

## Golang tls-client SDK

[![APItoolkit SDK](https://img.shields.io/badge/APItoolkit-SDK-0068ff?logo=go)](https://github.com/topics/apitoolkit-sdk) [![Join Discord Server](https://img.shields.io/badge/Chat-Discord-7289da)](https://discord.gg/dEB6EjQnKB) [![APItoolkit Docs](https://img.shields.io/badge/Read-Docs-0068ff)](https://apitoolkit.io/docs/sdks/golang?utm_source=github-sdks) [![GoDoc](https://godoc.org/github.com/apitoolkit/apitoolkit-go?status.svg)](https://godoc.org/github.com/apitoolkit/apitoolkit-go)

APItoolkit is an end-to-end API and web services management toolkit for engineers and customer support teams. To integrate your Golang application with APItoolkit, you need to use this SDK to monitor incoming traffic, aggregate the requests, and then deliver them to the APItoolkit's servers.

</div>

---

## Table of Contents

- [Installation](#installation)
- [Configuration](#configuration)
- [Contributing and Help](#contributing-and-help)
- [License](#license)

---

## Installation

Kindly run the command below to install the SDK:

```sh
go get github.com/apitoolkit/apitoolkit-go-tlsclient
```

Then add `github.com/apitoolkit/apitoolkit-go` to the list of dependencies like so:

```go
package main

import (
  apitoolkit "github.com/apitoolkit/apitoolkit-go"
)
```

## Configuration

Next, initialize APItoolkit in your application's entry point (e.g., `main.go`) like so:

```go
package main

import (
  "context"
  "log"
  "net/http"
  apitoolkit "github.com/apitoolkit/apitoolkit-go"
)

func main() {
  ctx := context.Background()

  // Initialize the client
  apitoolkitClient, err := apitoolkit.NewClient(ctx, apitoolkit.Config{APIKey: "{ENTER_YOUR_API_KEY_HERE}"})
  if err != nil {
    panic(err)
  }

  // Register APItoolkit's middleware
  http.Handle("/", apitoolkitClient.Middleware(http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
    w.WriteHeader(http.StatusOK)
    w.Write([]byte("Hello, World!"))
  })))

  http.ListenAndServe(":8080", nil)
}
```

> [!NOTE]
> 
> - This SDK supports multiple Golang frameworks (including, [Chi](https://apitoolkit.io/docs/sdks/golang/chi?utm_source=github-sdks), [Echo](https://apitoolkit.io/docs/sdks/golang/echo?utm_source=github-sdks), [Fiber](https://apitoolkit.io/docs/sdks/golang/fiber?utm_source=github-sdks), [Gin](https://apitoolkit.io/docs/sdks/golang/gin?utm_source=github-sdks), [Gorilla Mux](https://apitoolkit.io/docs/sdks/golang/gorillamux?utm_source=github-sdks), and [Native](https://apitoolkit.io/docs/sdks/golang/native?utm_source=github-sdks)). You can learn how to configure each framework using the provided Middleware (e.g.,  `EchoMiddleware`) in the respective linked docs above.
> - The `{ENTER_YOUR_API_KEY_HERE}` demo string should be replaced with the [API key](https://apitoolkit.io/docs/dashboard/settings-pages/api-keys?utm_source=github-sdks) generated from the APItoolkit dashboard.

<br />

> [!IMPORTANT]
> 
> To learn more configuration options (redacting fields, error reporting, outgoing requests, etc.), please read this [SDK documentation](https://apitoolkit.io/docs/sdks/golang?utm_source=github-sdks).

## Contributing and Help

To contribute to the development of this SDK or request help from the community and our team, kindly do any of the following:
- Read our [Contributors Guide](https://github.com/apitoolkit/.github/blob/main/CONTRIBUTING.md).
- Join our community [Discord Server](https://discord.gg/dEB6EjQnKB).
- Create a [new issue](https://github.com/apitoolkit/apitoolkit-go/issues/new/choose) in this repository.

## License

This repository is published under the [MIT](LICENSE) license.

---

<div align="center">
    
<a href="https://apitoolkit.io?utm_source=github-sdks" target="_blank" rel="noopener noreferrer"><img src="https://github.com/apitoolkit/.github/blob/main/images/icon.png?raw=true" width="40" /></a>

</div>
