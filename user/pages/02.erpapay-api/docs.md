---
title: API
taxonomy:
    category: docs
---

## API Entegrasyonu

Üye iş yerinin API entegrasyonu için kullandığı ödeme formunda bazı kontrollerin bulunması gerekmektedir. Bu kontroller: 

* Kart numarasının Luhn Algoritmasından geçmesi gerekmektedir. 
* Kartın son kullanma tarihinin geçmemiş olması gerekmektedir. 
* Kart sahibinin isim ve soy ismi bilgilerinin girilmesi gerekmektedir. 

Üye iş yerlerine sunulan servisler:

## Taksit ve Bin Sorgulama

Bu metot ile kartın ilk 6 hanesini girerek işlemlere yapılabilecek taksit oranları bilgisine ulaşabilirsiniz. Taksit oranları kartın bağlı olduğu bankaya bağlı olarak ortaya çıkmaktadır. 

## 3D ile Ödeme

Bu metot ile girilen kart bilgileri ile işleme ait miktar kartın bakiyesinden çekilir. Tek çekim ve taksitli çekim işlemleri gerçekleştirilebilir. 

## Ödeme Sorgulama

Bu metot ile bir islemin kayda geçip geçmediği sorgulanır ve işlemin detay bilgilerine ulaşılır. 

**3D Güvenli Ödeme İşlem Akışı**

![Standard Page](3Dsema.png)

