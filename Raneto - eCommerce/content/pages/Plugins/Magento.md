/*
Title: Magento
Sort: 4
*/

Build multi-channel commerce experiences for B2B and B2C customers on a single platform. From catalog to payment to fulfillment, our future-proof technology gives you a commerce platform that’s endlessly flexible, extensible and scalable. Whether you’re a B2B ready to go direct to consumer (D2C) or a B2C managing several brands in 10 different languages, Adobe Commerce lets you manage multiple sales channels and brands and expand into new countries, simply, from one platform. Adobe Commerce is completely scalable and extensible, with a modular core and headless capabilities that allow you to quickly incorporate new technologies.

### Download plugin <a href="https://github.com/Alpha-Fintech/Plugin.Magento.2.3.6" target="_blank">here</a>.

<br /><br />

Setup Your Plugin :

1. Unzip & Copy the files to a directory under your Magento application.
2. Access the command prompt as an administrator
3. Go to your Magento-2 installation directory and run the following command: **php bin/magento setup:upgrade && php bin/magento cache:flush**
4. In your Magento settings, go to **Stores > Configuration**

<img src="https://devdocs.scpayments.com.my/images/Magento/magento_pic1.png" algin="left" alt="Plugin Settings" />

<br />

5. Select **Sales > Payment Methods** from the sidebar.

<img src="https://devdocs.scpayments.com.my/images/Magento/magento_pic2.png" algin="left" alt="Plugin Settings" />

<br />

6. Configure below Settings and Save.

<img src="https://devdocs.scpayments.com.my/images/Magento/magento_pic3.png" algin="left" alt="Plugin Settings" />

<br />

- 6.1. Enable Payment Gateway.

- 6.2. **Merchant ID** : Get your Merchant ID from SC Payments (Different between UAT and Production).

- 6.3. **Secret Key** : Get your Secret Key from SC Payments (Different between UAT and Production).

- 6.4. **Mode** : Select your environment whether you are in Development or ready for live.
