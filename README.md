# ChatApp #

![](http://g.recordit.co/JYruQDLd0h.gif)

Django yordamida qurilgan kichik va funksional foydalanuvchidan foydalanuvchiga xabar almashish markazi. Ushbu ilova REST API'ga ega va mijozlarni yangi xabarlardan xabardor qilish va takroriy so‘rovlarni (polling) oldini olish uchun WebSocketlardan foydalanadi.

## Arxitektura ##
 - Foydalanuvchi tizimga kirganda, frontend foydalanuvchilar ro‘yxatini yuklab oladi va serverga WebSocket ulanishini ochadi (bildirishnomalar kanali).
 - Foydalanuvchi boshqa foydalanuvchi bilan suhbatni tanlaganda, frontend ularning oxirgi 15 xabarini yuklab oladi (sozlamalar bo‘yicha o‘zgartirilishi mumkin).
 - Foydalanuvchi xabar yuborganida, frontend REST API'ga POST yuboradi, keyin Django xabarni saqlaydi va WebSocket ulanishi orqali ishtirok etgan foydalanuvchilarni yangi xabar ID'si bilan xabardor qiladi.
 - Frontend yangi xabar bildirishnomasini (xabar ID'si bilan) olganda, API'ga GET so‘rovini yuboradi va qabul qilingan xabarni yuklab oladi.

## Masshtablash ##

### So‘rovlar ###
"Channels Django'ni ko‘p jarayonli modelga olib kelgani sababli, endi siz barcha narsalarni WSGI server bilan bitta jarayonda ishlatishingiz shart emas (albatta, Channels'dan foydalanishni xohlamasangiz, buni qilishingiz mumkin). Buning o‘rniga, siz bir yoki bir nechta interfeys serverlari va bir yoki bir nechta ishchi serverlarni ishlatasiz, ular ilgari sozlangan kanal qatlami orqali ulanadi."

Ushbu loyihada In-Memory kanal tizimidan foydalanilmoqda, lekin Redis backendiga o‘zgartirilishi mumkin, bu esa ko‘p ishchilarni tarqatilgan muhitda ishlatishni yaxshilaydi.

Qo‘shimcha ma’lumot uchun quyidagi havolani ko‘ring:  
https://channels.readthedocs.io/en/latest/introduction.html

**Yangilanish 04/06/19**

- Paketlarni boshqarish uchun pipenv'dan foydalanish
- Channels 2 ga o‘tish
- Redis kanal qatlami sifatida foydalanish. Qo‘shimcha ma’lumot uchun [channels_redis](https://github.com/django/channels_redis) ni ko‘ring.

### Ma’lumotlar bazasi ###
Ushbu demo uchun oddiy MySQL sozlamasi ishlatilmoqda. Agar ko‘proq samaradorlik talab qilinsa, MySQL klasteri yoki shardlash joriy qilinishi mumkin.

Eslatma: Ishlashni yaxshilash uchun indekslardan foydalanilmoqda.

## Farazlar ##
Vaqt cheklovlari sababli ushbu loyiha quyidagilardan mahrum:

- Foydalanuvchi ro‘yxatdan o‘tishi / Parolni unutdim funksiyasi
- Foydalanuvchi tanlash uchun sahifalash
- Yaxshi test qamrovi
- Yaxshi izohlar / hujjatlash matnlari
- Frontend testlari
- Zamonaviy frontend ramkasi (masalan, React)
- Frontend paketi (avtomatik linting, yig‘ish va siqish)
- Yaxshi foydalanuvchi tajribasi (UX) / dizayn (oddiy bootstrap ko‘rinishida)

## Ishga tushirish ##

0. Loyiha ildiz katalogiga o‘ting

1. Virtualenv yarating va faollashtiring (Python 3)
```bash
pipenv --python 3 shell
