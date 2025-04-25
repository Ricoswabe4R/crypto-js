# CryptoJS

JavaScript library of cryptographic standards.

[![npm version](https://badge.fury.io/js/crypto-js.svg)](https://www.npmjs.com/package/crypto-js)

---

## 🚨 Discontinued

The active development of CryptoJS has been **discontinued**. This library is no longer maintained.

Modern JavaScript environments, like **Node.js** and modern browsers, come with a native `Crypto` module that offers robust cryptographic capabilities. The latest version of CryptoJS already uses the native `Crypto` module for random number generation, as `Math.random()` is not cryptographically secure. 

Continuing the development of CryptoJS would result in it being just a wrapper around the native `Crypto` module. Therefore, we encourage you to migrate to the native `Crypto` module.

---

## 📦 Installation

### Node.js

**Requirements**:
- Node.js
- npm (Node.js package manager)

Install CryptoJS via npm:
```bash
npm install crypto-js
```

### Browser

**Requirements**:
- Node.js
- Bower (frontend package manager)

Install CryptoJS via Bower:
```bash
bower install crypto-js
```

---

## 🛠️ Usage

### Node.js Example

#### ES6 Import (for API Signing):
```javascript
import sha256 from 'crypto-js/sha256';
import hmacSHA512 from 'crypto-js/hmac-sha512';
import Base64 from 'crypto-js/enc-base64';

const message, nonce, path, privateKey; // ...
const hashDigest = sha256(nonce + message);
const hmacDigest = Base64.stringify(hmacSHA512(path + hashDigest, privateKey));
```

#### CommonJS Modular Include:
```javascript
const AES = require("crypto-js/aes");
const SHA256 = require("crypto-js/sha256");

console.log(SHA256("Message"));
```

#### Include All Libraries:
```javascript
const CryptoJS = require("crypto-js");

console.log(CryptoJS.HmacSHA1("Message", "Key"));
```

---

### Browser Example

#### Modular Include (with RequireJS):
```javascript
require.config({
    packages: [
        {
            name: 'crypto-js',
            location: 'path-to/bower_components/crypto-js',
            main: 'index'
        }
    ]
});

require(["crypto-js/aes", "crypto-js/sha256"], function (AES, SHA256) {
    console.log(SHA256("Message"));
});
```

#### Include All Libraries:
```javascript
require.config({
    paths: {
        'crypto-js': 'path-to/bower_components/crypto-js/crypto-js'
    }
});

require(["crypto-js"], function (CryptoJS) {
    console.log(CryptoJS.HmacSHA1("Message", "Key"));
});
```

#### Without RequireJS:
```html
<script type="text/javascript" src="path-to/bower_components/crypto-js/crypto-js.js"></script>
<script type="text/javascript">
    const encrypted = CryptoJS.AES.encrypt(...);
    const hashed = CryptoJS.SHA256(...);
</script>
```

---

## 🔒 API Overview

### AES Encryption

#### Encrypting Plain Text:
```javascript
const CryptoJS = require("crypto-js");

// Encrypt
const ciphertext = CryptoJS.AES.encrypt('my message', 'secret key 123').toString();

// Decrypt
const bytes = CryptoJS.AES.decrypt(ciphertext, 'secret key 123');
const originalText = bytes.toString(CryptoJS.enc.Utf8);

console.log(originalText); // 'my message'
```

#### Encrypting Objects:
```javascript
const CryptoJS = require("crypto-js");

const data = [{id: 1}, {id: 2}];

// Encrypt
const ciphertext = CryptoJS.AES.encrypt(JSON.stringify(data), 'secret key 123').toString();

// Decrypt
const bytes = CryptoJS.AES.decrypt(ciphertext, 'secret key 123');
const decryptedData = JSON.parse(bytes.toString(CryptoJS.enc.Utf8));

console.log(decryptedData); // [{id: 1}, {id: 2}]
```

---

### Modules

Below is a list of the available CryptoJS modules:

#### Hashing Algorithms:
- `crypto-js/md5`
- `crypto-js/sha1`
- `crypto-js/sha256`
- `crypto-js/sha224`
- `crypto-js/sha512`
- `crypto-js/sha384`
- `crypto-js/sha3`
- `crypto-js/ripemd160`

#### HMAC Algorithms:
- `crypto-js/hmac-md5`
- `crypto-js/hmac-sha1`
- `crypto-js/hmac-sha256`
- `crypto-js/hmac-sha224`
- `crypto-js/hmac-sha512`
- `crypto-js/hmac-sha384`
- `crypto-js/hmac-sha3`
- `crypto-js/hmac-ripemd160`

#### Symmetric Encryption:
- `crypto-js/aes`
- `crypto-js/tripledes`
- `crypto-js/rc4`
- `crypto-js/rabbit`
- `crypto-js/rabbit-legacy`

#### Encoding:
- `crypto-js/enc-latin1`
- `crypto-js/enc-utf8`
- `crypto-js/enc-hex`
- `crypto-js/enc-utf16`
- `crypto-js/enc-base64`

#### Padding Modes:
- `crypto-js/pad-pkcs7`
- `crypto-js/pad-ansix923`
- `crypto-js/pad-iso10126`
- `crypto-js/pad-iso97971`
- `crypto-js/pad-zeropadding`
- `crypto-js/pad-nopadding`

---

## 📝 Release Notes

### 4.2.0
- Updated default hash algorithm and iterations for PBKDF2 to improve security.
- Added support for custom KDF hasher.
- Introduced Blowfish support.

### 4.1.1
- Fixed module order in bundled release.
- Included the browser field in `package.json`.

### 4.1.0
- Added URL-safe variant of Base64 encoding.
- Avoided adding the `crypto-browser` package in Webpack builds.

### 4.0.0
- Replaced `Math.random()` with the native `Crypto` module for randomness.
- Breaking changes for environments lacking a native `Crypto` module (e.g., IE10, React Native).

### 3.x.x
- Legacy versions with `Math.random()` for randomness (not cryptographically secure). Avoid using these versions.

---

## 📚 Documentation

For detailed API usage and examples, visit the [CryptoJS Documentation](https://cryptojs.gitbook.io/docs/).

---

This rewrite organizes the content clearly, uses headings and icons for better readability, and improves the tone to ensure clarity and professionalism. Let me know if you need further adjustments!
