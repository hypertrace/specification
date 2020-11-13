# Agent data capture

Hypertrace agents MUST capture the following data:

## HTTP Request and response headers

The header names and values are added to the span attributes in the original format.

Attribute keys:

* request `http.request.header.<header-name>`
* response `http.response.header.<header-name>`

## HTTP Request and response bodies

The bodies are captured for the following content types:

* `application/json`
* `application/graphql`
* `application/x-www-form-urlencoded`
* `multipart/form-data`

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
