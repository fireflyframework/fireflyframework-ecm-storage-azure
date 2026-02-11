# Firefly Framework - ECM Storage - Azure Blob

[![CI](https://github.com/fireflyframework/fireflyframework-ecm-storage-azure/actions/workflows/ci.yml/badge.svg)](https://github.com/fireflyframework/fireflyframework-ecm-storage-azure/actions/workflows/ci.yml)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Java](https://img.shields.io/badge/Java-21%2B-orange.svg)](https://openjdk.org)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-green.svg)](https://spring.io/projects/spring-boot)

> Azure Blob Storage adapter for Firefly ECM document content management.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Configuration](#configuration)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [License](#license)

## Overview

This module implements the Firefly ECM `DocumentContentPort` using Azure Blob Storage as the storage backend. It provides `AzureBlobDocumentContentAdapter` for storing, retrieving, and managing document content in Azure Blob containers.

The adapter auto-configures via `AzureBlobAutoConfiguration` and is activated by including this module on the classpath alongside the ECM core module.

## Features

- Azure Blob Storage integration for document content storage and retrieval
- Spring Boot auto-configuration for seamless activation
- Implements Firefly ECM DocumentContentPort
- Configurable via application properties
- Standalone provider library (include alongside fireflyframework-ecm)

## Requirements

- Java 21+
- Spring Boot 3.x
- Maven 3.9+
- Azure Blob Storage account and API credentials

## Installation

```xml
<dependency>
    <groupId>org.fireflyframework</groupId>
    <artifactId>fireflyframework-ecm-storage-azure</artifactId>
    <version>26.01.01</version>
</dependency>
```

## Quick Start

The adapter is automatically activated when included on the classpath with the ECM core module:

```xml
<dependencies>
    <dependency>
        <groupId>org.fireflyframework</groupId>
        <artifactId>fireflyframework-ecm</artifactId>
    </dependency>
    <dependency>
        <groupId>org.fireflyframework</groupId>
        <artifactId>fireflyframework-ecm-storage-azure</artifactId>
    </dependency>
</dependencies>
```

## Configuration

```yaml
firefly:
  ecm:
    storage:
      azure-blob:
        connection-string: DefaultEndpointsProtocol=https;AccountName=...
        container-name: documents
```

## Documentation

No additional documentation available for this project.

## Contributing

Contributions are welcome. Please read the [CONTRIBUTING.md](CONTRIBUTING.md) guide for details on our code of conduct, development process, and how to submit pull requests.

## License

Copyright 2024-2026 Firefly Software Solutions Inc.

Licensed under the Apache License, Version 2.0. See [LICENSE](LICENSE) for details.
