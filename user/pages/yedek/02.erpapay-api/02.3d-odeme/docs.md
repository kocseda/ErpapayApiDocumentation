---
title: 3D İle Ödeme
page-toc:
  active: true
taxonomy:
    category: docs
---

3D ile ödeme işlemi bir kart ve tutar girildiğinde, girilen tutarın söz konusu kartın bakiyesinden düşürülmesini içerir. Eğer kart bilgileri geçerliyse 3D ile ödeme işlemi tek çekim ve taksitli çekim işlemlerine uygundur.

3D ile ödeme API ile üç aşamada yapılır.

## 1-Ödeme Bilgilerini Gönderme

**Servis Adresi:**

```yaml
https://testapi.erpara.com.tr/api/payment3d/secure3D/v1
```

**Servise Gönderilmesi Gereken Parametreler:**

[div class="table-keycol"]
| Parametre İsmi | Tip | Zorunluluk | Açıklama |
| -------- | ----------- |
| **Amount** | decimal | Evet | Kartın bakiyesinden düşecek ödeme tutarı |
| **BackrefUrl** | string | Evet | 3D Secure işleminde üye iş yerine başarılı ya da hatalı sonucu bildiren URL adresi. Bu adrese sonuç JSON olarak dönmektedir. |
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
| **Message** | string | Girilen bilgiler doğrultusunda servisten dönen mesaj |
| **MessageCode** | string | Dönen mesaja ait kod |
| **Secure3dUrl** | string | Müşterinin ekranında gösterilmesi gereken 3D şifre ekranının oluştuğu Url adresi |
| **Success** | string | Girilen bilgiler doğrultusunda 3D ödeme isteği yapılabiliyorsa true, yapılamıyorsa false döner |
| **SystemTime** | number | Dönen yanıta ait unix timestamp değeri |
| **UserMessage** | string | Dönen yanıta ait kullanıcıya yönelik mesaj |
[/div]

**JSON Request-Response (İstek-Yanıt)**

[prism classes="language-yaml line-numbers"]
//Request
  {
    "MerchantId": "5d891bbeea1e5e94b02b266b",
    "Language": "TR",
    "TransactionId": "e5180a5a-605b-4f91-b085-6427c595a138",
    "BackrefUrl": "http://backref.merchant.com/refpage",
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
    "Signature": "6e08a470a313634f2f46c4fce375f1c86457fe6c196d0928d32feb0a2376a21db0600e0c268864869f1f975c6d0718301cc2acbeb76f54e89156b112c1199d7a"
  }
[/prism]

[prism classes="language-yaml line-numbers"]
//Response
{
    "Secure3dUrl": "https://testapi.erpara.com.tr/api/payment3d/get3dSign/v1?id=e5180a5a-605b-4f91-b085-6427c595a138",
    "SystemTime": 1571819080625,
    "Success": true,
    "MessageCode": "00",
    "Message": "Başarılı",
    "UserMessage": "3d işlem başlatma başarılı."
}
[/prism]

## 2- 3D Güvenli Ödeme İmza İçin Şifre Gönderme

**Servis Adresi:**


```yaml
https://testapi.erpara.com.tr/api/payment3d/get3dSign/v1
```

Birinci aşamada servise gönderilen ödeme bilgilerinin ardından servisten bir yanıt döner. Eğer işlem başarılıysa dönen yanıtın içerisinde yer alan Secure3DUrl içerisinde URL adresi saklar. Bu adres ile kullanıcının 3D imza bilgisini girmesi sağlanır. 
Kullanıcı söz konusu adresi bir tarayıcıda açarak bankadan şifre talep eder ve SMS ile gelen şifreyi girer. Bu aşamadan sonra banka kredi kartı doğrulaması yapar. Bankadan gelen yanıt doğrultusunda kullanıcı işleminin gerçekleşip gerçekleşmediğini tarayıcıda açtığı sayfada görebilir. Ayrıca bankadan dönen yanıt BackrefUrl alanına yazılan adrese JSON şeklinde döner.

Örnek yanıt:

[prism classes="language-yaml line-numbers"]
{
    "TransactionId": "e5180a5a-605b-4f91-b085-6427c595a138",
    "SystemTime": "1575969358720",
    "Success": true,
    "MessageCode": "7280",
    "Message": "İşleminiz başarıyla gerçekleştirildi",
    "UserMessage": "3D Secure işlemi başarıyla gerçekleştirildi"
}
[/prism]

## 2- 3D Güvenli Ödeme Tamamlama

**Servis Adresi:**

```yaml
https://testapi.erpara.com.tr/api/payment3d/complete3dpayment/v1
```

Kullanıcının Sedure2DUrl adresini tarayıcıda açması ve başarılı bir şekilde 3D imza adımını geçmesinin ardından 3D güvenli ödeme tamamlama adımına geçilir. Bu adımda gerekli parametreler verilmesi ile 3D güvenli ödeme işlemi sonuca ulaşır.

**Servisten Gönderilmesi Gereken Parametreler**

[div class="table-keycol"]
| Parametre İsmi | Tip | Zorunluluk | Açıklama |
| -------- | ----------- |
| **MerchantId** | string |  Evet | Üye iş yerine ait benzersiz Id numarası |
| **TransactionId** | string | Evet | İstek esnasında gönderilen ve yanıtta döndürülen üye iş yerinin sipariş numarası |
[/div]

**Servise Gelen Yanıta Ait Parametreler**

[div class="table-keycol"]
| Parametre İsmi | Tip | Açıklama |
| -------- | ----------- |
| **Message** | string | Girilen bilgiler doğrultusunda servisten dönen mesaj |
| **MessageCode** | string | Dönen mesaja ait kod |
| **Success** | string | Girilen bilgiler doğrultusunda 3D ödeme isteği yapılabiliyorsa true, yapılamıyorsa false döner |
| **SystemTime** | timestamp | Dönen yanıta ait unix timestamp değeri |
| **UserMessage** | string | Dönen yanıta ait kullanıcıya yönelik mesaj |
[/div]

**JSON Request-Response (İstek-Yanıt)**

[prism classes="language-yaml line-numbers"]
//Request
{
    "MerchantId": "5d891bbeea1e5e94b02b266b",
    "TransactionId": "e5180a5a-605b-4f91-b085-6427c595a138",
}

[/prism]

[prism classes="language-yaml line-numbers"]
//Response
{
    "SystemTime": 1571819080625,
    "Success": true,
    "MessageCode": "7280",
    "Message": "İşleminiz başarıyla gerçekleştirildi",
    "UserMessage": "İşleminiz başarıyla gerçekleştirildi."
}
[/prism]
