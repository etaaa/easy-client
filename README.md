# easyclient

An easy to use Golang wrapper for the net/http package to perform requests.

## Features

* Auto body closing
* Auto body parsing
* Easily set and clear cookies for client
* Easily set cookies for a single request
* Ordered headers
* Easily set and clear headers for client
* Easily set headers for a single request
* Easily set and clear proxy for client
* Easily set proxy for a single request

## Usage

Install:
```bash
go get github.com/etaaa/easyclient
```

Usage:
```go
package main

import (
	"log"
	"github.com/etaaa/easyclient"
)

func main() {
	// Create a new client.
	client, _ := easyclient.NewClient(easyclient.ClientOptions{
		// Options specified here will persist for every request made with this client.
		Headers: map[string]string{
			"api-key": "123",
		},
	})
	// Execute a request with the created client.
	res, body, _ := client.Do(easyclient.RequestOptions{
		// Options specified here will only be applied for the current request.
		Cookies: map[string]string{
			"foo": "bar",
		},
		Headers: map[string]string{
			"user-agent": "easyclient",
		},
		Method:           "GET",
		ReadResponseBody: true,
		URL:              "https://httpbin.org/headers",
	})
	fmt.Print(res.StatusCode, string(body))
}
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change. Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
