![Manage your Kobble project and users from your server with Kobble Admin SDK](https://firebasestorage.googleapis.com/v0/b/kobble-prod.appspot.com/o/docs%2Fbanners%2Fgo-admin-sdk-banner.png?alt=media&token=cbdac131-5718-456e-b9b4-92e95760b688)

[![License](https://img.shields.io/:license-mit-blue.svg?style=flat)](https://opensource.org/licenses/MIT)
![Status](https://img.shields.io/:status-stable-green.svg?style=flat)
![Go](https://img.shields.io/badge/go-compatible-green.svg)
![Supabase](https://img.shields.io/:supabase_edge_functions-compatible-green.svg?style=flat)

## Project Status

This project is not currently in **stable** status. We are actively working on fixing bugs and adding new features.
Fill free to open an issue / open PR if you have any questions or need help.

## Getting started

### Installation
    
```bash
go get github.com/kobble-io/go-admin/kobble
```

Initialize a `Kobble` instance from a secret generated from your [Kobble dashboard](https://app.kobble.io/p/project/admin-sdk).

```go
import (
    "fmt"
    "log"
    "github.com/kobble-io/go-admin/kobble"
)

func main() {
    k := kobble.New("YOUR_SECRET", kobble.Options{})
    whoami, err := k.Whoami()
    if err != nil {
        log.Fatal(err)
    }

    // To verify your setup
    fmt.Println(whoami)
}
```

## Verify User Tokens

### Verify ID Token

You can verify **ID tokens** obtained using Kobble frontend SDKs as follows:

```go
func main() {
    k := kobble.New("YOUR_SECRET", kobble.Options{})
    result, err := k.Auth.VerifyIdToken("ID_TOKEN")
    if err != nil {
        log.Fatal(err)
    }

    fmt.Println(result)
    // Output:
    // {
    //     userId: 'clu9ob5480001mdhwk9qt00hv',
    //     user: {
    //         id: 'clu9ob5480001mdhwk9qt00hv',
    //         email: 'kevinpiac@gmail.com',
    //         name: null,
    //         pictureUrl: null,
    //         isVerified: true,
    //         stripeId: null,
    //         updatedAt: 2024-03-27T10:39:02.000Z,
    //         createdAt: 2024-03-27T10:39:02.000Z
    //     },
    //     claims: { ... }
    // }
}
```

### Verify Access Token

You can verify **Access tokens** obtained using Kobble frontend SDKs as follows:

```go
func main() {
	k := kobble.New("YOUR_SECRET", kobble.Options{})
	result, err := k.Auth.VerifyAccessToken("ACCESS_TOKEN")
	if err != nil {
		log.Fatal(err)
	}

	fmt.Println(result)
	// Output:
	// {
	//     projectId: 'cltxiphfv000129anb0kuagow',
	//     userId: 'clu9ob5480001mdhwk9qt00hv',
	//     claims: {
	//         sub: 'clu9ob5480001mdhwk9qt00hv',
	//         project_id: 'cltxiphfv000129anb0kuagow',
	//         iat: 1713183109,
	//         exp: 1713186709689,
	//         iss: 'https://kobble.io',
	//         aud: 'clu9ntcvr0000o9yfz87ybo4a'
	//     }
	// }
}
```

## Documentation 

Exported functions are extensively documented, and more documentation can be found on our [official documentation](https://docs.kobble.io).

## What is Kobble

<p align="center">
  <picture>
    <img alt="Kobble Logo" src="https://firebasestorage.googleapis.com/v0/b/kobble-prod.appspot.com/o/docs%2Fbanners%2Flogo.png?alt=media&token=35c9e52e-6a90-4192-aa98-fe99c76be15a" width="150">
  </picture>
</p>
<p align="center">
 Kobble is the one-stop solution for monetizing modern SaaS and APIs. It allows to add authentication, analytics and payment to any app in under 10 minutes.
</p>
