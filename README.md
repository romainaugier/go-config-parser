# ini_config_parser
Simple and easy to use .ini config parser written in Go

![BuildTest](https://github.com/romainaugier/go-config-parser/actions/workflows/build_and_test.yml/badge.svg)

`go install github.com/romainaugier/go-config-parser@latest`

API:
```go
package main

import (
    "fmt"
    cp "github.com/romainaugier/go-config-parser"
)

func main() {
    config_path := "/path/to/config.ini"

    // Parses the configuration
    config := cp.ConfigParse(config_path)

    // Config will be nil if there was an error during parsing
    if config == nil {
        fmt.Printf("Error during ini config parsing, check the log for more information")
        return
    }

    // Gets a key value as string. By default, all values are stored as strings. If the key is not present,
    // returns an empty one
    string_key := cp.ConfigGet(config, "Global", "STRING_KEY")

    // Gets a key value as int. If there was an error during the conversion string->int, returns the
    // default value
    int_key := cp.ConfigGetInt(config, "Global", "INT_KEY", 0)

    // Gets a key value as bool. If there was an error during the conversion string->bool, returns the
    // default value
    bool_key := cp.ConfigGetBool(config, "Global", "BOOL_KEY", false)
}
```
