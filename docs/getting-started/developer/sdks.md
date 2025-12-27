---
title: SDKs
description: Client libraries for integrating with the Lethean blockchain API in 30+ languages.
---

# SDK Documentation

Lethean provides auto-generated SDKs for 30+ programming languages, making it easy to integrate blockchain functionality into your applications.

## Quick Start Examples

All SDKs connect to the daemon's REST API (default: `http://127.0.0.1:48782`).

### Go

```go
package main

import (
    "context"
    "fmt"
    "log"

    lthn "github.com/LetheanNetwork/blockchain/utils/sdk/client/go"
)

func main() {
    // Create client configuration
    config := lthn.NewConfiguration()
    config.Servers = lthn.ServerConfigurations{
        {URL: "http://127.0.0.1:48782"},
    }
    client := lthn.NewAPIClient(config)

    // Get blockchain info
    info, _, err := client.InfoUtilsSdkClientGo.GetInfo(context.Background()).Execute()
    if err != nil {
        log.Fatalf("Error: %v", err)
    }

    fmt.Printf("Height: %d\n", info.GetHeight())
    fmt.Printf("Difficulty: %d\n", info.GetDifficulty())
    fmt.Printf("Network Hashrate: %d\n", info.GetCurrentNetworkHashrate50())
}
```

### Python

```python
import openapi_client
from openapi_client.api import info_api, block_api

# Configure the client
configuration = openapi_client.Configuration(
    host="http://127.0.0.1:48782"
)

with openapi_client.ApiClient(configuration) as api_client:
    # Get blockchain info
    info_api_instance = info_api.InfoApi(api_client)
    info = info_api_instance.get_info()

    print(f"Height: {info.height}")
    print(f"Difficulty: {info.difficulty}")

    # Get a specific block
    block_api_instance = block_api.BlockApi(api_client)
    block = block_api_instance.get_block("1000")  # Block at height 1000

    print(f"Block hash: {block.id}")
    print(f"Transactions: {len(block.transaction_details)}")
```

### TypeScript/Node.js

```typescript
import { Configuration, InfoApi, BlockApi } from '@lethean/sdk';

const config = new Configuration({
    basePath: 'http://127.0.0.1:48782'
});

async function main() {
    const infoApi = new InfoApi(config);
    const blockApi = new BlockApi(config);

    // Get blockchain info
    const info = await infoApi.getInfo();
    console.log(`Height: ${info.height}`);
    console.log(`Synchronized: ${info.synchronized}`);

    // Get current height
    const height = await blockApi.getHeight();
    console.log(`Current height: ${height.height}`);

    // Get latest block
    const block = await blockApi.getBlock({ identifier: height.height.toString() });
    console.log(`Latest block hash: ${block.id}`);
}

main().catch(console.error);
```

### PHP

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

use OpenAPI\Client\Api\InfoApi;
use OpenAPI\Client\Api\BlockApi;
use OpenAPI\Client\Configuration;

$config = Configuration::getDefaultConfiguration()
    ->setHost('http://127.0.0.1:48782');

// Get blockchain info
$infoApi = new InfoApi(null, $config);
$info = $infoApi->getInfo();

echo "Height: " . $info->getHeight() . "\n";
echo "Difficulty: " . $info->getDifficulty() . "\n";

// Get a block by hash or height
$blockApi = new BlockApi(null, $config);
$block = $blockApi->getBlock('1000');

echo "Block hash: " . $block->getId() . "\n";
foreach ($block->getTransactionDetails() as $tx) {
    echo "  TX: " . $tx->getPubKey() . "\n";
}
```

### Rust

```rust
use lethean_sdk::{apis::configuration::Configuration, apis::info_api, apis::block_api};

#[tokio::main]
async fn main() -> Result<(), Box<dyn std::error::Error>> {
    let config = Configuration {
        base_path: "http://127.0.0.1:48782".to_string(),
        ..Default::default()
    };

    // Get blockchain info
    let info = info_api::get_info(&config, None).await?;
    println!("Height: {}", info.height.unwrap_or(0));

    // Get current height
    let height = block_api::get_height(&config).await?;
    println!("Current height: {}", height.height.unwrap_or(0));

    Ok(())
}
```

---

## API Endpoints

All SDKs provide access to these endpoints:

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/info` | GET | Blockchain and daemon status |
| `/info/version` | GET | API version |
| `/block/height` | GET | Current blockchain height |
| `/block/{identifier}` | GET | Get block by hash or height |
| `/block` | GET | Get multiple blocks (paginated) |
| `/block/template` | POST | Create mining block template |
| `/block/submit` | POST | Submit mined block |

For detailed API documentation, see the [Go SDK Reference](../../sdk/go/index.md).

---

## Generating SDKs

SDKs are generated from the OpenAPI specification using [openapi-generator](https://openapi-generator.tech/).

### Generate a Specific SDK

```shell
# From the blockchain repository
make sdk go          # Generate Go SDK
make sdk python      # Generate Python SDK
make sdk typescript  # Generate TypeScript SDK
make sdk rust        # Generate Rust SDK
```

### Generate All SDKs

```shell
make sdk
```

### Available Generators

| Language | Generator Name |
|----------|---------------|
| Go | `go` |
| Python | `python` |
| TypeScript | `typescript`, `typescript-node`, `typescript-angular` |
| Rust | `rust` |
| PHP | `php` |
| Java | `java` |
| Ruby | `ruby` |
| Swift | `swift5`, `swift6` |
| Dart | `dart` |
| C++ | `cpp-oatpp-client` |
| Bash | `bash` |
| PowerShell | `powershell` |
| Lua | `lua` |
| Nim | `nim` |
| R | `r` |
| Haskell | `haskell-http-client` |
| GDScript | `gdscript` |
| GraphQL | `graphql-schema` |
| Protobuf | `protobuf-schema` |

---

## Error Handling

All SDKs follow similar error handling patterns:

```go
// Go example
info, response, err := client.InfoUtilsSdkClientGo.GetInfo(ctx).Execute()
if err != nil {
    // Check for specific error types
    if apiErr, ok := err.(*lthn.GenericOpenAPIError); ok {
        fmt.Printf("API Error: %s\n", apiErr.Body())
    }
    return err
}
```

```python
# Python example
from openapi_client.exceptions import ApiException

try:
    info = info_api.get_info()
except ApiException as e:
    print(f"API Error {e.status}: {e.body}")
```

---

## Connection Options

### Local Node

```
http://127.0.0.1:48782
```

### Remote Node

```
http://seed.lethean.io:48782
```

!!! warning "Remote Node Privacy"
    When connecting to a remote node, your queries are visible to that node. For maximum privacy, run your own node.

---

## Further Reading

- [Go SDK Reference](../../sdk/go/index.md) - Complete API documentation
- [Build Guide](build.md) - Compile the blockchain and SDKs
- [Network Architecture](../../network/architecture.md) - Understand the API context
