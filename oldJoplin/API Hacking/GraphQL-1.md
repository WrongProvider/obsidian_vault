GraphQL

```graphql
query {

pastes(public: true) {

title

content

public

ipAddr

}

}
```

jeitos de fazer queries usando json

```json
{
  "query": "mutation { importPaste(host: \"google.com\", path: \"/\", port: 80, scheme: \"http\") { result } }"
}
```

usando variáveis:

```json
{
  "query": "mutation($host: String!, $path: String!, $port: Int, $scheme: String!) { importPaste(host: $host, path: $path, port: $port, scheme: $scheme) { result } }",
  "variables": {
    "host": "google.com",
    "path": "/",
    "port": 80,
    "scheme": "http"
  }
}
```