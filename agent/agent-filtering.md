# Filter interface

The filtering capability allows running arbitrary filter at the entry point the application.
The instrumentation points use the result of the evaluation to block the execution.

## Filter interface

The filter interface defines following API for request evaluation. Each of these methods
can be called multiple times. If the request headers and body are available at the same time
the instrumentation MUST use the API with both entities.

### Evaluate request headers

```java
boolean evaluateRequestHeaders(Span span, Map<String, String> headers)
```

### Evaluate request body 

```java
boolean evaluateRequestBody(Span span, String body)
```

### Evaluate request headers and body

```java
boolean evaluateRequestHaeadersAndBody(Span span, Map<String, String> headers, String body)
```

## Filter registry

Multiple implementations of a filter can be installed to the registry. The registration is language
specific. For instance in Java it can be done via [Java Service Loader](https://docs.oracle.com/javase/7/docs/api/java/util/ServiceLoader.html)
and in Golang via programmatic API.

### `Filter getFilter()`

Returns a filter interface. If multiple filters are installed in the registry a single multiplexing filter
is returned. The multiplexing filter runs all filters and it returns `true` if any of the filters returns `true`.
