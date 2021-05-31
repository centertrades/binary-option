## BO will send request to clients including: balance, bet, win

## API Environments

| Name      | API Endpoint | 
| ----------- | ----------- |
| production      | https://api-bo.centertrades.com|
| staging      | https://api-staging-bo.centertrades.com|

## Web URL Environments

| Name      | Web url | 
| ----------- | ----------- |
| production      | https://bo.centertrades.com|
| staging      | https://staging-bo.centertrades.com|

## 1. Create merchant
Each site has one merchant only.
Please use merchantId, privateKey, publicKey for the following actions.

## 2. Generate token
For BO running, each user must have a token generated from bo center.
To generate, please make the request:

Enpoint: **<API>/game/token**

Method: **POST**

Content-type: **application/x-www-form-urlencoded**

**Request header**:

-hmac

**Request body**:
- key: '<PUBLIC_KEY>'
- merchantId: '<MERCHANT_ID>'
- identifier: '<USER_IDENTITY>' 

--> hmac is created using the privateKey of merchant

 The request will return a token. This token will expire after a day.

## 3. Access BO Web
  After token is created. You can access the BO Web interface at url:
  <WEB_URL>/auth?token=<TOKEN>&merchantId=<MERCHANT_ID>&identifier=<USER_IDENTITY>
 When token is expired, you must re-generated a new one.
    
The following request is callback request which means bo center will send request to merchant site for balance, bet, win:

 
Method: **POST**

Content-type: **application/x-www-form-urlencoded**
    
## 4. Balance request
**Request body**: 
    
- type: 'BALANCE'
- identifier: '<USER_IDENTITY>'

**Response header**:
    
- hmac
    
**Response body**:
- balance: <BALANCE_OF_USER>
- identifier: '<USER_IDENTITY>'

## 5. Bet request
**Request body**:
- type: 'BET'
- id: '<ID_OF_BET_REQUEST>'
- identifier: '<USER_IDENTITY>'
- amount: <BET_AMOUNT>


**Response header**:
- hmac
**Response body**:
- balance: <BALANCE_OF_USER_AFTER_BET>
- identifer: '<USER_IDENTITY>'

## 6. Win request
**Request body**:
- type: 'WIN'
- id: '<ID_OF_BET_REQUEST>'
- identifier: '<USER_IDENTITY>'
- amount: <BET_AMOUNT>

**Response header**:
- hmac
**Response body**:
- balance: <BALANCE_OF_USER_AFTER_WIN>
- identifier: '<USER_IDENTITY>'
