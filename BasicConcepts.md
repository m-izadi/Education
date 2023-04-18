
## Node

    - به هر instance از الستیک سرچ Node میگن

## Documents

    دیتا ها در قالب json و به صورت Document داخل الستیک ذخیره میشه
    هر داکیومنت یک ID یونیکی داره ک یا به صورت دستی بهش اختصاص میدیم یا الستیک خودش رندوم ی ID میده

## Index

    برای دسته بندی , داکیومنت های مشابه رو جز یک index میکنیم تا برای سرچ و جست و جو در همان ایندکس مربوطه سرچ بکنیم
    ایندکس ها باعث افزایش سرعت در جست و جو و کمتر شدن میزان پردازش سرویس میشه
    ایندکس داخل الستیک ۲ تا معنی داره
    ۱ دسته بندی کردن داکیومنت ها
    ۲ ساختن داکیومنت مثل ایندکس اینگ

## Shared

    با Shared ایندکس ها رو به چند تیکه ی مختلف تقسیم و روی نود های مختلف ذخیره کنیم
    باعث سرعت و پردازش سریع تر برای جست و جو دیتا میشود

## replica Shared

    از دیتای ایندکسی ک داخل هر نود هست کپی میگیره و داخل یک نود دیگه ذخیره میکنه


## Security certificates and keys

    used to connect a Kibana instance to your secured Elasticsearch cluster and to encrypt internode communication

## Version

    مشخص میکنه هر داکیومنت چند بار تغییر کرده

## QuearyParametr
    به وسیله ی پارامتر روی دیتای نمایشی میتونیم یکسری تغییرات بدیم به طوری مثال دستوری     GET _cat/indices/gis

    GET _cat/indices/gis/?v=true اما ?v=true نشون میده هر سطر مربوط به چیه






p0-∞ = Primery Shared

R0-∞ = Replica Shared
