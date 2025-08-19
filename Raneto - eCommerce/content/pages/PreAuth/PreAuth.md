/*
Title: Pre Auth
Sort: 1
*/

The Pre Authorization Payment Request is acceptable with HTTPS GET or POST method. 

<br />

**Staging URL**:	htt<span>ps://stagingpayment.scpayments.com.my/PreAuth

**Production URL**: htt<span>ps://payment</span>.scpayments.com.my/PreAuth

<br />
<br />


| Field Name        | Data Type (Len) | M/O | Description                                                                                                                                                                   |
|-------------------|-----------------|-----|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| MerchantID        | String (50)     | M   | Unique merchant   ID assigned to each merchant by SC Payments                                                                                                              |
| CurrencyCode      | String (5)      | M   | Transaction currency                                                                                                                                                          |
| PreAuthAmount     | Double (18,2)   | M   | Transaction Pre-Auth amount                                                                                                                                                   |
| MerchantOrderNo   | String (50)     | M   | Unique Order no generated in merchant system for each Pre-Auth transaction.                                                                                                   |
| MerchantOrderDesc | String (1000)   | M   | Order description                                                                                                                                                             |
| MerchantPaymentNo | String (50)     | M   | Unique Merchant Payment No for every transaction request                                                                                                                      |
| MerchantRef1      | String (100)    | O   | Merchant reference 1                                                                                                                                                          |
| MerchantRef2      | String (100)    | O   | Merchant reference 2                                                                                                                                                          |
| MerchantRef3      | String (100)    | O   | Merchant reference 3                                                                                                                                                          |
| CustReference     | String (50)     | O   | Customer reference<br />*It will use for customer tokenization if value provided                                                                                              |
| CustName          | String (150)    | O   | Customer name                                                                                                                                                                 |
| CustEmail         | String (150)    | O   | Customer email                                                                                                                                                                |
| CustPhoneNo       | String (50)     | O   | Customer phone number                                                                                                                                                         |
| CustAddress1      | String (100)    | O   | Customer address line 1                                                                                                                                                       |
| CustAddress2      | String (100)    | O   | Customer address line 2                                                                                                                                                       |
| CustCountryCode   | String (10)     | O   | Customer country code                                                                                                                                                         |
| CustAddressState  | String (150)    | O   | Customer state                                                                                                                                                                |
| CustAddressCity   | String (150)    | O   | Customer city                                                                                                                                                                 |
| CustPostcode      | String (10)     | O   | Customer Postcode                                                                                                                                                             |
| RedirectUrl       | String (1000)   | M   | Merchant return URL once the transaction   completed/failed                                                                                                                   |
| PaymentMethod     | String (100)    | O   | Submit blank to load SCPayments Payment Landing page.<br /> By specify payment option, it will redirect directly to Bank page.<br />(Refer to Appendix 2 - Payment Method) |
| Versioning        | Integer         | O   | API Versioning. Hard code 2.                                                                                                                                                  |
| SCSign            |                 | M   | Message sign (Refer to below <b>SCSign Calculation</b> section)                                                                                                               |



&nbsp;&nbsp;

**Legend:** <br />
**M: Mandatory field.**<br />
**O: Optional field. Value can be empty, but parameter must exist.**


&nbsp;


> **Request Sample (Http POST)**

        <html>
            <body>
                <form method="POST" name="payment" action="https://stagingpayment.scpayments.com.my/PreAuth" >
                    <input type="hidden" name="MerchantID" value="MID00001">
                    <input type="hidden" name="CurrencyCode" value="MYR">
                    <input type="hidden" name="PreAuthAmount" value="101.50">
                    <input type="hidden" name="MerchantOrderNo" value="POST0001">
                    <input type="hidden" name="MerchantOrderDesc" value="perfume">
                    <input type="hidden" name="MerchantPaymentNo" value="AHS917123">
                    <input type="hidden" name="MerchantRef1" value="mref1">
                    <input type="hidden" name="MerchantRef2" value="mref2">
                    <input type="hidden" name="MerchantRef3" value="mref3">
                    <input type="hidden" name="CustReference" value="ctRefIC111">
                    <input type="hidden" name="CustName" value="TomTom">
                    <input type="hidden" name="CustEmail" value="tomt@email.com">
                    <input type="hidden" name="CustPhoneNo" value="01938668396">
                    <input type="hidden" name="CustAddress1" value="add1">
                    <input type="hidden" name="CustAddress2" value="add2">
                    <input type="hidden" name="CustCountryCode" value="MY">
                    <input type="hidden" name="CustAddressState" value="semenyih">
                    <input type="hidden" name="CustAddressCity" value="selangor">
                    <input type="hidden" name="CustPostcode" value="12345">
                    <input type="hidden" name="RedirectUrl" value="https://www.shop.com">
                    <input type="hidden" name="PaymentMethod" value="">
                    <input type="hidden" name="Versioning" value="2">
                    <input type="hidden" name="SCSign" value="f4f697675814787ecb52711b8f894e2ec8046c4f1588546cd7b590cf47511da8">
                    <input type="submit" value="Submit">
                </form>
            </body>
        </html>

&nbsp;
&nbsp;

> **Request Sample (Http GET)**
    
        https://stagingpayment.scpayments.com.my/Payment
        ?MerchantID=MID00001
        &CurrencyCode=MYR
        &PreAuthAmount=101.50
        &MerchantOrderNo=POST0001
        &MerchantOrderDesc=Perfume
        &MerchantPaymentNo=AHS917123
        &MerchantRef1=mref1
        &MerchantRef2=mref2
        &MerchantRef3=mref3
        &CustReference=ctRefIC111
        &CustName=TomTom
        &CustEmail=tomt%40email.com
        &CustPhoneNo=01938668396
        &CustAddress1=add1
        &CustAddress2=add2
        &CustCountryCode=MY
        &CustAddressState=semenyih
        &CustAddressCity=selangor
        &CustPostcode=12345
        &RedirectUrl=https%3A%2F%2Fwww.shop.com
        &PaymentMethod=
        &Versioning=2
        &SCSign=f4f697675814787ecb52711b8f894e2ec8046c4f1588546cd7b590cf47511da8
****Note, above is one line string url.***

<br /><br /><br />


## <u>SCSign Calculation</u>

<br />

SCSign generation will concat all the above Table Field's value (in sequence), with HMACSHA256.

<br />

1. Concat all the value (refer to Sample)

    > **String to sign** : <p style="word-wrap: break-word;">MID00001MYR101.50POST0001perfumeAHS917123mref1mref2mref3ctRefIC111TomTomtomt<span>@</span>email.com01938668396add1add2MYsemenyihselangor12345https<span>​://w</span>ww.shop.com2</p>

<br />

2. Calculate with HMACSHA256
    > **Secret Key** : mSuE3Ttn5B8vJhe5ncMutMLV

    > **SCSign** : f4f697675814787ecb52711b8f894e2ec8046c4f1588546cd7b590cf47511da8


<br /><br />


## Response

Refer to the section <a href="https://devdocs.scpayments.com.my/pages/PreAuth/Response#ResponseGET" target="_blank"><b>PRE AUTH > Response > 1. Sample of response (Redirect / Http GET)</b></a>