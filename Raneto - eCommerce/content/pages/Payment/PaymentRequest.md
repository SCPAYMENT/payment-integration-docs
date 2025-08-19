/*
Title: Request
Sort: 5
*/

The Payment Request is acceptable with HTTPS GET or POST method. 

<br />

**Staging URL**:	htt<span>ps://stagingpayment.scpayments.com.my/payment

**Production URL**: htt<span>ps://payment</span>.scpayments.com.my/payment

<br />
<br />

| Field Name        | Data Type (Len) | M/O | Description                                                                                                          |
|-------------------|-----------------|-----|----------------------------------------------------------------------------------------------------------------------|
| MerchantID        | String (50)     | M   | Unique merchant   ID assigned to each merchant by SC Payments                                                     |
| CurrencyCode      | String (5)      | M   | Transaction currency                                                                                                 |
| TxnAmount         | Decimal (18,2)  | M   | Transaction amount                                                                                                   |
| MerchantOrderNo   | String (50)     | M   | Unique Order no generated in merchant system                                                                         |
| MerchantOrderDesc | String (1000)   | M   | Order description                                                                                                    |
| MerchantRef1      | String (100)    | O   | Merchant reference                                                                                                   |
| MerchantRef2      | String (100)    | O   | Merchant reference                                                                                                   |
| MerchantRef3      | String (100)    | O   | Merchant reference                                                                                                   |
| CustReference     | String (50)     | O   | Customer reference                                                                                                   |
| CustName          | String (150)    | O   | Customer name                                                                                                        |
| CustEmail         | String (150)    | O   | Customer email                                                                                                       |
| CustPhoneNo       | String (50)     | O   | Customer phone number                                                                                                |
| CustAddress1      | String (100)    | O   | Customer address line 1                                                                                              |
| CustAddress2      | String (100)    | O   | Customer address line 2                                                                                              |
| CustCountryCode   | String (10)     | O   | Customer country code                                                                                                |
| CustAddressState  | String (150)    | O   | Customer state                                                                                                       |
| CustAddressCity   | String (150)    | O   | Customer city                                                                                                        |
| RedirectUrl       | String (1000)   | M   | Merchant return URL once the transaction   completed/failed                                                          |
| PaymentMethod     | String (100)    | O   | Specify the payment option, thus it will redirect directly to Bank page.<br />(Refer to Appendix 2 - Payment Method) |
| Versioning        | Integer         | O   | API Versioning. Hard code 6.                                                                                         |
| SCSign            |                 | M   | Message sign (Refer to below <b>SCSign Calculation</b> section)                                                      |




&nbsp;&nbsp;

**Legend:** <br />
**M: Mandatory field.**<br />
**O: Optional field. Value can be empty, but parameter must exist.**


&nbsp;


> **Request Sample (Http POST)**

        <html>
            <body>
                <form method="POST" name="payment" action="https://stagingpayment.scpayments.com.my/payment" >
                    <input type="hidden" name="MerchantID" value="MID00001">
                    <input type="hidden" name="CurrencyCode" value="MYR">
                    <input type="hidden" name="TxnAmount" value="101.50">
                    <input type="hidden" name="MerchantOrderNo" value="POST0001">
                    <input type="hidden" name="MerchantOrderDesc" value="perfume">
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
                    <input type="hidden" name="RedirectUrl" value="https://www.MerchantRedirectURL.com">
                    <input type="hidden" name="PaymentMethod" value="CARD">
                    <input type="hidden" name="Versioning" value="6">
                    <input type="hidden" name="SCSign" value="9a07b085345f78949ebbdcc936f6b3cd97a17f7083e2c94617914b30a59a7bc4">
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
        &TxnAmount=101.50
        &MerchantOrderNo=POST0001
        &MerchantOrderDesc=Perfume
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
        &CustAddressCity=Selangor
        &RedirectUrl=https%3A%2F%2Fwww.MerchantRedirectURL.com
        &PaymentMethod=CARD
        &Versioning=6
        &SCSign=9a07b085345f78949ebbdcc936f6b3cd97a17f7083e2c94617914b30a59a7bc4
****Note, above is one line string url.***

<br /><br /><br />


## <u>SCSign Calculation</u>

<br />

SCSign generation will concat all the above Table Field's value (in sequence), with HMACSHA256.

<br />

1. Concat all the value (refer to Sample)

    > **String to sign** : <p style="word-wrap: break-word;">MID00001MYR101.50POST0001perfumemref1mref2mref3ctRefIC111TomTomtomt<span>@</span>email.com01938668396add1add2MYsemenyihselangorhttps<span>​://w</span>ww.MerchantRedirectURL.comCARD6</p>

<br />

2. Calculate with HMACSHA256
    > **Secret Key** : mSuE3Ttn5B8vJhe5ncMutMLV

    > **SCSign** : 9a07b085345f78949ebbdcc936f6b3cd97a17f7083e2c94617914b30a59a7bc4


<br /><br />


## Response

Refer to the section <a href="https://devdocs.scpayments.com.my/pages/Payment/RedirectCallback#ResponseRedirect" target="_blank"><b>PAYMENT > Response Redirect / Callback > 1. Response Sample (Redirect)</b></a>