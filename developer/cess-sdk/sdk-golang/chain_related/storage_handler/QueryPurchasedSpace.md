This is the interface to query the size of purchased space.

```golang
// QueryPurchasedSpace query all purchased space size
//   - block: block number, less than 0 indicates the latest block
//
// Return:
//   - uint64: all purchased space size
//   - error: error message
func (c *ChainClient) QueryPurchasedSpace(block int32) (uint64, error)
```

Example code:
```golang
package main

import (
    "context"
    "fmt"
    "time"

    sdkgo "github.com/CESSProject/cess-go-sdk"
    "github.com/CESSProject/cess-go-sdk/utils"
)

var RPC_ADDRS = []string{
    //testnet
    "wss://testnet-rpc.cess.network/ws/",
}

func main() {
    sdk, err := sdkgo.New(
        context.Background(),
        sdkgo.ConnectRpcAddrs(RPC_ADDRS),
    )
    if err != nil {
        panic(err)
    }
    defer sdk.Close()

    fmt.Println(sdk.QueryPurchasedSpace(-1))
}
```