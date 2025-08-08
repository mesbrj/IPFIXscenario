# IPFIXscenario

## Project Overview

### Deployments

- Helm charts for Kubernetes
- Development: docker compose / podman-kube

## Components

![IPFIXscenario](/documentation/images/apisix.png)

*[**Ory**](https://www.ory.sh/open-source) IAM&CIAM with Identies management (as reference stack and used in development and tests).*
- [hydra](https://www.ory.sh/hydra/) for OAuth2 and OIDC, [kratos](https://www.ory.sh/kratos/) for user management and [keto](https://www.ory.sh/keto/) for access control.

### Kubernetes Operator

IPFIXscenario Kubernetes Operator for managing the lifecycle of below IPFIXscenario components in a Kubernetes environment using the [**Java operator SDK**](https://github.com/java-operator-sdk/java-operator-sdk):

[**Apache APISIX** API Gateway](https://apisix.apache.org/):
- APISIX as a centralized API Gateway for security, routing, and traffic management.
- OAuth Integration - Native OAuth 2.0/OIDC token validation.
- JWT Verification - Automatic token signature and claims validation
- Rate Limiting - Per-client and global rate limiting policies
- Load Balancing - Multiple algorithms with health checks
- TLS Termination - Centralized certificate management
- Request/Response Transformation - Header manipulation and data transformation

**IPyFIXweb**: https://github.com/mesbrj/IPyFIXweb (WIP)
  - Python FastAPI REST (HATEOAS-driven) API (OpenAPI compliant)
  - Core [IPFIX Services](https://tools.netsa.cert.org/pyfixbuf/doc/index.html): Collector, Mediation, Exporter and Analyzer
  - [keepalived](https://www.keepalived.org/) (VRRP, [LVS/IPVS](http://www.linux-vs.org/)) for high availability and load balancing of IPFIX collectors (TCP)
  - Integration with [IPjFIXsvc](https://github.com/mesbrj/IPjFIXsvc) for sending (transformed / converted) flow records (IPFIX mediation)
  - [PCAP converter/exporter IPFIX and DPI analysis](https://tools.netsa.cert.org/yaf/yaf.html)
  - [MinIO](https://min.io/) object storage for flow records
  - [RRDTool](https://oss.oetiker.ch/rrdtool/) or [Graphite](https://graphiteapp.org/) for Time series analysis for flow records
  - [Lua integration](https://github.com/scoder/lupa) via [LuaJIT](https://luajit.org/) for custom (on the fly) processing and analysis
  - AI agent for: IPFIX collector and (mediator) exporter / IPFIX mediator pipelines / tasks and analysis

**keep-a-remote**: https://github.com/mesbrj/keep-a-remote (WIP)
  - Keepalived Go web REST API for managing keepalived instrumentation and telemetry
  - Get, set and reload, securely and in monitored way, all keepalived configuration (keepalived.conf)
  - Monitor status, metrics and health of keepalived daemon and related resources
  - Deploy methods for Kubernetes (identifying the appropriate approaches and pre-requisites, for keepalived LB/HA features)
  - Integration with [IPyFIXweb](https://github.com/mesbrj/IPyFIXweb) for IPFIX collector (TCP) service LB and HA

**IPjFIXsvc**: https://github.com/mesbrj/IPjFIXsvc (WIP)
  - Java Spring Boot - [Olingo ODATA (Open Data Protocol V4)](https://olingo.apache.org/doc/odata4/index.html) REST API support
  - High-performance flow record ingestion and parsing / Real-time and batch processing capabilities
  - Integration with [IPyFIXweb](https://github.com/mesbrj/IPyFIXweb) for data retrieval
  - [Ignite](https://ignite.apache.org/) integration for distributed data
  - [Lucene Core](https://lucene.apache.org/core/) or [Apache Solr](https://solr.apache.org/) for flow records search and indexing
  - AI agent for (intelligent data analysis and insights ...)

**IPjFIXqry**: Java Spring Boot - (GraphQL API / ODATA proxy)
  - GraphQL API for flexible data querying
  - Read-only ODATA proxy for data access and querying \ GraphQL query only, implementation
  - Distributed Cache with [Hazelcast](https://hazelcast.com/) ([Community Edition](https://hazelcast.com/community-edition-projects/downloads/))
  - Integration with [IPjFIXsvc](https://github.com/mesbrj/IPjFIXsvc) for data retrieval
  - AI agent for (query optimization and data analytics and insights ...)

**IPFIXcommand**: https://github.com/mesbrj/IPFIXcommand (WIP)
  - Golang based Terminal UI for system control and monitoring
  - Command-line interface for system administration
  - Real-time monitoring and configuration management
  - Performance metrics and system health monitoring
  - AI agent (for command execution and analysis, automation and optimization ...)

**IPFIXanalysis**: Kotlin based analysis engine (JavaScript, WebAssembly)
  - Cross-platform user interface for data visualization
  - Interactive dashboards for flow record analysis
  - Customizable data views and reports
  - AI agent (for predictive analytics and anomaly detection ...)
