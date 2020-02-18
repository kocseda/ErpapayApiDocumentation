---
title: 3D'siz Ödeme
page-toc:
  active: true
taxonomy:
    category: docs
---

3D'siz ödeme işlemi bir kart ve tutar girildiğinde, girilen tutarın söz konusu kartın bakiyesinden düşürülmesini içerir. Eğer kart bilgileri geçerliyse 3D'siz ödeme işlemi tek çekim ve taksitli çekim işlemlerine uygundur.

## 1-Ödeme Bilgilerini Gönderme

**Servis Adresi:**

```yaml
https://testapi.erpara.com.tr/api/payment/nonsecure3D/v1
```

**Servise Gönderilmesi Gereken Parametreler:**

[div class="table-keycol"]
| Parametre İsmi | Tip | Zorunluluk | Açıklama |
| -------- | ----------- |
| **Amount** | decimal | Evet | Kartın bakiyesinden düşecek ödeme tutarı |
| **CardExpireMonth** | string | Evet | Ödeme işleminin yapılacağı kartın son kullanma tarihi ayı |
| **CardExpireYear** | string | Evet | Ödeme işleminin yapılacağı kartın son kullanma tarihi yılı |
| **CardNumber** | string | Evet | Ödeme işleminin yapılacağı kartın üzerinde yazan numara |
| **CardOwner** | string | Evet | Ödeme yapılacak kartın üzerinde yazan isim (kartın sahibi) |
| **CardSecurityCode** | string | Evet | Ödeme yapılacak kartın arka yüzünde yazan üç haneli güvenlik numarası |
| **ClientIp** | string | Evet | Ödemeyi gerçekleştiren üye iş yerine ait IP adresi |
| **Description** | string | Evet | Üye iş yerinin ödemeye ait doldurabileceği açıklama alanı |
| **BasketId** | string | Evet | Üye iş yerinin ilgili ödemenin sepetini tanımlamak için kullanılan id|
| **Installment** | string | Evet | Ödeme işleminin kaç orana bölünerek gerçekleşeceğini belirten taksit miktarı alanı |
| **Language** | string | Evet | Bu alana "TR" girilmelidir. |
| **MerchantId** | string | Evet | Üye iş yerine ait benzersiz Id numarası |
| **PaymentChannel** | string | Evet | Bu alana 'Api' yazılmalıdır |
| **Signature** | string | Evet | HMac Sha512 hashleme metodu kullanılarak oluşturulan imza |
| **TransactionId** | string | Evet | İstek esnasında gönderilen ve yanıtta döndürülen üye iş yerinin sipariş numarası |
| **TransactionTime** | timestamp | Evet | İşlemin gerçekleştiği unix timestamp değeri |
| **Id (Buyer)** | decimal | Hayır | Üye işyeri tarafındaki alıcıya ait id |
| **Name (Buyer)** | string | Hayır | Üye işyeri tarafındaki alıcıya ait ad |
| **Surname (Buyer)** | string | Hayır | Üye işyeri tarafındaki alıcıya ait soyad |
| **IdentityNumber (Buyer)** | string | Hayır | Üye işyeri tarafındaki alıcıya ait kimlik (TCKN) numarası |
| **City (Number)** | string | Hayır | Üye işyeri tarafındaki alıcıya ait kimlik (TCKN) numarası |
| **Country (Buyer)** | string | Hayır | Üye işyeri tarafındaki alıcıya ait ülke bilgisi |
| **Email (Buyer)** | string | Hayır | Üye işyeri tarafındaki alıcıya ait e-posta bilgisi. E-posta adresi alıcıya ait geçerli ve erişilebilir bir adres olmalıdır |
| **GsmNumber (Buyer)** | string | Hayır | Üye işyeri tarafındaki alıcıya ait GSM numarası |
| **Ip (Buyer)** | string | Hayır | Üye işyeri tarafındaki alıcıya ait IP adresi |
| **RegistrationAddress (Buyer)** | string | Hayır | Üye işyeri tarafındaki alıcıya ait kayıt adresi |
| **ZipCode (Buyer)** | string | Hayır | Üye işyeri tarafındaki alıcıya ait posta kodu |
| **RegistrationDate (Buyer)** | string | Hayır | Üye işyeri tarafındaki alıcıya ait kayıt tarihi. Tarih formatı 2015-09-17 23:45:06 şeklinde olmalıdır |
| **LastLoginDate (Buyer)** | string | Hayır | Üye işyeri tarafındaki alıcıya ait son giriş tarihi. Tarih formatı 2015-09-17 23:45:06 şeklinde olmalıdır |
| **ContactName (BillingAddress)** | string | Hayır | Üye işyeri tarafındaki fatura adresi ad soyad bilgisi |
| **City (BillingAddress)** | string | Hayır | Üye işyeri tarafındaki fatura adresi şehir bilgisi |
| **Country (BillingAddress)** | string | Hayır | Üye işyeri tarafındaki fatura adresi ülke bilgisi |
| **Address (BillingAddress)** | string | Hayır | Üye işyeri tarafındaki fatura adresi |
| **ZipCode (BillingAddress)** | string | Hayır | Üye işyeri tarafındaki fatura adresi posta kodu |
| **ContactName (ShippingAddress)** | string | Hayır | Üye işyeri tarafındaki teslimat adresi, ad, soyad bilgisi |
| **City (ShippingAddress)** | string | Hayır | Üye işyeri tarafındaki teslimat adresi şehir bilgisi |
| **Country (ShippingAddress)** | string | Hayır | Üye işyeri tarafındaki teslimat adresi ülke bilgisi |
| **Address (ShippingAddress)** | string | Hayır | Üye işyeri tarafındaki teslimat adresi |
| **ZipCode (ShippingAddress)** | string | Hayır | Üye işyeri tarafındaki teslimat adresi posta kodu |
| **Id (BasketItems)** | string | Hayır | Üye işyeri tarafındaki sepetteki ürüne ait id |
| **ItemType (BasketItems)** | string | Hayır | Üye işyeri tarafındaki sepetteki ürüne ait tip |
| **Name (BasketItems)** | string | Hayır | Üye işyeri tarafındaki sepetteki ürüne ait isim |
| **Category1 (BasketItems)** | string | Hayır | Üye işyeri tarafındaki sepetteki ürüne ait kategori 1 |
| **Category2 (BasketItems)** | string | Hayır | Üye işyeri tarafındaki sepetteki ürüne ait kategori 2 |
| **Price (BasketItems)** | decimal | Hayır | Üye işyeri tarafındaki sepetteki ürüne ait tutar. 0 ve 0’dan küçük olamaz, tutarlar toplamı sepet tutarına (price) eşit olmalıdır |
[/div]

