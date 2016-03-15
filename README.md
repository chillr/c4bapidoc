# Chillr for Business API Documentation

## Introduction
The Chillr for Business platform provides a simple secure REST based API in order to accept payments easily via Chillr. This document is a comprehensive reference for all endpoints available in the Chillr for Business API.

## Implementation

The API implementation has two parts:
1. The client side implementation
2. The server side implementation

The server sends a request to the Chillr API with details of the transaction to be performed. This includes the amount, product details and API credentials.

The server will get a _qr\_code_ and an _alpha\_code_ in the response. The client side Javascript Chillr SDK is to be initialized with these parameters. The display of the QR code and the alpha code is taken care by the widget. It also updates progress of the transaction automatically and shows the user with instructions as and when necessary. 

Once the user completes the transaction, status is updated on the Javascript widget. After a few seconds the widget will send a HTTP POST request to the redirect URL provided by the merchant. This request will have a JSON payload with the status and the details of the transaction in encrypted format. These details can be decrypted using the API secret key.

If there is a network failure or timeout; the merchant has an option to check the status of the transaction directly from the server. 

Details on the encryption scheme used is available here.


