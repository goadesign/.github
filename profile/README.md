<p align="center">
  <img alt="Goa Design Banner" src="/profile/assets/goadesign-banner.png">
</p>

<h1 align="center">Design-first Go infrastructure for APIs, services, agents, and distributed systems</h1>

<p align="center">
  Define contracts once. Generate the transports, clients, docs, schemas, tools,
  and runtime glue that keep production code honest.
</p>

<p align="center">
  <a href="https://github.com/goadesign/goa"><img alt="Goa stars" src="https://img.shields.io/github/stars/goadesign/goa?style=for-the-badge&logo=github"></a>
  <a href="https://github.com/goadesign/goa-ai"><img alt="Goa-AI" src="https://img.shields.io/badge/Goa--AI-agentic%20systems-006BFF?style=for-the-badge"></a>
  <a href="https://github.com/goadesign/goa/releases/latest"><img alt="Goa release" src="https://img.shields.io/github/v/release/goadesign/goa?style=for-the-badge"></a>
  <a href="https://go.dev"><img alt="Go 1.25+" src="https://img.shields.io/badge/Go-1.25%2B-00ADD8?logo=go&logoColor=white&style=for-the-badge"></a>
  <a href="https://github.com/goadesign/goa/blob/main/LICENSE"><img alt="MIT license" src="https://img.shields.io/badge/license-MIT-brightgreen.svg?style=for-the-badge"></a>
  <a href="https://gophers.slack.com/messages/goa"><img alt="Goa Slack" src="https://img.shields.io/badge/Goa-Slack-4A154B?logo=slack&logoColor=white&style=for-the-badge"></a>
</p>

<p align="center">
  <a href="https://goa.design">Documentation</a>
  ·
  <a href="https://github.com/goadesign/goa">Goa</a>
  ·
  <a href="https://github.com/goadesign/goa-ai">Goa-AI</a>
  ·
  <a href="https://github.com/goadesign/examples">Examples</a>
  ·
  <a href="https://github.com/goadesign/goa/discussions">Discussions</a>
  ·
  <a href="https://goadesign.substack.com">Design First</a>
</p>

---

## Start Here

<table>
  <tr>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/goadesign/goa">Goa</a></h3>
      <p>
        Design-first APIs and microservices in Go. Write one DSL contract and
        generate type-safe HTTP, gRPC, JSON-RPC, clients, OpenAPI docs, CLIs,
        and transport scaffolding with zero drift between design and code.
      </p>
      <p>
        <a href="https://goa.design/docs/">Read the docs</a>
        ·
        <a href="https://github.com/goadesign/examples">Browse examples</a>
        ·
        <a href="https://pkg.go.dev/goa.design/goa/v3/dsl">Go package docs</a>
      </p>
    </td>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/goadesign/goa-ai">Goa-AI</a></h3>
      <p>
        Design-first agentic systems in Go. Declare agents, tools, MCP servers,
        policies, structured model outputs, streaming events, and durable
        execution; generate the plumbing and run it locally or with Temporal.
      </p>
      <p>
        <a href="https://goa.design/docs/2-goa-ai/">Read the Goa-AI docs</a>
        ·
        <a href="https://github.com/goadesign/goa-ai/tree/main/quickstart">Quickstart</a>
        ·
        <a href="https://pkg.go.dev/goa.design/goa-ai">Go package docs</a>
      </p>
    </td>
  </tr>
</table>

## Start With Goa In 60 Seconds

Install the generator, describe a service, and let Goa create the boring parts.

```bash
go install goa.design/goa/v3/cmd/goa@latest

mkdir hello && cd hello
go mod init example.com/hello
mkdir design
```

```go
package design

import . "goa.design/goa/v3/dsl"

var _ = Service("hello", func() {
	Method("say_hello", func() {
		Payload(func() {
			Field(1, "name", String)
			Required("name")
		})
		Result(String)

		HTTP(func() {
			GET("/hello/{name}")
		})
	})
})
```

```bash
goa gen example.com/hello/design
goa example example.com/hello/design
go run ./cmd/hello
```

From that one design, Goa generates server interfaces, transport adapters,
clients, OpenAPI documentation, and command-line helpers. Your code stays
focused on business behavior.

## Build Agents With Goa-AI

Goa-AI applies the same design-first contract model to agent systems:

