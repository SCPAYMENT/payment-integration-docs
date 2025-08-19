/*
Title: Capture / Sale (Void)
Sort: 4
*/


The Capture / Sale (Void) request is acceptable with HTTPS POST method only. 


**Staging URL**:	http<span>s://</span>stagingpayment.scpayments.com.my/PreAuth/Capture/Void

**Production URL**: http<span>s://</span>payment.scpayments.com.my/PreAuth/Capture/Void

<br />
<hr />
<br /><br />

## Request

Merchant need to pass in the following for Capture / Sale (Void) transaction.

<br />

| Field Name        | Data Type   (Len) | M/O | Description                                                    |
|-------------------|-------------------|-----|----------------------------------------------------------------|
| MerchantID        | String (50)       | M   | Unique merchant ID assigned to each merchant by SC Payments |
| MerchantOrderNo   | String (50)       | M   | MerchantOrderNo upon submission on Pre-Auth transaction        |
| MerchantPaymentNo | String (50)       | M   | Unique Merchant Payment No for every transaction request       |
| PreAuthTxnRefNo   | String (50)       | M   | TxnRefNo from successful Pre-Auth transaction                  |
| VoidAmount        | Decimal (18,2)    | M   | Exact capture / sale transaction void amount                   |


&nbsp;
&nbsp;



| Http Header | Data Type   (Len) | M/O | Description                                                     |
|-------------|-------------------|-----|-----------------------------------------------------------------|
| SCSign      |                   | M   | Message sign (Refer to below <b>SCSign Calculation<b/> section) |

****Note, field SCSign have to put in Http Header.***

<br /><br />


> **Request Sample**
    
    {
        "MerchantID": "MID0001",
        "MerchantOrderNo": "POST0001",
        "MerchantPaymentNo": "AHS92738",
        "PreAuthTxnRefNo": "8712893729013",
        "VoidAmount": 25.00
    }
    
<br /><br />

<hr />

<br />

## <u>SCSign Calculation (Request)</u>

<br />

For Pre-Auth (Void), SCSign generation will based on the raw request send or raw response received, and calculate with HMACSHA256. And **SCSign** value have to be capture at Http Header.

**Secret Key** : mSuE3Ttn5B8vJhe5ncMutMLV

<br /><br />

<u>**Raw Request**</u> 

<p style="word-wrap: break-word;">
{"MerchantID":"MID0001","MerchantOrderNo":"POST0001","MerchantPaymentNo":"AHS92738","PreAuthTxnRefNo": "8712893729013","VoidAmount":25.00}
</p>

**SCSign (Request)** : 2db5c39fa1a5a686c3f6760d04e45ece8835221388f05f68db67e66ef4bc28cd


<br /><br />


## Response

Refer to the section <a href="https://devdocs.scpayments.com.my/pages/PreAuth/Response#ResponsePOST" target="_blank"><b>PRE AUTH > Response > 2. Sample of response (Http POST)</b></a>