**Signature (İmza) Oluşturma**

Aşağıdaki alanların art arda eklenmesi ve ardından hashlenmesi ile imza oluşmaktadır. Oluşan imzanın servise gönderilmesi gerekmektedir. Hashlemede kullanılacak algoritma HMac Sha512 algoritmasıdır. 

```yaml
secretKey + MerchantId + TransactionId + TransactionTime + Amount + Currency + Installment + CardNumber
```

**Servisten Gelen Yanıta Ait Parametreler**

[div class="table-keycol"]
| Parametre İsmi | Tip | Açıklama |
| -------- | ----------- |
| **TransactionId** | string | İstek esnasında gönderilen ve yanıtta döndürülen üye iş yerinin sipariş numarası |
| **Message** | string | Girilen bilgiler doğrultusunda servisten dönen mesaj |
| **MessageCode** | string | Dönen mesaja ait kod |
| **Success** | string | Girilen bilgiler doğrultusunda 3D ödeme isteği yapılabiliyorsa true, yapılamıyorsa false döner |
| **SystemTime** | number | Dönen yanıta ait unix timestamp değeri |
| **UserMessage** | string | Dönen yanıta ait kullanıcıya yönelik mesaj |
| **Description** | string | Üye iş yerinin doldurduğu açıklama alanında yazan metin |
[/div]

**JSON Request-Response (İstek-Yanıt)**

[prism classes="language-yaml line-numbers"]
//Request
  {
    "MerchantId": "5d891bbeea1e5e94b02b266b",
    "Language": "TR",
    "TransactionId": "e5180a5a-605b-4f91-b085-6427c595a138",
    "Currency": "TRY",
    "Installment": "3",
    "Description": "May the force be with you.",
    "BasketId": "123456",
    "PaymentChannel": "Api",
    "Amount": 12.5,
    "CardNumber": "4508034508034509",
    "CardExpireMonth": "12",
    "CardExpireYear": "30",
    "CardSecurityCode": "000",
    "CardOwner": "testname",
    "ClientIp": "10.10.2.27",
    "TransactionTime": "1571819068557",
    "Signature":    "6e08a470a313634f2f46c4fce375f1c86457fe6c196d0928d32feb0a2376a21db0600e0c268864869f1f975c6d0718301cc2acbeb76f54e89156b112c1199d7a"
  }
[/prism]

[prism classes="language-yaml line-numbers"]
//Response
{
	"TransactionId": "e5180a5a-605b-4f91-b085-6427c595a138",
    "SystemTime": 1571819080625,
    "Success": true,
    "MessageCode": "00",
    "Message": "Başarılı",
    "UserMessage": "3d işlem başlatma başarılı.",
	"Description": "May the force be with you."
}
[/prism]
