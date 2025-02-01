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
consumer arasındakı əlaqəni yaradan sistemdir. <br>
<strong>Bir Message Broker içərisində birdən çox queue ola bilər.</strong> <br>
Təbii ki, burada publisher hansı queue-ə mesaj atırsa, o queue-i təqib edən
consumer öz işinə davam edəcək.

# Message Broker Texnologiyaları Nələrdir?
- RabbitMQ
- Kafka
- ActiveMQ
- ZeroMQ
- NSQ
- İronMQ

# RabbitMQ Nədir?
Open source olan bir message queueing sistemidir. Erland dili ilə yazılmışdır. Cross
platform olduğuna görə fərqli əməliyyat sistemlərində qurula bilər. Zəngin bir
dokumentasiyaya malikdir. Cloud-da xidməti mövcuddur.

# RabbitMQ-ü Niyə İstifadə Emtəliyik?
Yazılmış proqramlarda scalable bir environment yaratmaq istəyiriksə, RabbitMQ
istifadə edilə bilər. Scalabed environment dedikdə, yəni ödəmə etdik, fakturanın
yaradılmasını gözləməkdənsə, bunu fərqli bir servisə alıb asinxron bir əlaqə qura
bilərik. <br>
Proqramlarımızda userlərdən gələn istəklərə anındaca cavab verə bilmiriksə ya da
anlıq olmayan, zaman alan əməliyyatları araya salmalıyıqsa, useri gözlətmək yerinə
bu tərz periodları asinxron bir şəkildə konfiqurasiya edib, proqram intensivliyini
düşürməliyik. <br>
Əks halda user lazımsız bir response time gecikməsinə məruz qalacaqdır və
proqramımız əlehinə bir vəziyyət olacaqdır. <br>
Bu kimi hallarda asinxron periodu kontrol edəcək olan struktur RabbitMQ-dür. <br>
RabbitMQ, response time-ı uzun çəkəcək əməliyyatları proqramdan
müstəqilləşdirəcək/asılılğdan azad edərək buradakı məsuliyyəti fərqli bir proqramın
üzərinə götürməsinə imkan yaradacaq bir mexanizma bizə verir. <br>
Bu mexanizma uzun çəkə biləcək maliyyətli işləri RabbitMQ vasitəsilə, quyruğa
göndərəcək və bu quyruqdakı əməliyyatlar fərqli bir proqram tərəfindən
hazırlanaraq response asinxron bir şəkildə <strong>əsas proqramdan asılı
olmadan/müstəqil əldə ediləcəkdir.</strong> Beləcə əsas/ana proqramdakı intennsivlik
mümkün qədər azaldılmış olacaqdır. <br>
Bu hala abstact bir nümunə verməliyiksə:
Bir web saytın hər hansı bir word faylını PDF formatına dönüşdürmə xidmətini
verəcəyiksə, buradakı əməliyyat intensivliyini web proqramda etməkdən
qaçmalıyıq. <br>
Edilməsi gərəkən RabbitMQ vasitəsilə yaradılan bir quyruğa bütün dəyərlərin
verilməsi və bu zaman daxilində əlaqəli quyruğu dinləyən fərqli bir proqram
<br>
vasitəsilə convert əməliyyatının həyata keçirilməsi gərəkir. Nəticə etibarı ilə əsas
proqramı lazımsız response time-a məruz qalmadan lazımi dönüşdürmə əməliyyatı
müvəffəqiyyətlə həayat keçirilmiş olacaqdır.

# RabbitMQ Necə İşləyir
<img src = "https://github.com/user-attachments/assets/2a83fd9e-7a12-4e03-9438-cd400fb669de"/>
<br>
Şəkildən görüldüyü kimi RabbitMQ fərqli strukturlarla/vasitələrlə bir bütövlük oratay
qoyur.
RabbitMQ, bir message broker olduğu üçün mesajları yayınlayan
publisher/producer və bu mesajları istifadə edən consumer servisləri tərəfindən
ortaq olaraq istifadə edilməkdədir. <br>
<strong>
Struktur olaraq Exchange və Queue strukturları üzərindən funksionallıq göstərə
bilir.Exchange, mesajların necə istifadə ediləcəyinin modelini göstərən/verən
bir strukturdur. Yəni, bir mesaj göndərdikdə hansı quyruğa gedəcək? Necə

isitfadə olunacaq? Və.s. kimi bunların modelləri olacaq. Bu modellər Exchaneg-
lər üzərindən bildiriləcək.
</strong>
<br>
Publisher mesajı publish etdikdən sonra əlaqəli mesajı Exchange qarşılayacaq.
Exchange isə müəyyən route ilə mesajı əlaqəli quyruğa yönləndirəcəkdir.
(Mesajın hansı queue-a gedəcəyi exchange içərisindəki route-dan öyrənilir)
<br>
Burada Publisher və Consumerin hansı platform və hansı dillə yazıldığının heç bir
əhəmiyyəti yoxdur. Bu arxitektura bütöv olaraq proqramlaşdırma dilindən asılı
olmayaraq funksionallıq göstərəcəkdir.
<br>
Bütün bu zaman daxilində RabbitMQ AMPQ (Advanced Message Queuing Protocol)
protokolunu isitfadə edərək faliyyət göstərməkdədir.
Bu model sayəsində RabbitMQ, mesajarın güvənli və məsuldar bir şəkildə istifadə
ediməsini və servislər arasındakı sağlam əlaqənin qurulmasını həyata keçirir.

