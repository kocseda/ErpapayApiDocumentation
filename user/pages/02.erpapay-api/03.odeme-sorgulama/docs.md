---
title: Ödeme Sorgulama
page-toc:
  active: true
taxonomy:
    category: docs
---

## Ödeme Sorgulama

**Servis Adresi:**

```yaml
https://testapi.erpara.com.tr/api/payment3d/paymentInfo/v1
```

Ödeme sorgulama işlemi üye iş yeri Id’si ve bir sipariş numarası girildiğinde, söz konusu sipariş numarasına ait ödemenin kayıtlara geçip geçmeme bilgisi ve ödemenin detayları ile ilgili bilgi verir.

**Servise Gönderilmesi Gereken Parametreler**

[div class="table-keycol"]
| Parametre İsmi | Tip | Zorunluluk | Açıklama |
| -------- | ----------- |
| **MerchantId** | string |  Evet | Üye iş yerine ait benzersiz Id numarası |
| **TransactionId** | string | Evet | İstek esnasında gönderilen ve yanıtta döndürülen üye iş yerinin sipariş numarası |
[/div]

**Servisten Gelen Yanıta Ait Parametreler**

[div class="table-keycol"]
| Parametre İsmi | Tip | Açıklama |
| -------- | ----------- |
| **TransactionId** | string | İstek esnasında gönderilen ve yanıtta döndürülen üye iş yerinin sipariş numarası |
| **SystemTime** | timestamp | Dönen yanıta ait unix timestamp değeri |
| **Success** | string | Girilen bilgiler doğrultusunda 3D ödeme isteği yapılabiliyorsa true, yapılamıyorsa false döner |
| **Amount** | decimal | Kartın bakiyesinden düşen ödeme tutarı |
| **TotalPay** | string | Üye iş yerine ödenecek toplam tutar |
| **MessageCode** | string | Dönen mesaja ait kod |
| **Message** | string | Girilen bilgiler doğrultusunda servisten dönen mesaj |
| **UserMessage** | string | Dönen yanıta ait kullanıcıya yönelik mesaj |
[/div]

**Servisten Dönen Mesaj Kodları**

[div class="table-keycol"]
| MessageCode | Açıklama |
| -------- | ----------- |
| **MessageCode = 0000** | İşlem kayıt edilmiş ve başarılı |
| **MessageCode = 7712** | İşlem bulunamadı |
| **MessageCode = 7719** | İşlem kayıt edilmiş ancak başarısız. |
[/div]

**JSON Request-Response (İstek-Yanıt)**

[prism classes="language-yaml line-numbers"]
//Request
{
    "MerchantId": "5d891bbeea1e5e94b02b266b",
    "TransactionId": "test123456789"
}
[/prism]

[prism classes="language-yaml line-numbers"]
//Response
{
    "TransactionId": "test123456789",
    "SystemTime": 1574077298636,
    "Success": true,
    "Amount": "100.00",
    "TotalPay": "98.1500",
    "MessageCode": "0000",
    "Message": "İşlem Başarılı",
    "UserMessage": "İşlem Başarılı"
}
[/prism]