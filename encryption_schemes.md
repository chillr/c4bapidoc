# Encryption Scheme

The payload string of the transaction status is encrypted and needs to be decrypted at the client side.

The encryption algorithm used is **[AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)**.

The cipher mode is _AES-128-ECB_

The merchant API secret key is to be used to decrypt the message.

#### Decryption Code Samples
##### 1. Ruby 

```ruby
def decryption(msg)
	KEY = ‘00e9d200dfdc119a0e78f0dcef1da4f8’
    # this is the same as the merchant secret key
    
	algorithm = ‘AES-128-ECB’
    
    cipher = OpenSSL::Cipher.new(algorithm)
    cipher.decrypt()
    cipher.key = KEY
    
    tempkey = Base64.decode64(msg)
    crypt = cipher.update(tempkey)
    
    crypt << cipher.final()
    
    return crypt
end
```
##### 2. PHP

```php
$method = 'AES-128-ECB';
$key = "00e9d200dfdc119a0e78f0dcef1da4f8";
// this is the same as the merchant secret key

$response = openssl_decrypt( $data, $method, $key );
```
##### 2. Node
```javascript
function decryptPayload(payload) {
   var iv = new Buffer(16); // 16 byte buffer with default iv for AES-128-CBC in Ruby
   iv.fill(0);
   var decodeKey = new Buffer(16)  // Converting merchant_api_key to 16 byte long. 
   decodeKey.fill(merchant_api_key)
   var result,
     encoded   = new Buffer(payload, 'base64'),
     decipher  = crypto.createDecipheriv('aes-128-cbc', decodeKey, iv);
   result = decipher.update(encoded);
   result += decipher.final();
   return result;
 }
```