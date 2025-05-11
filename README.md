# API v1 Query Examples

Based on the PHP example, here are code samples in several popular programming languages for querying the API available at [en.cpfcnpj.com.br/dev](https://en.cpfcnpj.com.br/dev).

## Prerequisites

Make sure you have the necessary HTTP client libraries installed:

- **PHP**: cURL extension  
- **Python**: requests  
- **Node.js**: axios (or native fetch in Node.js 18+)  
- **Java**: HttpClient (Java 11+)  
- **C#**: System.Net.Http  
- **Ruby**: httparty  
- **Go**: net/http  
- **Bash**: curl  

## Install Instructions

### PHP

```bash
composer require curl/curl
```

### Python

```bash
pip install requests
```

### Node.js

```bash
npm install axios
```

### Ruby

```bash
gem install httparty
```

## Request Examples

### PHP

```php
<?php
require 'vendor/autoload.php';

$curl = new Curl\Curl();

$params = [
    'token'    => '5ae973d7a997af13f0aaf2bf60e65803',
    'pacote'   => 9,
    'cpfcnpj'  => '45317828791',
];

$curl->get("https://api.cpfcnpj.com.br/{$params['token']}/{$params['pacote']}/{$params['cpfcnpj']}");
$curl->close();

$response = json_decode($curl->response, true);

print_r($response);
```

### Bash (cURL)

```bash
curl -X GET "https://api.cpfcnpj.com.br/5ae973d7a997af13f0aaf2bf60e65803/9/45317828791"
```

### Python

```python
import requests

token = "5ae973d7a997af13f0aaf2bf60e65803"
package = 9
cpfcnpj = "45317828791"
url = f"https://api.cpfcnpj.com.br/{token}/{package}/{cpfcnpj}"

response = requests.get(url)
data = response.json()
print(data)
```

### JavaScript (Node.js with axios)

```javascript
const axios = require('axios');

const token = '5ae973d7a997af13f0aaf2bf60e65803';
const pacote = 9;
const cpfcnpj = '45317828791';
const url = `https://api.cpfcnpj.com.br/${token}/${pacote}/${cpfcnpj}`;

axios.get(url)
  .then(response => {
    console.log(response.data);
  })
  .catch(error => {
    console.error(error);
  });
```

### Java (HttpClient)

```java
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;

public class ApiExample {
    public static void main(String[] args) throws Exception {
        String token = "5ae973d7a997af13f0aaf2bf60e65803";
        int pacote = 9;
        String cpfcnpj = "45317828791";
        String url = String.format("https://api.cpfcnpj.com.br/%s/%d/%s", token, pacote, cpfcnpj);

        HttpClient client = HttpClient.newHttpClient();
        HttpRequest request = HttpRequest.newBuilder()
            .uri(URI.create(url))
            .GET()
            .build();

        HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());
        System.out.println(response.body());
    }
}
```

### C# (.NET Core)

```csharp
using System;
using System.Net.Http;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        var token = "5ae973d7a997af13f0aaf2bf60e65803";
        var pacote = 9;
        var cpfcnpj = "45317828791";
        var url = $"https://api.cpfcnpj.com.br/{token}/{pacote}/{cpfcnpj}";

        using var client = new HttpClient();
        var response = await client.GetStringAsync(url);
        Console.WriteLine(response);
    }
}
```

### Ruby

```ruby
require 'httparty'

token = '5ae973d7a997af13f0aaf2bf60e65803'
pacote = 9
cpfcnpj = '45317828791'
url = "https://api.cpfcnpj.com.br/#{token}/#{pacote}/#{cpfcnpj}"

response = HTTParty.get(url)
puts response.parsed_response
```

### Go

```go
package main

import (
    "fmt"
    "io/ioutil"
    "net/http"
)

func main() {
    token := "5ae973d7a997af13f0aaf2bf60e65803"
    pacote := "9"
    cpfcnpj := "45317828791"
    url := fmt.Sprintf("https://api.cpfcnpj.com.br/%s/%s/%s", token, pacote, cpfcnpj)

    resp, err := http.Get(url)
    if err != nil {
        panic(err)
    }
    defer resp.Body.Close()

    body, err := ioutil.ReadAll(resp.Body)
    if err != nil {
        panic(err)
    }
    fmt.Println(string(body))
}
```
