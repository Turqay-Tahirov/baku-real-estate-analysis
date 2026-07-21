# 🏢 Bakı Daşınmaz Əmlak Bazarının Data Analitikası (Bina.az)

## 🎯 Layihə Haqqında (Project Overview)
Bu layihə, 2026-cı ilin iyul ayında Bina.az platformasından çıxarılmış ~50,000 elandan ibarət real məlumat bazasının analizinə həsr olunub. Layihə sadə bir "hesabat hazırlamaq" məqsədi daşımır; burada tamamilə **Problem Həll Etmə (Problem-Solving) və Biznes Yönümlü** yanaşma tətbiq edilərək, bazardakı süni qiymət manipulyasiyaları, struktur faktorların qiymətə təsiri və investorlar üçün gizli fürsətlər araşdırılıb.

---

## ❓ Layihənin Cavab Tapdığı 5 Kritik Biznes Sualı

<details open>
<summary><b>1. Rieltorlar (Agentliklər) bazarı nə dərəcədə ələ keçirib?</b></summary>
<blockquote>
  <ul>
    <li>Saytdakı elanların neçə faizi maklerlərə (agentliklərə), neçə faizi birbaşa ev sahiblərinə məxsusdur?</li>
    <li>Agentliklər eyni ərazidə qiyməti ev sahibindən nə qədər baha qoyaraq süni qiymət artımı yaradırlar?</li>
  </ul>
</blockquote>
</details>

<details open>
<summary><b>2. Bakının real kvadratmetr bahalığı xəritəsi nə deyir?</b></summary>
<blockquote>
  <ul>
    <li>1 kvadratmetrə görə Bakının ən baha və ən ucuz zonaları (rayon və qəsəbələri) haralardır?</li>
    <li>Evin sahəsi böyüdükcə kvadratmetr qiyməti ucuzlaşır, yoxsa <i>"böyük ev lüksdür"</i> yanaşması ilə daha da bahalaşır?</li>
  </ul>
</blockquote>
</details>

<details open>
<summary><b>3. "Mərtəbə Cəzası" (Floor Penalty) qiyməti neçə faiz aşağı salır?</b></summary>
<blockquote>
  <ul>
    <li>Bakıda alıcılar "rütubətlidir" deyə 1-ci mərtəbəni, "damı axar, lifti xarab olar" deyə sonuncu mərtəbəni (mansardı) almağa çox vaxt tərəddüd edirlər.</li>
    <li>Tələb az olduğu üçün bu mənzillərin real bazar qiyməti orta mərtəbələrdən statistik olaraq neçə faiz ucuzlaşır?</li>
  </ul>
</blockquote>
</details>

<details open>
<summary><b>4. Dəniz kimi datadan "Qızıl Fürsət" (Kələpir) evləri necə tapa bilərik?</b></summary>
<blockquote>
  <ul>
    <li>50,000-dən çox elanın içindən, satıcısının təcili pula ehtiyacı olduğu üçün bazar dəyərindən 20-25% aşağı qiymətə qoyulmuş real "Kələpir" evləri riyazi və statistik alqoritmlə (məsələn, regional median qiymətdən kənara çıxmalarla) necə tutub investora təqdim edə bilərik?</li>
  </ul>
</blockquote>
</details>

<details open>
<summary><b>5. Hansı otaqlı evlər bazarda daha çoxdur və daha tez satıla bilər?</b></summary>
<blockquote>
  <ul>
    <li>Tikinti şirkətləri və investorlar üçün bazarın "qızıl ortasını" tapırıq — Bakıda ən çox təklif olunan və alıcısı dərhal hazır olan optimal mənzil profili (məsələn, 2 otaqlı 60 m², yoxsa 3 otaqlı mənzil) hansıdır?</li>
  </ul>
</blockquote>
</details>
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
* [ ] ⏳ Datanın Toplanması (Rayonlar üzrə CSV faylları)
* [ ] Python ilə Data Təmizləmə və ETL prosesi
* [ ] Kəşfiyyatçı Data Analizi (Python EDA & Qrafiklər)
* [ ] SQL Bazasının Qurulması və Analitik Sorğular
* [ ] Power BI Dashboard Dizaynı
* [ ] Biznes Strategiyasının Hazırlanması və Portfolionun Tamamlanması


---

## 🗄️ Məlumatların Toplanması (Data Scraping)

Layihədə analiz ediləcək daşınmaz əmlak elanları veb-skrapinq vasitəsilə birbaşa onlayn platformadan yığılmışdır. Skrapinq prosesinin stabil olması üçün məlumatlar rayonlar üzrə hissə-hissə toplanır və növbəti mərhələdə vahid bir verilənlər bazasında (master-data) birləşdirilir.

### 🛠️ İstifadə Olunan Alətlər:
* **Web Scraper (Browser Extension):** Elanların avtomatik toplanması, səhifələnmənin (pagination) idarə olunması və datanın CSV formatında ixracı üçün istifadə edilmişdir.

### 📊 Cari Data Toplanma Statusu (Scraping Progress)

Hazırda Bakı şəhəri və ətraf ərazilərin demək olar ki, bütün əsas rayonları üzrə məlumatlar uğurla toplanmışdır. Layihənin bu hissəsi dinamikdir və qalan son bir neçə rayonun yığılması davam edir:

* **Çəkilmiş rayonlar (Hazırdır):** Abşeron, Binəqədi, Nizami, Nəsimi, Pirallahı, Qaradağ, Sabunçu,Xırdalan, Səbail, Suraxanı, Xətai, Xəzər r, Yasamal, Nərimanov r.
* **Yığılan rayonlar (Gözlənilir):** Bütün rayonlar çəkildi.

---

### ⚠️ Kodlaşdırma (Encoding) Probleminin Həlli

Veb-skrapinq zamanı Azərbaycan hərflərinin (ə, ö, ü, ş, ç, ı, ğ) pozularaq sistemə səhv simvollarla (məsələn: `ElmlE™r AkademiyasÄ± m.`, `3 otaqlÄ±` və s.) yazılması problemi aşkarlanmışdır.

Bu problem datanın emalı (ETL) mərhələsində Python ilə oxunarkən **UTF-8 (utf-8-sig)** formatında məcburi kodlaşdırılaraq tamamilə aradan qaldırılacaqdır:

<pre><code># Azərbaycan şriftlərinin düzgün oxunması üçün UTF-8-sig tətbiqi
df = pd.read_csv('raw_data.csv', encoding='utf-8-sig')</code></pre>

---
### 🔄 Növbəti Addım (Data ETL Pipeline):
Bütün rayonların məlumatları tamamlandıqdan sonra, Python (`Pandas` kitabxanası) vasitəsilə bütün datalar tək bir master DataFrame-də birləşdiriləcək və təmizləmə (Data Cleaning) mərhələsinə ötürüləcək.
