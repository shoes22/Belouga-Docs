---
title: Token Requirements
---

# Token Requirements

Once you have a PASETO library installed, you can generate a token. We use Version 2 protocol, 'local' purpose tokens. This means all requests must be encrypted by a shared secret key that we provide for you. All tokens, regardless of endpoint, must have the following fields:

```json json_schema
{
  "title": "User",
  "description": "The claims section of the token.",
  "type": "object",
  "properties": {
    "aud": {
      "type": "string",
      "description": "The type of token this is. Valid values are 'testing' or 'production'."
    },
    "iss": {
      "type": "string",
      "description": "The issuer of the token. Must match the issuer id we provide you."
    },
    "jti": {
      "type": "string",
      "description": "The consumer of the token. Should always be   'belouga_api' unless otherwise specified."
    },
    "exp": {
      "type": "datetime",
      "description": "The expiry date of the token. Default value should be 24 hours ahead of the current time."
    },
    "user": {
      "type": "object",
      "description": "If submitting a registration, include the user object as part of the token here."
    }
  },
  "required": [
    "aud",
    "iss",
    "jti",
    "exp"
  ]
}
```

Once the token claims are generated, encrypt the token with the Belouga-provided secret key, and include the token in an HTTP Authorization header field with the 'Bearer' type, when sending the request. An example header is shown below:

## HTTP Header Example

<!-- title: My Table Title -->

| Key   |      Value      |
| ------------- | :-----------: |
| Authorization | Bearer v2.local.YbQp7XOUmhtw0lrWjmL4OOJpij_BSCkd9cDEf2dxlYBiA8n2jC_N_0V9znk2eh6DkwYB107Ov1c3JWEuFOapua7hySFsrpHjr_qwpOIkS9oZyxzzmJFfhs9A7cZYB-XAkhd_GMFPYRZY_Y5AMbC7_-VIhnzhrQcgkFxFNoWh4A | 