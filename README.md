# Firefly ECM Storage – Azure Blob

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Java](https://img.shields.io/badge/Java-21+-orange.svg)](https://openjdk.java.net/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen.svg)](https://spring.io/projects/spring-boot)

Microsoft Azure Blob Storage adapter for Firefly lib‑ecm. Reactive streaming uploads/downloads, block uploads, and resilience baked‑in.

## Features
- Reactive streaming with backpressure
- Single/block blob uploads with thresholds
- Metadata (content‑type) handling
- Resilience4j circuit‑breaker and retry hooks
- Auto‑config guarded by `firefly.ecm.adapter-type=azure-blob`

## Installation
```xml
<dependency>
  <groupId>org.fireflyframework</groupId>
  <artifactId>fireflyframework-ecm-storage-azure</artifactId>
  <version>${firefly.version}</version>
</dependency>
```

## Configuration
```yaml
firefly:
  ecm:
    enabled: true
    adapter-type: azure-blob
    adapter:
      azure-blob:
        account-name: ${AZURE_ACCOUNT_NAME}
        container-name: ${AZURE_CONTAINER_NAME}
        # one of the following
        account-key: ${AZURE_ACCOUNT_KEY:}
        connection-string: ${AZURE_CONNECTION_STRING:}
        sas-token: ${AZURE_SAS_TOKEN:}
        endpoint: ${AZURE_BLOB_ENDPOINT:}
        path-prefix: ${AZURE_PATH_PREFIX:documents/}
        block-upload-threshold: ${AZURE_BLOCK_UPLOAD_THRESHOLD:268435456}
```

## Usage
```java
@Autowired DocumentContentPort contentPort;
Flux<DataBuffer> body = ...;
Mono<String> key = contentPort.storeContentStream(id, body, "application/pdf", null);
```

## Resilience
Inject your own `CircuitBreaker`/`Retry` beans (qualifiers `azureBlobCircuitBreaker`, `azureBlobRetry`) or use defaults.

## Testing
- Unit tests mock BlobContainerClient/BlobClient and verify `upload`/`downloadStream`
- Boot smoke test validates the adapter bean

## License
Apache 2.0