- **Typed tool contracts**: Goa types, validations, examples, generated JSON Schema, and generated codecs.
- **MCP integration**: generated MCP servers and callers for exposing Goa services and consuming external tools.
- **Structured completions**: service-owned result schemas with unary and streaming helpers.
- **Runtime policy**: budgets, tool caps, confirmation gates, cancellation, retries, and bounded tool results.
- **Durable execution**: an in-memory development engine and a Temporal-backed production engine.
- **Real-time products**: typed stream events for assistant text, tool progress, awaits, child runs, usage, and status.

Start with the [Goa-AI quickstart](https://github.com/goadesign/goa-ai/tree/main/quickstart),
then go deeper in the [Goa-AI docs](https://goa.design/docs/2-goa-ai/) and
[repository guides](https://github.com/goadesign/goa-ai/tree/main/docs).

## Why Design First

- **No drift**: the design owns the contract; generated code, docs, schemas, and clients stay aligned.
- **Less boilerplate**: Goa generates the repetitive 30-50% of an API or agent system so teams build the behavior that matters.
- **One contract, many surfaces**: HTTP, gRPC, JSON-RPC, OpenAPI, clients, CLIs, tools, MCP adapters, and agent runtimes come from the same source.
- **Production boundaries**: business logic stays separate from transports, model providers, workflow engines, storage, and observability.

## The Goa Design Ecosystem

| Project | What it is for |
| --- | --- |
| [goa](https://github.com/goadesign/goa) | The core design-first framework and code generator for Go APIs and services. |
| [goa-ai](https://github.com/goadesign/goa-ai) | Agents, tools, MCP, structured completions, policies, streaming events, and durable runtimes. |
| [examples](https://github.com/goadesign/examples) | Copy-pasteable services that show specific Goa capabilities in real projects. |
| [plugins](https://github.com/goadesign/plugins) | Official plugins that extend Goa generation. |
| [clue](https://github.com/goadesign/clue) | OpenTelemetry-based observability for logs, metrics, traces, and health. |
| [pulse](https://github.com/goadesign/pulse) | Event streaming, replicated maps, Redis-backed semaphores, and distributed worker pools. |
| [model](https://github.com/goadesign/model) | C4 software architecture diagrams as Go code. |

## Community

We are building Goa with people who care about typed contracts, generated
infrastructure, clean service boundaries, and production-grade Go systems.

- Join the [Goa Slack channel](https://gophers.slack.com/messages/goa).
- Follow project updates on [Design First](https://goadesign.substack.com).
- Ask questions and shape the roadmap in
  [GitHub Discussions](https://github.com/goadesign/goa/discussions).
- Read the published documentation at [goa.design](https://goa.design).

## Sponsors

<table width="100%">
  <tr>
    <td>
      <a href="https://www.incident.io">
        <img src="https://raw.githubusercontent.com/goadesign/goa/v3/docs/incidentio.png" alt="incident.io" width="240" align="right">
      </a>
      <h3>incident.io: Bounce back stronger after every incident</h3>
      <p>
        Use incident.io to run incidents end-to-end, rapidly fix issues, and
        learn from them so your team can build more resilient products.
      </p>
      <a href="https://incident.io">Learn more</a>
    </td>
  </tr>
  <tr>
    <td>
      <a href="https://www.speakeasy.com/editor?utm_source=goa+org&utm_medium=github+sponsorship">
        <img src="https://raw.githubusercontent.com/goadesign/goa/v3/docs/speakeasy.png" alt="Speakeasy" width="240" align="right">
      </a>
      <h3>Speakeasy: Enterprise DevEx for your API</h3>
      <p>
        Speakeasy helps teams create feature-rich, production-ready SDKs and
        improve API developer experience.
      </p>
      <a href="https://www.speakeasy.com/docs/api-frameworks/goa?utm_source=goa+org&utm_medium=github+sponsorship">Integrate with Goa</a>
    </td>
  </tr>
</table>

## Contributing

Goa Design is open source and community-built. The most helpful contributions
come with a small design, a failing test, a clear reproduction, or a focused
documentation improvement.

Start with the [contributing guide](https://github.com/goadesign/goa/blob/main/CONTRIBUTING.md)
and [code of conduct](https://github.com/goadesign/goa/blob/main/CODE_OF_CONDUCT.md),
or browse [good first issues](https://github.com/search?q=org%3Agoadesign+label%3A%22good+first+issue%22+state%3Aopen&type=issues).

<p align="center">
  <a href="https://github.com/goadesign/goa/graphs/contributors">
    <img alt="Goa contributors" src="https://contrib.rocks/image?repo=goadesign/goa">
  </a>
</p>
