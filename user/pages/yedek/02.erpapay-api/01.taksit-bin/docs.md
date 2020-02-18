---
title: Taksit ve Bin Sorgulama
taxonomy:
    category: docs
process:
    twig: true
---

**Servis Adresi:**

```yaml
https://testapi.erpara.com.tr/api/payment3d/bin/v1
```

Taksit sorgulama işlemi bir kredi kartı girildiğinde ve kredi kartı anlaşmalı bir taksit programına dahilse, kartın ilk 6 hanesinin kullanılması ile taksit oranları hakkında bilgi vermektedir. 

**Servise Gönderilmesi Gereken Parametreler:**

[div class="table-keycol"]
| Parametre İsmi | Tip | Zorunluluk | Açıklama |
| -------- | ----------- |
| **MerchantId** | string | Evet | Üye iş yerine ait benzersiz Id numarası |
| **BinCode** | string | Evet | Kartın ilk 6 hanesi |
[/div]

**Servisten Gelen Yanıta Ait Parametreler:**

[div class="table-keycol"]
| Parametre İsmi | Tip | Açıklama |
| -------- | ----------- |
| **BankCode** | string | Kartın ait olduğu bankanın standard kodu. |
| **BankName** | string | Kartın ait olduğu bankanın adı. |
| **CardBrand** | string | Kartın ait olduğu ödeme kuruluşu. |
| **CardType** | string | Girilen kartın türü. |
| **installment (Installments)** | number | Girilen kart ile yapılabilecek taksit miktarı. |
| **BankName** | string | Kartın ait olduğu bankanın adı. |
| **CardBrand** | string | Kartın ait olduğu ödeme kuruluşu. |
| **CardType** | string | Girilen kartın türü. |
[/div]

**Servisten Dönen Mesaj Kodları:**

[div class="table-keycol"]
| MessageCode | Açıklama |
| -------- | ----------- |
| **MessageCode = 00** | Başarılı |
| **MessageCode = 7201** | Geçersiz MerchantId |
[/div]

**JSON Request-Response (İstek-Yanıt)**

[prism classes="language-yaml line-numbers"]
//Request
{
    "MerchantId": "5d891bbeea1e5e94b02b266b",
    "BinCode": "450803"
}
[/prism]

[prism classes="language-yaml line-numbers"]
//Response
{
    "SystemTime": 1571813371325,
    "Success": true,
    "MessageCode": "00",
    "Message": "Başarılı",
    "UserMessage": "İşleminiz başarıyla gerçekleştirildi.",
    "SaleRate": "1.75",
    "CardType": "Credit",
    "CardBrand": "VISA",
    "BankCode": "64",
    "BankName": "T. İŞ BANKASI A.Ş.",
    "IsInstallment": true,
    "Installments": [
        {
            "installment": 1,
            "gatewayId": "5d9fb188e578e039573880b9",
            "ccMerchantRateInstallment": "1.92"
        },
        {
            "installment": 2,
            "gatewayId": "5d9fb188e578e039573880b9",
            "ccMerchantRateInstallment": "4"
        },
        {
            "installment": 3,
            "gatewayId": "5d9fb188e578e039573880b9",
            "ccMerchantRateInstallment": "5"
        },
        {
            "installment": 6,
            "gatewayId": "5d9fb188e578e039573880b9",
            "ccMerchantRateInstallment": "8"
        },
        {
            "installment": 9,
            "gatewayId": "5d9fb188e578e039573880b9",
            "ccMerchantRateInstallment": "12"
        },
        {
            "installment": 12,
            "gatewayId": "5d9fb188e578e039573880b9",
            "ccMerchantRateInstallment": "15"
        }
    ]
}
[/prism]
