## BO will send request to clients including: balance, bet, win

Method: **POST**

Content-type: **application/x-www-form-urlencoded**

**Request headers**: 
- hmac
--> hmac is calculated using privateKey of merchant

**Response headers**:
- hmac
--> hmac is calculated using privateKey of merchant

## 1. Balance request
**Request body**: 
- type: 'BALANCE'
- identifier: '<USER_IDENTITY>'

**Response header**:
- hmac
**Response body**:
- balance: <BALANCE_OF_USER>
- identifer: '<USER_IDENTITY>'

## 2. Bet request
Request body:
- type: 'BET'
- id: '<ID_OF_BET_REQUEST>'
- identifer: '<USER_IDENTITY>'
- amount: <BET_AMOUNT>


**Response header**:
- hmac
**Response body**:
- balance: <BALANCE_OF_USER_AFTER_BET>
- identifer: '<USER_IDENTITY>'

## 3. Win request
**Request body**:
- type: 'WIN'
- id: '<ID_OF_BET_REQUEST>'
- identifer: '<USER_IDENTITY>'
- amount: <BET_AMOUNT>

**Response header**:
- hmac
**Response body**:
- balance: <BALANCE_OF_USER_AFTER_WIN>
- identifer: '<USER_IDENTITY>'
