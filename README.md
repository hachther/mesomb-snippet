# Some code snippet to perform operation

## Payment 

### PHP

```
<?php

$curl = curl_init();

$url = 'https://mesomb.hachther.com/api/v1.0/payment/online/';
$appKey = 'APP_KEY';
$data = array(
  'amount' => 100,
  'payer' => '670000000',
  'fees' => true,
  'service' => 'MTN',
  'currency' => 'XAF',
  'message' => "Message",
  'country' => 'CM'
);

curl_setopt_array($curl, [
  CURLOPT_URL => $url,
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => json_encode($data),
  CURLOPT_HTTPHEADER => [
    "Accept: application/json",
    "Content-Type: application/json",
    "User-Agent: Mozilla",
    "X-MeSomb-Application: ${appKey}"
  ],
]);

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
?>
```

### Ruby

```
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://mesomb.hachther.com/api/v1.0/payment/online/")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request["X-MeSomb-Application"] = 'APP_KEY'
request["X-MeSomb-OperationMode"] = 'synchronous'
request.body = "{\n\t\"amount\": 10,\n\t\"payer\": \"670000000\",\n\t\"fees\": true,\n\t\"service\": \"MTN\",\n\t\"currency\": \"XAF\",\n\t\"country\": \"CM\",\n\t\"fees\": true\n}"

response = http.request(request)
puts response.read_body
```

## Deposit 

### PHP

```
<?php

$curl = curl_init();

$appKey = 'APP_KEY';
$appPIN = 'USER_PIN';
$apiKey = 'API_KEY';
$url = "https://mesomb.hachther.com/en/api/v1.0/applications/$appKey/deposit/";
$data = array(
  'amount' => 20,
  'receiver' => '237690000000',
  'service' => 'ORANGE',
  'pin' => $appPIN
);

curl_setopt_array($curl, [
  CURLOPT_URL => $url,
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => json_encode($data),
  CURLOPT_HTTPHEADER => [
    "Accept: application/json",
    "Content-Type: application/json",
    "User-Agent: Mozilla",
    "Authorization: Token $apiKey"
  ],
]);

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
?>
```

### Ruby

```
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://mesomb.hachther.com/en/api/v1.0/applications/APP_KEY/deposit/")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token [API_KEY]'
request.body = "{\n\t\"amount\": 20,\n\t\"receiver\": \"670000000\",\n\t\"service\": \"ORANGE\",\n\t\"pin\": \"[PIN_CODE]\",\n\t\"country\": \"CM\",\n}"

response = http.request(request)
puts response.read_body
```
