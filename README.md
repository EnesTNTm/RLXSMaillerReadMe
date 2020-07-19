

# RLXSMailler Guide



Yapabileceklerinize Sınır Tanımayın Bu RLXS Mailler Eklentiniz ile Kolay bir biçimde Mail Gönderin.



Yapabilecekleriniz :



- E-Posta Gönderebilirsiniz

- E-Posta Hesaplarını Kaldırabilirsiniz

- E-Posta Hesapları Oluşturabilirsiniz



Bunlar için sadece 1 adım uzaktasınız Yeni Bir Dosya Oluştur



- Adım 1 :

> Dosya Oluştur ve sendmail.rlxs yap adını



- Adım 2 :

> Dosyanın İlk Satırına

```rlxs

RLXS;

use RLXSMailler.RLXSMailler;

RLXS;

```

> Yaz Ve Bunu Kaydet



- Adım 3 :

> Bu İşlemlerden Sonra Alt Satırlara geç ve

```rlxs

RLXS;

String host = "mail.mydomainto.com";

rlxs.Ports port = "465";

String password = "123456";

String email = "test@mydomainto.com";

String type = "ssl";

String mailtype = "text";

RLXS;

```

> Tamamdır,

> Artık Mail Gönderme Satırlarımız Tam İstediğimiz Şekilde Hazır



### Bir Mail Nasıl Oluşturabilirim ?

> Mail Oluşturmak İçin Yukardaki Adımları Tamamlaman Gerekir

> Şimdi Nasıl Olacağını Anlatalım

> Bu Kodların Alt Satırlarına Geç

```rlxs

RLXS;

RLXSMailler.Mail(email, password, port, host, type, mailtype).Create();

RLXS;

```

> Bu Sayede Artık Mailiniz Oluşturuldu



### Bir Mail Nasıl Silebilirim ?

> Şimdi Nasıl Olacağını Anlatalım

> Bu Kodların Alt Satırlarına Geç

```rlxs

RLXS;

RLXSMailler.Mail(email, password, port, host, type, mailtype).Delete();

RLXS;

```

> Bu İşlemde Tamamlandı Artık Bu Mail Hesabı Yok



### Bir Mail Nasıl Atarım ?

> Bu İşlemde Sistem Kolaydır

```rlxs

RLXS;

RLXSMailler.Mail(email, password, port, host, type, mailtype).Send("Your Text Message", ["info@gmail.com"]);

RLXS;

```

> Bu Tekli Bir Mail Gönderme İşlemiydi



### Birden Fazla Kişiye Nasıl Mail Atabilirim ?

> Bu İşlemde Tekli Atma Kadar Kolaydır Aslında

> Göreceksin

```rlxs

RLXS;

Array kisiler = ["info@gmail.com", "info@yenimiras.com", "deneme@yenimiras.com"];

RLXSMailler.Mail(email, password, port, host, type, mailtype).Send("Your Text Message", kisiler);

RLXS;

```

> Bu Şekilde Birden Fazla Mail Atma Bu Kadar Kolay

> Yakında Eklenecek Olan Eventler İle İşlemleriniz Daha Kolay Hale Gelecektir.



### Kendi Socket Bağlantım ile İşlem Nasıl Yapabilirim ?

```rlzs

RLXS;

use RLXSMailler.SendMail;

use RLXSMailler.RLXSMailler;

if(RLXSMailler.ConnectServer(convert.socketType(host, port, type))){

    rlxs.library.getLibrary("Mailler").sendMail(RLXSMailler.aSocket, email, password).message("Send To Mail").to("info@gmail.com").then(RLXSMailler.End());

}

RLXS;

```
