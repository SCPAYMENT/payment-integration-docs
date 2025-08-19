/*
Title: Enquiry
Sort: 5
*/


The enquiry request is acceptable with HTTPS POST method only. 


**Staging URL**:	http<span>s://</span>stagingpayment.scpayments.com.my/PreAuth/Enquiry

**Production URL**: http<span>s://</span>payment.scpayments.com.my/PreAuth/Enquiry

<br />
<hr />
<br /><br />

## Request

Merchant need to pass in the following for Enquiry transaction.

<br />

| Field Name      | Data Type   (Len) | M/O | Description                                                    |
|-----------------|-------------------|-----|----------------------------------------------------------------|
| MerchantID      | String (50)       | M   | Unique merchant ID assigned to each merchant by SC Payments |
| MerchantOrderNo | String (50)       | M   | MerchantOrderNo upon submission on Pre-Auth transaction        |
| Versioning      | Integer           | M   | API Versioning. Hard code 2.                                   |


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
        "Versioning": 2
    }
    
<br /><br />

<hr />

<br />

## <u>SCSign Calculation (Request)</u>

<br />

For Enquiry, SCSign generation will based on the raw request send or raw response received, and calculate with HMACSHA256. And **SCSign** value have to be capture at Http Header.

**Secret Key** : mSuE3Ttn5B8vJhe5ncMutMLV

<br /><br />

<u>**Raw Request**</u> 

<p style="word-wrap: break-word;">
{"MerchantID":"MID0001","MerchantOrderNo":"POST0001","Versioning":2}
</p>

**SCSign (Request)** : d275f570cbf67de8766e113e1988c4ceefa98999ddc460c2b51c30d909048b59


<br /><br />


## Response

Refer to the section <a href="https://devdocs.scpayments.com.my/pages/PreAuth/Response#ResponsePOST" target="_blank"><b>PRE AUTH > Response > 2. Sample of response (Http POST)</b></a>