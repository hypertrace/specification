# Agent data capture

Hypertrace agents MUST capture the following data:

## Request and response headers

## Request and response HTTP bodies

The bodies are captured for the following content types:

* `application/json`
* `application/graphql`
* `application/x-www-form-urlencoded`
* `multipart/form-data`

## RPC metadata

## gRPC request and response bodies

The body objects MUST be serialized into JSON.
