# A Private Blockchain: Star Registry

Create a private blockchain to rRegister ownership of stars.
this app was created for the Udacity Blockchain Developer Nanodegree.

## Technologies

    * Node.JS: as a JavaScript Web Server
    * Express: the Web Framework
    * morgan - to log HTTP requests
    * ES6 classes
    * body-parser: to extract data from HTTP requests
    * bitcoinjs-lib & bitcoinjs-message: to verify Messages
    * crypto-js: to hash arbitrary strings into fixed-256-bit-long SHA256 strings
    * hex2ascii: to hex-encode & decode

## Instructions

To get the blockchain up and running, and interact with it:

Install the dependencies:

```
npm install
```

Run the app:

```
node app.js
```

To use the endpoints, open Postman and go to:

```
http://localhost:8000/
```

## I. [GET /block/0] to request the Genesis Block

Take a look at the Genesis Block created by the application upon initialization.

![Request: http://localhost:8000/block/height/0 ](/images/GenesisBlock.png)

## II. [Get /validateChain] to validate the blockchain

This endpoint verifies that all the blocks in the blockchain are valid through validating the hashes.

![Request: http://localhost:8000/requestValidation ](/images/ValidateTheChain.png)

## III. [POST /requestValidation] to request a message for the address signing

To prove that you are the owner of your wallet address, send this request to receive a message to be used with your wallet to get a signature.

![Request: http://localhost:8000/requestValidation ](/images/GetMessageSignature.png)

## IV. Sign the Message from your Bitcoin wallet

Sign the Message with your Electrum or Bitcoin Core wallet.

![Request: http://localhost:8000/requestValidation ](/images/BitcoinCoreSignedmessage.png)

## V. [POST /submitstar] to register your star

Register your star by submitting a `POST` request to `/submitstar`. Requires these parameters: `wallet address`, `message`, `signature`, and the `star` object in a JSON object in the request body. Here is the format to register a star:

```json
"star": {
    "dec": "68° 52' 56.9",
    "ra": "16h 29m 1.0s",
    "story": "Testing the story 1"
}
```

![Request: http://localhost:8000/submitstar](/images/SubmitStar1.png)

## VI. [GET /blocks/<YOUR_WALLET_ADDRESS>] to retrieve stars for an address

Retrieve a list of all the stars that have been stored in the blockchain that are associated with a certain `address`.

![Request: http://localhost:8000/blocks/<WALLET_ADDRESS>](/images/GetStarsPerAddress.png)
