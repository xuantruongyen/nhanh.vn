# Get API Account

Please contact **chukhanhvan@gmail.com** to get an API account.
    (or Skype: **chukhanhvan**).

The register form will be available soon.

An API account includes:

Param | Data type (Max-length) | Description
------| -----------------------|------------
apiUsername | string(32) | API Username
secretKey | string(32) | used to [create the checksum](#create-checksum)

## Environment
- Môi trường kiểm thử (testing domain): http://dev.nhanh.vn
- Môi trường thật (production domain): https://graph.nhanh.vn
- Mỗi một API request có 1 URL, nối testing domain hoặc production domain để có 1 đường dẫn request đầy đủ. VD:
 
Môi trường kiểm thử | Môi trường thật
---- | ------------
[http://dev.nhanh.vn/api/order/add](/order/add.md)|[https://graph.nhanh.vn/api/order/add](/order/add.md)
[http://dev.nhanh.vn/api/product/add](/product/add.md)|[https://graph.nhanh.vn/api/product/add](/product/add.md)
[http://dev.nhanh.vn/api/product/detail](/product/detail.md)| [https://graph.nhanh.vn/api/product/detail](/product/detail.md)
... | ...

# Request
- RESTful applications use HTTP requests to post data. The POST params include:

Param | Data Type (Max-length) | Mandatory | Description
-------- | ----------- | -------- | ---------
version | string(10) | Yes | The current version is 1.0
storeId | string(20) | No | id gian hàng trên các sàn thương mại điện tử. Param này chỉ bắt buộc với các sàn.
apiUsername | string(32) | Yes | API Username
data | string | Yes | The JSON encoded string of an array (the structure of **data array** will be explained in each request below).
checksum | string(32) | Yes | Each request must have a checksum to validate the data. See [How to create the checksum below](#create-checksum).

## Response
- The response is a JSON encoded string, which decodes into the following structure:
```js
{
	"code": 1, // 1 = success, 0 = failed (see errors in messages)
	"messages": { // if the code = 0 the server will return error messages
		"error code": "message 1",
		"error code": "message 2"
	},
	"data": {
		// structure will be explained in detail each request below
	}
}
```

## Create checksum
- dataString  = json_encode(**data array**)

- **checksum** = md5(md5(secretKey + dataString) + dataString)
 
## Code Sample
Simple request: send product information
```php
<?php

	$apiUsername = “_YOUR_API_USERNAME_”;
	$secretKey = “_YOUR_SECRET_KEY_”;

	$dataArray = array(
		array( // product 1
		'id' => “1741235”,
   		 'parentId' => null,
   		 'code' => “SSGS2”,
   		 'barcode' => null,
   		 'name'  => “Samsung galaxy S2”,
   		 'image' => “http://example.com/images/samsung-galaxy-s-2.jpg”,
   		 'images' => array(),
   		 'shippingWeight' => “370”,
   		 'importPrice' => 12000000,
   		 'price' => 13500000,
   		 'vat' => 10, // 10%
   		 'status' => “Active”,
		)
	);

	$dataString = json_encode($dataArray);
	$checksum = md5(md5($secretKey . $dataString) . $dataString);

	$postArray = array(
		“version” => “1.0”,
		“apiUsername” => $apiUsername,
		“data” => $dataString,
		“checksum” => $checksum
	);

	$curl = curl_init(“http://dev.nhanh.vn/api/product/add”);
	curl_setopt($curl, CURLOPT_POST, 1);
	curl_setopt($curl, CURLOPT_POSTFIELDS, $postArray);
	curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);

	$curlResult = curl_exec($curl);

	if(!curl_error($curl)) {
		// success
		$response = json_decode($curlResult);
	} else {
		// failed, cannot connect nhanh.vn
		$response = new stdClass();
		$response->code = 0;
		$response->messages = array(curl_error($curl));
	}
	curl_close($curl);

	if ($response->code == 1) {
		// send product successfully
	} else {
		// failed
		if(isset($response->messages) && is_array($response->messages)) {
			// error messages
			foreach($response->messages as $message) {
				echo $message;
			}
		}
	}

```