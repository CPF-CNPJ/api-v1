# Example

PHP sample code for API v1 queries

www.cpfcnpj.com.br/dev

## Install PHP cURL extension

In order to install this library via composer run the following command in the console:

```bash
composer require curl/curl
```
or add the package manually to your composer.json file in the require section:

```bash
"curl/curl": "^2.0"
```

## Creating a Request

```php
include 'vendor/autoload.php';

$curl = new Curl\Curl();

$params = array(
    "token" => "5ae973d7a997af13f0aaf2bf60e65803",
    "pacote" => 9,
    "cpfcnpj" => '45317828791'
);
$curl->get('https://api.cpfcnpj.com.br/'.$params["token"].'/'.$params["pacote"].'/'.$params["cpfcnpj"]);
$curl->close();

$response = json_decode($curl->response, 1);

print_r($response);
```
