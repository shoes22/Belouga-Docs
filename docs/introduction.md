# Belouga API Documentation 

In this documentation you will find out how to generate valid requests to the Belouga API server for retrieving and submitting information.

> All Belouga API endpoints require PASETOv2 token authorization. We use PASETO instead of standard JWT because sensitive user data is being transmitted, so all information must be encrypted using the most bulletproof security standards. This means you need a PASETO token library to generate valid tokens. 

You can find a PASETO library for your platform [HERE](https://paseto.io/).

## Pages
- ** [Token Requirements](./requirements.md) ** Documentation on how to generate signed PASETO tokens that are valid for Belouga. 
- ** [Registration Request Lifecycle](./requirements.md) ** The request flow of API calls when registering a user.
