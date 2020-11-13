# Agent data capture

Hypertrace agents MUST be capable of capturing the following data entities.
The data capture is configurable via [agent config](https://github.com/hypertrace/agent-config).

## HTTP request and response headers

The header names and values are added to the span attributes in the original format.

Attribute keys:

* request `http.request.header.<header-name>`
* response `http.response.header.<header-name>`

## HTTP request and response bodies

The bodies are captured for the following content types:

* `application/json`
* `application/graphql`
* `application/x-www-form-urlencoded`

Attribute keys:

* request `http.request.body`
* response `http.response.body`

## RPC metadata

The metadata names and values are added to the span attributes in the original format.

Attribute keys:

* request `rpc.request.metadata.<metadata-name>`
* response `rpc.response.metadata.<metadata-name>`

## RPC request and response bodies

* request `rpc.request.body`
* response `rpc.response.body`

### Notes

The gRPC body objects MUST be serialized into JSON.
