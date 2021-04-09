# Trace state

The Hypertrace agents encode vendor specific information in [tracestate header](https://www.w3.org/TR/trace-context/#tracestate-header).

## Format

The tracestate format is `vendorname1=opaqueValue1,vendorname2=opaqueValue2`. The value
is up to 256 characters long and contains ASCII from `0x20` to `0x7E` excluding `,` and `=`. For more
detailed information see the [specification](https://www.w3.org/TR/trace-context/#value).

The Hypertrace vendor name is `hypertrace`.

### Value

The Hypertrace tracestate vendor value can encode multiple values. The values are separated by `|`. 

An example:
* `tracestate: somevendor=opaqueValue1,hypertrace=key1:val1|key2:val2`

#### Capture

The capture feature allows coherently capturing data within a trace. For instance a sampler
can make use of this capability to capture only some percentage of request and response payloads.

The agent MUST set the capture value if the value was not previously present.

Value key: `cap`

Possible values:
* `0` - do not capture payloads and headers except whitelisted ones
* `1` - capture all request/response headers and payloads

An example:
* `tracestate: hypertrace=cap:0`

##### Whitelisted headers

The whitelisted headers are:
* `Content-Type`
* `User-Agent`
