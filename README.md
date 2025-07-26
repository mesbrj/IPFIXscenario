# IPFIXscenario

## Project Overview

## Components

[**Apache APISIX API Gateway**](https://apisix.apache.org/):

![IPFIXscenario](/documentation/images/apisix.png)

**IPyFIXweb**: https://github.com/mesbrj/IPyFIXweb (WIP)
  - Python FastAPI REST (HATEOAS-driven) API (OpenAPI compliant)
  - Core [IPFIX Services](https://tools.netsa.cert.org/pyfixbuf/doc/index.html): Collector, Mediation, Exporter and Analyzer
  - Integration with [IPjFIXsvc](https://github.com/mesbrj/IPjFIXsvc) for sending (transformed / converted) flow records (IPFIX mediation)
  - [PCAP converter/exporter IPFIX and DPI analysis](https://tools.netsa.cert.org/yaf/yaf.html)
  - [RRDTool](https://oss.oetiker.ch/rrdtool/) or [Graphite](https://graphiteapp.org/) for Time series analysis for flow records
  - [Lua integration](https://github.com/scoder/lupa) via [LuaJIT](https://luajit.org/) for custom (on the fly) processing and analysis
  - AI agent for: IPFIX collector and (mediator) exporter / IPFIX mediator pipelines / tasks and analysis

**IPjFIXsvc**: https://github.com/mesbrj/IPjFIXsvc (WIP)
  - Java Spring Boot - [Olingo ODATA (Open Data Protocol V4)](https://olingo.apache.org/doc/odata4/index.html) REST API support
  - High-performance flow record ingestion and parsing / Real-time and batch processing capabilities
  - Integration with [IPyFIXweb](https://github.com/mesbrj/IPyFIXweb) for data retrieval
  - [Ignite](https://ignite.apache.org/) integration for distributed data
  - [Lucene Core](https://lucene.apache.org/core/) or [Apache Solr](https://solr.apache.org/) for flow records search and indexing
  - AI agent for (intelligent data analysis and insights ...)

**IPjFIXqry**: Java Spring Boot - GraphQL API + Read-only ODATA proxy
  - GraphQL API for flexible data querying
  - Read-only ODATA proxy for data access and querying
  - Integration with [IPjFIXsvc](https://github.com/mesbrj/IPjFIXsvc) for data retrieval
  - Distributed Cache with [Hazelcast](https://hazelcast.com/) for performance optimization on ODATA models
  - AI agent for (query optimization and data analytics and insights ...)

**IPFIXcommand**: Golang based Terminal UI for system control and monitoring
  - Command-line interface for system administration
  - Real-time monitoring and configuration management
  - Performance metrics and system health monitoring
  - AI agent (for command execution and analysis, automation and optimization ...)

**IPFIXanalysis**: Kotlin based analysis engine (JavaScript, WebAssembly)
  - Cross-platform user interface for data visualization
  - Interactive dashboards for flow record analysis
  - Customizable data views and reports
  - AI agent (for predictive analytics and anomaly detection ...)
