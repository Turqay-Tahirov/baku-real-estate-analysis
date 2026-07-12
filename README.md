# 🏢 Bakı Daşınmaz Əmlak Bazarının Data Analitikası (Bina.az)

## 🎯 Layihə Haqqında (Project Overview)
Bu layihə, 2026-cı ilin iyul ayında Bina.az platformasından çıxarılmış ~50,000 elandan ibarət real məlumat bazasının analizinə həsr olunub. Layihə sadə bir "hesabat hazırlamaq" məqsədi daşımır; burada tamamilə **Problem Həll Etmə (Problem-Solving) və Biznes Yönümlü** yanaşma tətbiq edilərək, bazardakı süni qiymət manipulyasiyaları, struktur faktorların qiymətə təsiri və investorlar üçün gizli fürsətlər araşdırılıb.

---

## ❓ Layihənin Cavab Tapdığı 5 Kritik Biznes Sualı

1. **Bazar Manipulyasiyası və İnhisarçılıq:** Elanların nə qədəri Agentliklərin (rieltorların), nə qədəri fərdi şəxslərin (Sahibinin) əlindədir? Eyni ərazidə agentliklər qiyməti orta hesabla neçə faiz süni şəkildə şişirdirlər?
2. **Coğrafi Qiymət Dürüstlüyü:** Bakının 1 kvadratmetrə ($Qiymət / m^2$) görə real rəqəmsal qiymət xəritəsi nə deyir? Şəhər mərkəzindən uzaqlaşdıqca kvadratmetr səmərəliliyi necə dəyişir?
3. **Mərtəbə Cəzası:** Mənzilin yerləşdiyi mərtəbə (məsələn: 1-ci mərtəbə və ya sonuncu mərtəbə/mansard) mülkün real bazar dəyərindən neçə faiz "kəsir"?
4. **Gizli Fürsətlərin Tapılması:** 50 minlik data dənizindən riyazi metodlarla (IQR/Z-score) bazar qiymətindən 20-25% aşağı qoyulmuş real "Təcili Elanları" avtomatik necə süzə bilərik?
5. **Sahə Elastikliyi:** Mənzilin ümumi sahəsi ($m^2$) böyüdükcə kvadratmetrin qiyməti ucuzlaşır, yoxsa "böyük ev lüksdür" məntiqi ilə daha da bahalaşır?

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
