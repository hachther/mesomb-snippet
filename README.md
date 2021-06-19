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
  'payer' => '237670000000',
  'fees' => true,
  'service' => 'MTN',
  'currency' => 'XAF',
  'message' => "Message"
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

## Deposit 

### PHP

```
<?php

$curl = curl_init();

$appKey = '57af24d87365baee326e3e7a12dce17e76f49c5c';
$appPIN = '8908';
$apiKey = '77dd38a98a39305953d74a8492e3d9d7bc8b27a8';
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
