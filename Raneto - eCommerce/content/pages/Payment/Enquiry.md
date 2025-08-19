/*
Title: Enquiry
Sort: 7
*/


The Payment Request is acceptable with HTTPS POST method only. 


**Staging URL**:	http<span>s://</span>stagingpayment.scpayments.com.my/enquiry

**Production URL**: http<span>s://</span>payment.scpayments.com.my/enquiry

<br />
<hr />
<br /><br />

## Request

Merchant need to pass in the following for transaction status enquiry.

<br />

| Field Name      | Data Type   (Len) | M/O | Description                                                                              |
|-----------------|-------------------|-----|------------------------------------------------------------------------------------------|
| MerchantID      | String (50)       | M   | Unique merchant ID assigned to each merchant by   SC Payments                         |
| MerchantOrderNo | String (50)       | M   | Unique Order no generated in merchant system (Based on value submit on Payment Request). |
| Versioning      | Integer           | M   | API Versioning. Hard code 6.                                                             |

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
        "Versioning": 6
    }
    
<br /><br />

<hr />

<br />

## Response


Refer to the section <a href="https://devdocs.scpayments.com.my/pages/Payment/RedirectCallback#ResponseRedirect" target="_blank"><b>PAYMENT > Response Redirect / Callback > 1. Response Sample (Redirect)</b></a>