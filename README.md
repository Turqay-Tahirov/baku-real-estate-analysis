# 🏢 Bakı Daşınmaz Əmlak Bazarının Data Analitikası (Bina.az)

## 🎯 Layihə Haqqında (Project Overview)
Bu layihə, 2026-cı ilin iyul ayında Bina.az platformasından çıxarılmış ~50,000 elandan ibarət real məlumat bazasının analizinə həsr olunub. Layihə sadə bir "hesabat hazırlamaq" məqsədi daşımır; burada tamamilə **Problem Həll Etmə (Problem-Solving) və Biznes Yönümlü** yanaşma tətbiq edilərək, bazardakı süni qiymət manipulyasiyaları, struktur faktorların qiymətə təsiri və investorlar üçün gizli fürsətlər araşdırılıb.

---

## ❓ Layihənin Cavab Tapdığı 5 Kritik Biznes Sualı

1. **Rieltorlar (Agentliklər) bazarı nə dərəcədə ələ keçirib?**
   * *Sadə dildə:* Saytdakı elanların neçə faizi maklerlərə, neçə faizi ev sahibinə məxsusdur? Agentliklər eyni ərazidə qiyməti ev sahibindən nə qədər baha qoyaraq süni artım yaradırlar?

2. **Bakının real kvadratmetr bahalığı xəritəsi nə deyir?**
   * *Sadə dildə:* 1 kvadratmetrə ($Qiymət / m^2$) görə Bakının ən baha və ən ucuz zonaları haralardır? Evin sahəsi böyüdükcə kvadratmetr ucuzlaşır, yoxsa "böyük ev lüksdür" deyə daha da bahalaşır?

3. **"Mərtəbə Cəzası" qiyməti neçə faiz aşağı salır?**
   * *Sadə dildə:* Bakıda çox adam "rütubətlidir" deyə 1-ci mərtəbəni, "damı axar, lifti xarab olar" deyə sonuncu mərtəbəni (mansardı) almır. Alıcı az olduğu üçün bu mənzillərin qiyməti orta mərtəbələrdən real olaraq neçə faiz ucuzlaşır?

4. **Dəniz kimi datadan "Qızıl Fürsət" (Ucuz) evləri necə tapa bilərik?**
   * *Sadə dildə:* 50 min elanın içindən, satıcısının təcili pula ehtiyacı olduğu üçün bazar qiymətindən 20-25% aşağı qoyulmuş real "Kələpir" evləri riyazi alqoritmlə necə tutub investora təqdim edə bilərik?

5. **Hansı otaqlı evlər bazarda daha çoxdur və daha tez satıla bilər?**
   * *Sadə dildə:* Tikinti şirkətləri və investorlar üçün bazarın "qızıl ortasını" tapırıq – Bakıda ən çox təklif olunan və alıcısı hazır olan mənzil profili (məsələn, 2 otaqlı 60 $m^2$, yoxsa 3 otaqlı) hansıdır?

---

## 🛠️ Texniki İş Axımı və Problemlərin Həlli (Technical Workflow)

### 1. Data Təmizləmə və Yeni Dəyişənlərin Yaradılması (Python)
* **Problem:** Web-dən gələn xam data tamamilə çirkli mətn (string) formatında idi (məsələn: "915 000 AZN", "190 m²"). Ünvanlar və mərtəbələr qarışıq yazılmışdı.
* **Həll (Regex):** Müntəzəm ifadələrdən (Regex) istifadə edərək simvolları təmizlədim və datanı riyazi formatlara (`int`/`float`) gətirdim. Qarışıq ünvanlardan təmiz `Rayon` və `Metro` sütunları çıxardım.
* **Mərtəbə Parçalanması:** "4/10 mərtəbə" kimi bitişik gələn strukturu bölərək `evin_mertebesi` və `binanin_mertebesi` adlı iki ayrı metrika yaratdım.
* **Anomaliyalar və Təkrarlanmalar:** Süni qiymət yazılmış saxta elanları statistik üsullarla təmizlədim və agentliklərin təkrar paylaşdığı dublikat sətirləri sildim.

### 2. Verilənlər Bazası və Analitik Sorğular (SQL)
* Təmizlənmiş datanı yerli verilənlər bazasına köçürərək, biznes suallarına sürətli və dəqiq cavab tapmaq üçün mürəkkəb SQL pəncərə funksiyaları (Window Functions) və analitik sorğular yazdım.

### 3. İnteraktiv İdarəetmə Paneli (Power BI)
* Rəhbərlik və investorlar üçün minimalist (tünd rejimdə) professional dashboard dizayn etdim. Bura əsas daşınmaz əmlak KPI-ları və kliklədikdə birbaşa saytdakı ucuz elana yönləndirən dinamik **"İnvestor Matrisi"** əlavə etdim.

---

## 🚧 Cari Status: [İcra Olunur]
* [x] Biznesin Anlanılması və Hipotezlərin Qurulması
* [x] Datanın Toplanması (Rayonlar üzrə CSV faylları)
* [ ] Python ilə Data Təmizləmə və ETL prosesi
* [ ] Kəşfiyyatçı Data Analizi (Python EDA & Qrafiklər)
* [ ] SQL Bazasının Qurulması və Analitik Sorğular
* [ ] Power BI Dashboard Dizaynı
* [ ] Biznes Strategiyasının Hazırlanması və Portfolionun Tamamlanması
