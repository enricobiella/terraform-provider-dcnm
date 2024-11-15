# Cisco DCNM Provider 1

Requirements
------------

- [Terraform](https://www.terraform.io/downloads.html) v0.12 or later.

- [Go](https://golang.org/doc/install) Latest Version

## Building The Provider ##
Clone this repository to: `$GOPATH/src/github.com/ciscoecosystem/terraform-provider-dcnm`.
Clone dcnm-go-client to `$GOPATH/src/github.com/ciscoecosystem/dcnm-go-client`.

```sh
$ mkdir -p $GOPATH/src/github.com/ciscoecosystem; cd $GOPATH/src/github.com/ciscoecosystem
$ git clone https://github.com/ciscoecosystem/terraform-provider-dcnm.git
$ git clone https://github.com/ciscoecosystem/dcnm-go-client.git
```


Using The Provider
------------------
If you are building the provider, follow the instructions to [install it as a plugin.](https://www.terraform.io/docs/plugins/basics.html#installing-a-plugin) After placing it into your plugins directory, run `terraform init` to initialize it.

ex.
```hcl
#configure provider with your Cisco DCNM/NDFC credentials.
terraform {
  required_providers {
    dcnm = {
      source = "CiscoDevNet/dcnm"
    }
  }
}

provider "dcnm" {
  # Cisco DCNM/NDFC user name
  username = "admin"
  # Cisco DCNM/NDFC password
  password = "password"
  # Cisco DCNM/NDFC url
  url      = "https://my-cisco-dcnm.com"
  insecure = true
  proxy_url = "https://proxy_server:proxy_port"
  platform = "dcnm"
}

resource "dcnm_inventory" "first" {
  fabric_name   = "fab1"
  username      = "Username for NXOS switch"
  password      = "Password for NXOS switch"
  ip            = "IP of NXOS switch"
}
```


Developing The Provider
-----------------------
If you want to work on the provider, you'll first need [Go](http://www.golang.org) installed on your machine. You'll also need to correctly setup a [GOPATH](http://golang.org/doc/code.html#GOPATH), as well as adding `$GOPATH/bin` to your `$PATH`.

To compile the provider, run `make build`. This will build the provider with sanity checks present in scripts directory and put the provider binary in `$GOPATH/bin` directory.

