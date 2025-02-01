# Message Queue Nədir?
Message queue, proqramlaşdırma sistemlərində əlaqə üçün istifadə edilən strukturdur. Yəni, 2 dənə
proqram düşünək, bunlar öz aralarında əlaqə saxlayacaqlarsa, bu əlaqəni müxtəlif
protokollarla, üsullarla saxlaay bilərik. Məzh bu davranışlardan birisi də message queue
strukturudur.
Message queue ilə müstəqil sistemlər arasında data alış-verişi üçün istifadə edilir.
Message queue göndərilən mesajları queue-də/ növbədə/ list-də saxlayır və sonradan bu
mesajların işlənməsinə imkan yaradır. Indi iki proqram arasında bu modellə əlaqə
saxlamaq istəyiriksə, ortaya bir message queue qoyuruq. Proqramın biri bir eventlə digər
proqramı tətikləmək istəyirsə, queue-ə bir mesaj göndərilir. Bu mesaj nəticəsində bu
queue-i təqib edən digər proqram, o mesajı alıb əməliyyatını yerinə yetirir.
Bu tərz davranış ortaya qoyan bir proqram modelinə message queue deyilir. Bu modelin
adı isə message queueing olur.
DEMƏLİ...
Bir queue var dedik, 2 proqram arasında bu queue üzərindən proqramlar arasında əlaqə
yaradırıq. Bu queue-ə mesaj göndərənə Producder ya da Publisher, queue-dəki
mesajları istifadə edənə isə Consumer deyilir.

Tutaq ki, 2 proqramımız var, əgər bu proqramlar arasında əlaqə modeli message queue
olarsa, araya bir queue qoyuruq. Qoyulan queue iki proqram belə bir davranışla
yanaşacaqdır...
Bir A proqramımız publisher olsun, bu proqram etmiş olduğu bir əməliyyat nəticəsində bu əməliyyatın
davamını digər B proqramına buraxmaq istəyirsə, message queue-ə bir mesaj
göndərəcəkdir. Bu mesaj sırası gəldikdə consumer tərəfindən alınacaq və deyəcək ki, bu
əməliyyata görə öz əməliyyatımı görməliyəm.
Message queue-də olan proqramlar bir birndən fərqli və proqramlaşdırma dillərində
yazılmş proqramlar ola bilər.
Bu message queue strukturunda message-nin nə məna verdiyini anlamaq lazımdır.

Burada message odur ki, iki sistem arasında əlaqə üçün istifadə olunan datadır. Yəni
Producer-in Consumer tərəfindən üzərində işləməsini istədiyi datanın məzh özüdür.

Məsələn, bir e-commerce üzərindən nümunə versək, sifarişə aid mesaj olaraq: sifariş
nömrəsi, müştəri məlumatları, product məlumatları və ya ödəmə məlumatları nümunə
verilə bilər.
Həmçinin message queue içərisindəki mesajların consumer tərəfindən sırası ilə işləndiyini
deməliyik. (FİFO məntiqində)

# Message Queue-nin Məqsədi Nədir?
Bəzi hallarda bir birindən fərqli sistemlər arasında funksionallıq nöqteyi-nəzərdən
sinxron xəbərləşmək user təcürbəsi nöqteyi nəzərdən çox da uyğun deyil.
Buna bir misal göstərəcək olsaq, bir e-commerce proqramında ödəmə
əməliyyatında sonra faktura yaratmaq üçün əlaqəli servisin funksiyasını sinxron bir
şəkildə gözləmək və bunu son use-ə əks etdirmək heç də məntiqli bir davranış
olmayacaqdır. Bu tərzdə hallarda sistemlər arasında sinxrondan əlavə asinxron
əlaqə modeli mənimsənilir.
Ödəmə nəticəsində userə sifrişin müvəffəqiyyətlə həyata keçdiyini aid bir nəticə
qaytarılarkən, bir yandan da message queue-a faktura ilə əlaqənən bir mesaj
göndərilməlidir. Ödəməni edərkən təsdiq mesajı gözləmək <strong>sinxron əlaqədir.</strong>

# Sinxron və Asinxron Əlaqə Modelləri
Tutuaq ki, 2 servisimiz var. Bu servislər bir-biri ilə əlaqə saxlayarkən bir response
gözləyirlərsə bu bir asinxron əlaqədir. Asinxron əlaqdə isə response gözlənilməz.

Mail göndərmək, faktura yaratmaq, stok güncəlləmək və.s. kimi zaman gəgrkdirən
əməliyyatların asinxron əlaqə modeli ilə modellənməsi daha idealdır.

# Message Broker Nədir?
Message broker, RabbitMQ kimi texnologiyaların ümumi adıdır.
Içərisində Message Queue-i saxlayan və bu queue üzərindən publisher/producer ilə
consumer arasındakı əlaqəni yaradan sistemdir.
<strong>Bir Message Broker içərisində birdən çox queue ola bilər.</strong>
Təbii ki, burada publisher hansı queue-ə mesaj atırsa, o queue-i təqib edən
consumer öz işinə davam edəcək.
