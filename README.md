ç# trex_research
.NET Backend Geliştirme - Temel Bilgi ve Kavramlar Araştırma Raporu

# .NET Backend Geliştirme – Temel Bilgi ve Kavramlar

## 📌 İçindekiler
1. [Modern Yazılım Geliştirme Pratikleri](#1-modern-yazılım-geliştirme-pratikleri)
2. [.NET Ekosistemi](#2-net-ekosistemi)
3. [Backend Geliştirme Temelleri](#3-backend-geliştirme-temelleri)
4. [ASP.NET](#4-aspnet)
5. [Veritabanı ve ORM](#5-veritabanı-ve-orm)
6. [Güvenlik ve Performans](#6-güvenlik-ve-performans)
7. [Logging ve Hata Yönetimi](#7-logging-ve-hata-yönetimi)
8. [Yazılım Geliştirme Prensipleri](#8-yazılım-geliştirme-prensipleri)

## 1. Modern Yazılım Geliştirme Pratikleri

## Git ve GitHub

### Git Nedir?
- Yazılım projelerinde kullanılan bir **versiyon kontrol sistemidir**.  
- Projenin farklı sürümlerini kaydeder ve yönetir.  
- Yapılan değişiklikleri adım adım takip etmemizi sağlar.  
- Hatalı bir işlemde eski sürümlere dönmeyi kolaylaştırır.  
- Aynı proje üzerinde birden fazla kişinin eş zamanlı çalışmasına imkan tanır.  

Kısaca benim için **Git**, projeyi yerel bilgisayarımda güvenle yönetmemi sağlayan bir araçtır.  

---

### GitHub Nedir?
- Git ile yönetilen projelerin internet üzerinde saklandığı ve paylaşıldığı bir **platformdur**.  
- Git projeleri için bir **bulut deposu** gibi çalışır.  
- Kendi projelerimizi yedeklememizi ve istediğimiz yerden erişmemizi sağlar.  
- Ekip çalışmasını kolaylaştırır, farklı kişilerin katkı yapmasına olanak tanır.  
- Açık kaynak projelere katılım için en çok kullanılan platformlardan biridir.  

**GitHub’u**, projelerimi paylaşmak ve başkalarıyla iş birliği yapmak için en çok kullandığım araç olarak görebilirim.  

---
## Temel Git Komutları

## `git init`
- Bir klasörü Git deposuna dönüştürmek için kullanılır.  
- Projeyi ilk kez Git ile takip etmeye başlamanın yoludur.  

Benim için bu komut, **sıfırdan bir proje başlatırken ilk adımı atmak** gibidir.  



## `git clone`
- Var olan bir projeyi GitHub veya başka bir uzak depodan bilgisayara kopyalamayı sağlar.  
- Özellikle ekip çalışmalarında ortak projeyi kendi bilgisayarımıza indirmek için kullanılır.  
- Örneğin:  
-  `git clone repo-adresi` → ile bir arkadaşımın oluşturduğu depoyu kolayca bilgisayarıma çekebilirim.



## `git add`

Dosyalarda yapılan değişiklikleri **staging area (hazırlık alanı)**’na ekler.

- `git add dosya.txt` → belirli dosyayı ekler.  
- `git add .` → tüm değişiklikleri ekler.  

Bu aşama, commit öncesinde hangi değişikliklerin kaydedileceğini seçmemi sağlar.


#### → Staging Area Nedir?

Commit edilmeden önce dosyaların toplandığı **geçici alandır**.  

- Sadece staging area’ya eklenen dosyalar commit edilir.  
- Örneğin, 3 dosyadan sadece 2’sini `git add` ile staging area’ya alırsam commit sırasında yalnızca bu 2 dosya kaydedilir.  

 **Yani staging area, commit öncesi bir kontrol listesi gibidir.**



## `git commit`
Staging area’daki değişiklikleri **kalıcı olarak kaydeder**.  

- `git commit -m "mesaj"` → yapılan işlemi açıklayan bir mesaj yazılır.  

 Commit mesajları düzenli tutulduğunda, proje geçmişi çok daha anlaşılır olur.



## `git push`
Yerelde yapılan commit’leri **uzak depoya** (örneğin GitHub’a) gönderir.  

- Ekip çalışmasında kodun paylaşılmasını sağlar.  
- Push = *“Benim yaptıklarımı herkes görsün”* demektir.  



## `git pull`
Uzak depoda yapılan değişiklikleri bilgisayara indirir.  

- `git pull` ile başkalarının yaptığı güncellemeleri kendi koduma eklemiş olurum.  
- Projede güncel kalmak için en sık kullanılan komutlardan biridir.  



## `git branch`
Yeni bir dal (**branch**) oluşturur.  

- Farklı bir özellik üzerinde çalışırken ana projeyi bozmamak için kullanılır.  
- Örneğin: `git branch deneme` → “deneme” isimli yeni bir dal açar.  



## `git merge`
Bir branch’te yapılan değişiklikleri başka bir branch ile birleştirir.  

- Özellikle feature branch’ler tamamlandığında **main branch** ile merge edilir.  
- Bence bu, farklı yolların sonunda birleşim noktası gibidir.  

#### → Feature branch = yeni bir özellik geliştirme dalı.
Ana kodu bozmadan, güvenli şekilde geliştirme yapmayı sağlar.

#### Küçük Terminal Çıktısı Örneği

```bash
$ git init
Initialized empty Git repository

$ git add .

$ git commit -m "ilk commit"
[main] ilk commit
 1 file changed
```
---

## Merge Conflict Nedir, Nasıl Çözülür?

## Merge Conflict Nedir?
İki farklı dalda (**branch**) aynı dosyanın aynı satırlarında değişiklik yapılırsa **merge conflict** oluşur.  

- Git hangi değişikliğin doğru olduğunu kendi başına bilemez.  
- Bu yüzden bize sorar, biz karar verip düzenleriz.  

 **Basit Örnek:**  
- `main` branch’inde **index.html** dosyasına: `Merhaba Dünya` yazdım.  
- `login-feature` branch’inde aynı satırı: `Hello World` yaptım.  
- İkisini birleştirmeye çalıştığımda Git hangisini seçeceğini bilemez → merge conflict olur.  

---

## Merge Conflict Nasıl Çözülür?
Çakışan dosyayı açtığımda Git şu şekilde işaretler koyar:  

```bash
<<<<<<< HEAD
Merhaba Dünya
=======
Hello World
>>>>>>> login-feature
```
- Hangi kısmı tutacağıma **ben karar veririm**.  
- İster birini silerim, ister ikisini birleştiririm.  
- Düzelttikten sonra dosyayı kaydederim.  

Sonrasında Git’e bildiririm:  

```bash
git add index.html
git commit -m "Merge conflict çözüldü"
```

→ Özetle:
Merge conflict, Git’in karar veremediği bir çakışmadır.
Çözmek için dosyayı açıp hangisinin kalacağına biz karar veririz.

---
# CI/CD Nedir?

## CI (Continuous Integration – Sürekli Entegrasyon)
- Geliştiricilerin yaptığı kod değişikliklerinin **ortak depoya eklenmesidir**.  
- Kod her gönderildiğinde **otomatik testler** çalışır.  
- **Amaç:** Hataları erkenden görmek.  

---

## CD (Continuous Delivery / Deployment – Sürekli Teslim / Dağıtım)
- Testlerden geçen kodun **yayınlanmaya hazır hale gelmesidir**.  
- Gerekirse otomatik olarak **sunucuya aktarılır**.  
- **Amaç:** Kod her an **güncel ve çalışır** olsun.  

---

## Azure DevOps
- Microsoft’un geliştirdiği bir **CI/CD ve proje yönetim aracı**dır.  
- Kodlarımızı **test etmek, derlemek ve dağıtmak** için kullanılır.  
- Büyük projelerde **ekip çalışmasını kolaylaştırır**.  
#### Azure DevOps Pipeline Örneği

```yaml
trigger:
- main

pool:
  vmImage: 'ubuntu-latest'

steps:
- task: DotNetCoreCLI@2
  inputs:
    command: 'build'
    projects: '**/*.csproj'

- task: DotNetCoreCLI@2
  inputs:
    command: 'test'
    projects: '**/*Tests.csproj'
```
#### Açıklama

- `main` branch’e kod gönderildiğinde **pipeline otomatik tetiklenir**.  
- **Build adımı:** Projedeki tüm `.csproj` dosyaları derlenir.  
- **Test adımı:** Test projeleri (`*Tests.csproj`) çalıştırılır.  


## GitHub Actions

- GitHub’ın içinde gelen **otomatik işlem (automation) sistemidir**.  
- Kod her **push edildiğinde**:  
  - **Test** edebilir  
  - **Build** edebilir  
- **Kullanımı kolaydır** ve **hızlıdır**.
  
#### Örnek GitHub Actions Workflow

```yaml
name: .NET CI

on:
  push:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    
    - uses: actions/setup-dotnet@v3
      with:
        dotnet-version: '8.0.x'
    
    - run: dotnet build --configuration Release
    - run: dotnet test --no-build --verbosity normal
```
#### Açıklama

- **Trigger:** `main` branch’e push olduğunda çalışır.
- **Checkout:** Repo içeriği runner’a indirilir.
- **Setup .NET:** .NET 8.0 SDK yüklenir.
- **Build:** Proje Release modunda derlenir.
- **Test:** Testler çalıştırılır, ayrıntılı çıktı alınır.
  


## CI/CD – Azure DevOps ve GitHub Actions Karşılaştırması

| **Özellik**       | **Azure DevOps**                                      | **GitHub Actions**                                |
|--------------------|-------------------------------------------------------|--------------------------------------------------|
| **Kullanım Alanı** | Daha çok **büyük ekipler** ve **kurumsal projeler**   | Daha çok **bireysel** ve **küçük/orta projeler** |
| **Kurulum**        | İlk kurulum biraz daha **detaylıdır**                 | GitHub’da hazır, **çok hızlı başlar**            |
| **Esneklik**       | Çok kapsamlı ayarlar, ortamlar, onay adımları vardır  | Daha **basit** ve **hızlı** çalışır             |
| **Entegrasyon**    | **Azure ekosistemi** (Boards, Repos, vb.) ile uyumlu | Doğrudan **GitHub reposu** ile uyumlu           |
| **Avantaj**        | Profesyonel projelerde **detaylı kontrol** sağlar     | **Öğrenmesi ve kullanması daha kolay**           |

## Özet

- **CI** = Kod değişince **otomatik test**.  
- **CD** = Kodun **otomatik yayına alınması**.  
- **Azure DevOps** = Daha **kurumsal ve detaylı**.  
- **GitHub Actions** = Daha **basit ve hızlı**.

---

  ## Software Development Life Cycle (SDLC)

## SDLC Nedir?
- Yazılım geliştirme sürecinin adımlarını tanımlayan yöntemdir.  
- **Amaç:** Yazılımı planlı, düzenli ve hatasız şekilde geliştirmek.  


### SDLC Aşamaları

#### 1. Planlama
- Projenin amacı, kapsamı ve gereksinimleri belirlenir.  
- Zaman, maliyet ve ekip planı yapılır.  

#### 2. Analiz
- Kullanıcı ihtiyaçları toplanır.  
- Teknik gereksinimler çıkarılır.  

#### 3. Geliştirme (Coding)
- Yazılımcılar kodlama yapar.  
- Gereksinimlere uygun yazılım üretilir.  

#### 4. Test
- Yazılımda hatalar aranır ve düzeltilir.  
- Uygulamanın doğru çalışıp çalışmadığı kontrol edilir.  

#### 5. Dağıtım (Deployment)
- Yazılım kullanıcılara sunulur.  
- Ürün gerçek ortamda çalışmaya başlar.  

#### 6. Bakım (Maintenance)
- Hatalar düzeltilir, güncellemeler yapılır.  
- Yazılım yeni ihtiyaçlara göre geliştirilir.  



## Agile / Scrum / Kanban Metodolojileri

#### Agile
- Kısa döngülerle (**sprint**) hızlı geri bildirim alınarak geliştirme yapılır.  

#### Scrum
- Agile’ın en çok kullanılan çerçevesidir.  
- Roller: **Scrum Master, Product Owner, Team**  
- Günlük toplantılar (**daily scrum**) ve sprintlerle ilerler.  

#### Kanban
- İşlerin bir panoda kartlar halinde sıralanarak ilerlediği yöntemdir.  
- “**Yapılacaklar → Devam edenler → Tamamlananlar**” şeklinde görselleştirilir.  



## Yazılımcının Süreçteki Yeri
- **Planlama & Analiz:** Gereksinimleri anlamak için katkı sağlar.  
- **Geliştirme:** Kod yazar, veritabanı ve iş mantığını kurar.  
- **Test:** Hataları bulup düzeltir.  
- **Bakım:** Yazılımın sorunsuz çalışmaya devam etmesini sağlar.  

---

## 2. .NET Ekosistemi

## .NET Nedir?

## Tarihçesi
- **.NET**, Microsoft tarafından 2000’li yılların başında geliştirilmeye başlanmıştır.  
- İlk sürümü **2002’de** çıktı.  
- Başlangıçta sadece **Windows** için vardı, daha sonra **.NET Core** ile Linux ve macOS desteği geldi.  
- Günümüzde **.NET 5, .NET 6, .NET 7, .NET 8** sürümleriyle devam ediyor ve artık **platformdan bağımsız** çalışabiliyor.  



## Amacı
- Yazılımcıların farklı platformlarda (**Windows, web, mobil, bulut**) uygulama geliştirmesini kolaylaştırmak.  
- Tek bir çatı altında birden fazla programlama dilini desteklemek (**C#, F#, VB.NET**).  
- Hızlı, güvenli ve modern uygulamalar geliştirmeye imkan vermek.  



## Neden Kullanılır?
- **Çok platformlu:** Windows, Linux, macOS üzerinde çalışır.  
- **Geniş ekosistem:** Masaüstü, web, mobil, oyun (**Unity**), bulut uygulamaları geliştirilebilir.  
- **C# dili:** Öğrenmesi kolay, güçlü ve yaygın bir dildir.  
- **Performans:** Modern sürümlerde oldukça hızlıdır.  
- **Topluluk ve destek:** Microsoft ve geniş bir topluluk tarafından sürekli geliştirilir.  


 **Kısaca:**  
.NET, yazılım geliştirmeyi kolaylaştıran ve farklı ortamlarda kullanılabilen **güçlü bir platformdur**.  


## .NET Framework, .NET Core ve .NET 7/8+ Farkları

## .NET Framework
- **2002’de** çıktı, Microsoft tarafından geliştirildi.  
- Sadece **Windows** üzerinde çalışır.  
- **WinForms, WPF** gibi masaüstü uygulamaları için kullanılır.  
- Artık yeni özellikler eklenmiyor, sadece bakım yapılıyor.  


## .NET Core
- **2016’da** çıktı.  
- **Cross-platform** (Windows, Linux, macOS) desteği vardır.  
- **Açık kaynak** olarak geliştirildi.  
- Daha hızlı, hafif ve modern projeler için uygundur.  



## .NET 5/6/7/8+ (Güncel .NET)
- .NET Framework ve .NET Core birleşerek **tek platform** oldu.  
- Artık sadece **“.NET”** ismiyle devam ediyor.  
- **.NET 5 → 2020**, **.NET 6 → 2021 (LTS)**, **.NET 7 → 2022**, **.NET 8 → 2023 (LTS)**.  
- Hem Framework’ün gücünü hem Core’un hızını birleştiriyor.  
- Geniş destek alanları:  
  - Web (**ASP.NET**)  
  - Masaüstü (**WinForms, WPF**)  
  - Mobil (**Xamarin, MAUI**)  
  - Oyun (**Unity**)  
  - Bulut uygulamaları  



## Kıyaslama Tablosu

| **Özellik**       | **.NET Framework**        | **.NET Core**                   | **.NET 7/8+ (Güncel)**        |
|--------------------|---------------------------|----------------------------------|--------------------------------|
| **Çıkış Yılı**     | 2002                      | 2016                             | 2020 (5), 2021–2023 (6/7/8)   |
| **Çalıştığı Sistem** | Sadece Windows            | Windows, Linux, macOS            | Tüm platformlar                |
| **Açık Kaynak**    | Hayır                     | Evet                             | Evet                           |
| **Performans**     | Görece yavaş              | Daha hızlı, hafif                | En hızlı ve en güncel          |
| **Durum**          | Yeni geliştirme yok       | Destekleniyor                    | Gelecek bu platformda          |



 **Kısaca:**  
- **.NET Framework** → Eski, sadece Windows için.  
- **.NET Core** → Modern, açık kaynak ve platform bağımsız.  
- **.NET 7/8+** → Gelecek, hepsini birleştiren tek ve güncel .NET.  


## .NET Platformlar Arası Çalışabilir mi?

## .NET Framework
- Sadece **Windows** işletim sisteminde çalışır.  
- **Linux** ve **macOS** desteği yoktur.  


## .NET Core
- **Windows, Linux ve macOS** üzerinde çalışabilir.  
- Bu sayede aynı kod farklı sistemlerde kullanılabilir.  



## .NET 5/6/7/8+
- **Platformdan bağımsızdır**.  
- Tek bir .NET çatısı altında hem **Windows**, hem **Linux** hem de **macOS**’ta çalışır.  
- Ayrıca **mobil (Android, iOS)** ve **bulut uygulamaları** için de destek sunar.  



 **Özet:**  
Eski **.NET Framework** sadece Windows’a özel iken, **.NET Core** ile başlayan süreçte **.NET 7/8+** artık tamamen **cross-platform (çoklu platform)** hale gelmiştir.  

## Senkron ve Asenkron Programlama

## Senkron Programlama
- İşlemler **sıra ile** yapılır.  
- Bir işlem bitmeden diğeri başlamaz.  
- Basit projelerde uygundur fakat uzun süren işlemlerde programın **kilitlenmesine** neden olabilir.  



## Asenkron Programlama
- İşlemler aynı anda yürüyormuş gibi çalışır.  
- Uzun süren işlemler (**dosya okuma, veritabanı sorgusu, API çağrısı**) programı bekletmez.  
- Kullanıcı arayüzü **donmaz**, program daha **hızlı** ve **akıcı** çalışır.  



## Temel Kavramlar
- **async** → Bir metodun **asenkron** çalışacağını belirtir.  
- **await** → Asenkron işlemin bitmesini bekler ama programı **kilitlemez**.  
- **Task** → Bir işi temsil eden nesnedir. Asenkron metotlar genelde **Task** döner.  
- **ConfigureAwait(false)** → UI (arayüz) uygulamalarında, işlemin bitince aynı iş parçacığına dönüp dönmeyeceğini kontrol eder. Performans için kullanılır.  

##  Örnek: Asenkron Metot Kullanımı

```csharp
public async Task GetDataAsync()
{
    var data = await httpClient.GetStringAsync("https://example.com");
    Console.WriteLine(data);
}
```
- Burada **GetDataAsync** metodu veri indirirken programı kilitlemez.
- **await** ifadesi sayesinde veri indirilirken uygulama akışı donmaz.
- Kullanıcı arayüzü akıcı kalır, başka işlemler devam edebilir.

### Arrow Function (=>) C#’ta

- **Lambda ifadesi** olarak da bilinir.  
- Kısa ve okunabilir fonksiyon yazmak için kullanılır.  

---

##  Örnekler

### Normal yöntem
```csharp
int Square(int x)
{
    return x * x;
}
```
### Arrow function ile
```csharp
int Square(int x) => x * x;
```
### List filtreleme örneği
```csharp
var numbers = new List<int> {1, 2, 3, 4, 5};
var even = numbers.Where(n => n % 2 == 0);
````
- => ifadesi sayesinde tek satırda fonksiyonlar tanımlanabilir.
- Özellikle LINQ sorgularında çok sık kullanılır.

### Özet:

- Senkron = sırayla, bekletir.
- Asenkron = aynı anda, bekletmez.
- async/await, Task gibi yapılar asenkron programlamanın temelidir.
- Arrow function (=>) C#’ta kısa ve pratik kod yazmayı sağlar.


## Senkron ve Asenkron Programlama

## 1. Temel Farklar

| **Özellik**        | **Senkron Programlama**                       | **Asenkron Programlama**                          |
|---------------------|-----------------------------------------------|--------------------------------------------------|
| **Çalışma Şekli**   | İşlemler **sırayla** yapılır.                 | İşlemler **aynı anda yürüyormuş gibi** çalışır.  |
| **Bekleme**         | Bir işlem bitmeden diğeri başlamaz.           | Uzun süren işlem beklerken diğerleri devam eder. |
| **Kullanıcı Deneyimi** | Uzun işlemlerde program **donmuş gibi** olur. | Kullanıcı arayüzü **akıcı** kalır.               |
| **Performans**      | Basit ama **yavaş** olabilir.                 | Daha **hızlı** ve **verimli** çalışır.           |
| **Kullanım Alanı**  | Küçük ve kısa işlemler.                       | Dosya okuma, API çağrısı, veritabanı sorgusu gibi uzun işlemler. |

##  dotnet --info Örneği

 **Terminal çıktısı:**

```bash
$ dotnet --info
.NET SDK:
 Version:   8.0.100
 Commit:    abc123

Runtime Environment:
 OS Name:     Windows
 OS Version:  10.0.19045
 RID:         win10-x64

Host:
 Version:    8.0.0
 Architecture: x64
```
##  Yorum

- **SDK Version** → Yüklü .NET sürümü (**8.0.100**)  
- **OS Name/Version** → İşletim sistemi bilgisi (**Windows 10**)  
- **Architecture** → 64-bit çalıştığını gösterir  

 → Bu komut, hangi **.NET sürümüyle** geliştirme yaptığımızı öğrenmek için kullanılır.  

 ## Senkron / Asenkron Senaryo

## Senkron Senaryo
- Bir kafede kahve almak istiyorsun.  
- Kasaya gidiyorsun, sipariş veriyorsun.  
- Kasiyer hem kahveyi hazırlıyor hem de parayı alıyor.  
- Kahve hazır olmadan sıradaki müşteriyi almıyor.  
- Yani herkes **tek tek beklemek zorunda**.  

➡ Bu, **senkron programlama** gibidir: Bir işlem bitmeden diğeri başlamaz.  


## Asenkron Senaryo
- Aynı kafede başka bir durum düşün:  
- Kasada siparişini veriyorsun, ödemeyi yapıyorsun.  
- Kasiyer sana bir fiş veriyor ve sen kenarda beklerken başka müşterilere hizmet ediyor.  
- Barista kahveni hazırlıyor, hazır olunca adını sesleniyor ve alıyorsun.  
- Böylece hem sen beklerken boş durmuyorsun hem de kasada işler tıkanmıyor.  

➡ Bu da **asenkron programlama** gibidir: İşler aynı anda yürüyormuş gibi devam eder.  



##  Yazılım Açısından
- **Senkron →** Program bir işi yaparken diğerini **bekletir**.  
- **Asenkron →** Uzun süren iş arka planda devam ederken program **başka işleri de yapar**.

  ## C# Senkron Örnek

```csharp
// Senkron örnek
using System;
using System.Threading;

class Program
{
    static void Main()
    {
        Console.WriteLine("Dosya indiriliyor...");
        DownloadFile(); // Bu bitmeden aşağıya geçmez
        Console.WriteLine("İndirme tamamlandı.");
        Console.WriteLine("Program bitti.");
    }

    static void DownloadFile()
    {
        // 3 saniye dosya indiriyormuş gibi bekletelim
        Thread.Sleep(3000);
    }
}
```
 ➡ Burada Thread.Sleep dosya indiriyormuş gibi davranıyor.
Kod, indirme bitene kadar bekliyor.
Başka iş yapılmıyor, program bloklanıyor.

## C# Asenkron Örnek

```csharp
// Asenkron örnek
using System;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        Console.WriteLine("Dosya indiriliyor...");
        var task = DownloadFileAsync(); // İndirme başladı ama bekletmiyor
        Console.WriteLine("Başka işler yapılabiliyor...");
        
        await task; // İndirme bitince devam eder
        Console.WriteLine("İndirme tamamlandı.");
        Console.WriteLine("Program bitti.");
    }

    static async Task DownloadFileAsync()
    {
        // 3 saniye dosya indiriyormuş gibi bekletelim
        await Task.Delay(3000);
    }
}
```
➡ Burada Task.Delay kullanıldı.

İndirme devam ederken program başka iş yapabiliyor.
Sonunda await ile indirme tamamlanıyor.
#### Özet
**Senkron:** Her şey sırayla → İndirme bitmeden başka iş olmaz.
**Asenkron:** İşler aynı anda yürüyormuş gibi → İndirme devam ederken başka işler yapılabilir.


## 3. Backend Geliştirme Temelleri

##  Backend Nedir?
- **Backend**, bir uygulamanın **arka planda çalışan kısmıdır**.  
- Kullanıcıların görmediği ama uygulamanın **asıl işlerini yapan taraftır**.  
- **Veritabanı işlemleri**, **kimlik doğrulama**, **iş mantığı (business logic)** burada gerçekleşir.  

 **Örnek:** Bir e-ticaret sitesinde ürün arama, sipariş oluşturma, ödeme alma işlemleri **backend** tarafından yapılır.  



## Frontend Nedir?
- **Frontend**, bir uygulamanın **kullanıcının gördüğü ve etkileşim kurduğu kısmıdır**.  
- Kullanıcı arayüzü (**UI**) tasarımı, butonlar, formlar, görseller bu tarafta bulunur.  
- **HTML, CSS, JavaScript** gibi teknolojilerle geliştirilir.  

 **Örnek:** E-ticaret sitesindeki ürün listesi, alışveriş sepeti ekranı, ödeme formu **frontend** kısmıdır.  


## Backend ve Frontend Farkları

| **Özellik**   | **Frontend (Kullanıcı Yüzü)**        | **Backend (Sunucu Tarafı)**          |
|---------------|---------------------------------------|---------------------------------------|
| **Görünürlük** | Kullanıcı tarafından görülür          | Kullanıcı görmez                      |
| **Teknolojiler** | HTML, CSS, JS, React, Angular        | C#, Java, Python, SQL                 |
| **Görev**     | Görselliği ve etkileşimi sağlar       | İş mantığı ve veri yönetimi           |
| **Örnek**     | Ürün kartı, buton, form               | Sepet hesaplama, ödeme işleme         |
| **Çalışma Yeri** | Tarayıcı / mobil uygulama            | Sunucu / veritabanı                   |



##  Basit Örnek Senaryo
- Bir kullanıcı web sitesinde **“Giriş Yap”** butonuna tıklar.  
- **Frontend:** Butona basıldığında form verilerini (**e-posta + şifre**) toplar.  
- **Backend:** Gelen verileri kontrol eder, doğruysa kullanıcıyı veritabanından doğrular ve giriş yapmasını sağlar.  



## Web Sunucusu ve API
###  Web Sunucusu Nedir?

**Tanım:**  
Web sunucusu, internet üzerinden gelen istekleri (**HTTP/HTTPS**) karşılayan ve istemcilere (tarayıcı, mobil uygulama vb.) cevap dönen bir yazılımdır.  

### Görevleri
- İstemciden gelen isteği alır (örn: `/index.html`).  
- İlgili içeriği bulur veya **backend**’e yönlendirir.  
- Cevabı istemciye geri gönderir.  

### Örnek Web Sunucuları
- **IIS (Internet Information Services):** Microsoft’un web sunucusu  
- **Apache HTTP Server:** En çok kullanılan açık kaynak sunucu  
- **Nginx:** Hafif ve performanslı sunucu  
- **Kestrel:** .NET Core projelerinde varsayılan sunucu  

 **Basitçe:** Web sunucusu, **istemci (frontend)** ile **uygulama (backend)** arasındaki **köprüdür**.  


###  API Nedir?

**Tanım:**  
**API (Application Programming Interface)**, yazılımların birbirleriyle iletişim kurmasını sağlayan **arayüzdür**.  

### Görevleri
- Bir uygulamanın sunduğu verileri veya işlevleri dış dünyaya açar.  
- İstemciler, API üzerinden bu verilere erişebilir veya işlem yapabilir.  

#### Örnek
- **Hava durumu API’si:** Kullanıcıya anlık hava bilgisi döner.  
- **Banka API’si:** Para transferi veya bakiye sorgulama yapılır.  

 **Kısacası:** API, **“uygulamalar arası köprü”** gibidir.  


##  API Türleri

### 1. REST (Representational State Transfer)
- **HTTP protokolü** kullanır.  
- Kaynaklara (`/users`, `/products`, `/orders`) URL üzerinden erişilir.  
- **JSON** veya **XML** ile veri taşır (**JSON daha yaygın**).  

📌 **Örnek:**  
```http
GET /users/1    → id=1 kullanıcısını getir
POST /users     → yeni kullanıcı ekle
  ````
### 2. SOAP (Simple Object Access Protocol)
- Daha **eski** ve **ağır** bir protokoldür.  
- **XML tabanlıdır.**  
- Daha çok **banka, sigorta** gibi güvenlik gerektiren sistemlerde tercih edilir.  
- Katı kurallara ve standartlara sahiptir.  


### 3. GraphQL
- **Facebook** tarafından geliştirilmiştir.  
- İstemci, yalnızca **ihtiyacı olan veriyi** isteyebilir.  
- Tek bir endpoint üzerinden çalışır (**/graphql**).  
- **JSON** ile veri döner.  

####  Örnek Sorgu:
```graphql
{
  user(id: 1) {
    name
    email
  }
}
```
➝ Sadece name ve email alanlarını döndürür.

###  Özet Tablo: REST vs SOAP vs GraphQL

| **Özellik**       | **REST**                    | **SOAP**                      | **GraphQL**                           |
|--------------------|-----------------------------|--------------------------------|----------------------------------------|
| **Veri Formatı**   | JSON / XML                  | XML                            | JSON                                   |
| **Hız**            | Hızlı ve hafif              | Yavaş (ağır XML)               | Daha hızlı, esnek                      |
| **Güvenlik**       | Orta (**HTTPS**)            | Yüksek (**WS-Security**)       | Orta (**JWT, HTTPS**)                  |
| **Kullanım Alanı** | Modern **web/mobil**        | **Banka, sigorta**             | **Büyük veri**, frontend odaklı        |
| **Endpoint Yapısı**| Çoklu (`/users`, `/products`)| Tek tip ama SOAP action        | Tek endpoint (`/graphql`)              |


## HTTP ve HTTP Metodları

### HTTP Nedir?

**HTTP (HyperText Transfer Protocol)**, web üzerindeki veri iletişimini sağlayan bir protokoldür.  
- **Tarayıcı** ile **sunucu** arasında **istek–cevap (request–response)** mantığıyla çalışır.  
- Örneğin, bir web sitesine girdiğimizde tarayıcı sunucuya *“sayfayı gönder”* der, sunucu da cevabı yollar.  


### HTTP Metodları

| **Metod** | **Açıklama**                  | **Basit Örnek**                                      |
|-----------|--------------------------------|------------------------------------------------------|
| **GET**   | Sunucudan veri alma           | Bir e-ticaret sitesinde **ürün listesini çekmek**    |
| **POST**  | Sunucuya yeni veri ekleme     | Kullanıcının **kayıt formu göndermesi**              |
| **PUT**   | Var olan veriyi güncelleme    | Kullanıcı **profil bilgilerinin değiştirilmesi**     |
| **DELETE**| Veriyi silme                  | Bir ürünün **sepetten çıkarılması**                  |

#### HTTP Metodları ve Örnekleri  

##### 1. GET – Veri çekmek  
**Amaç:** Sunucudan bilgi almak.  

 **Örnek Senaryo:**  
Menüdeki kahveleri görmek istiyoruz.  

```http
GET /api/kahveler
```

➡ Sunucu bize JSON formatında tüm kahvelerin listesini döner.

##### 2. POST – Yeni veri eklemek  

**Amaç:** Sunucuya yeni bir kayıt eklemek.  

 **Örnek Senaryo:**  
Filtre kahve siparişi veriyoruz.  

```http
POST /api/siparisler
````

Body (gönderilen veri):

```json
{
  "urun": "Filtre Kahve",
  "adet": 2,
  "boyut": "Grande"
}
```
➡ Sunucu yeni siparişi oluşturur ve bize sipariş numarası döner.

##### 3. PUT – Var olan veriyi güncellemek  

**Amaç:** Mevcut bir kaydı tamamen değiştirmek.  

 **Örnek Senaryo:**  
Sipariş verdiğimiz kahveyi **küçük boy** yapmaya karar verdik.  

```http
PUT /api/siparisler/123
```

Body:

```json
{
  "urun": "Filtre Kahve",
  "adet": 2,
  "boyut": "Tall"
}
```
➡ Sipariş 123 artık küçük boy kahve ile güncellenir.

##### 4. DELETE – Veri silmek  

**Amaç:** Var olan bir kaydı silmek.  

 **Örnek Senaryo:**  
Siparişi iptal etmek istiyoruz.  

```http
DELETE /api/siparisler/123
```
➡ Sunucu siparişi siler ve şu yanıtı döner: "mesaj": "Sipariş iptal edildi"

## RESTful Servislerin Çalışma Mantığı

**REST (Representational State Transfer)**, web servislerinin nasıl tasarlanacağını belirleyen bir prensiptir.  

### Mantığı
- **Kaynaklar (resources)** vardır → örnek: **kullanıcılar, ürünler, siparişler**  
- Bu kaynaklara **URL üzerinden** erişilir → `https://api.site.com/users/1`  
- Her işlem için **HTTP metodları** kullanılır: **GET, POST, PUT, DELETE**  



###  Küçük Senaryo: “Alışveriş Sitesi”

```http
GET /products      → Tüm ürünleri getir
GET /products/5    → ID’si 5 olan ürünü getir
POST /products     → Yeni ürün ekle
PUT /products/5    → 5 numaralı ürünü güncelle
DELETE /products/5 → 5 numaralı ürünü sil
```
- Görüldüğü gibi, URL’de sadece kaynak adı olur.
- Ne yapılacağına HTTP metodu karar verir.

#### REST’in Avantajları
- Basit ve anlaşılırdır.
- Her platformdan (C#, Java, Python, JavaScript vb.) kolayca kullanılabilir.
- JSON formatı ile çalıştığı için hafif ve hızlıdır.

### RESTful Servislerin Çalışma Mantığı

```mermaid
sequenceDiagram
    participant Client as İstemci (Frontend)
    participant Server as Sunucu (Backend / API)
    participant DB as Veritabanı

    Client->>Server: HTTP İsteği (GET/POST/PUT/DELETE)
    Server->>DB: Veriyi sorgula / güncelle
    DB-->>Server: Veriyi döndür
    Server-->>Client: JSON formatında cevap
    Client-->>Client: Kullanıcıya sonucu göster
```

## JSON Veri Formatı ve Kullanım Amacı

- **JSON (JavaScript Object Notation)**, veri saklamak ve taşımak için kullanılan çok basit bir formattır.  
- **İnsanların okuması kolaydır**, aynı zamanda bilgisayarlar da rahatça anlayıp işleyebilir.  
- Özellikle **istemci (frontend)** ile **sunucu (backend)** arasında veri alışverişinde en çok tercih edilen formattır.  
- Veriler **anahtar : değer (key : value)** şeklinde tutulur.
  

#### Örnek JSON Verisi

```json
{
  "siparisId": 12345,
  "urun": {
    "ad": "Filtre Kahve",
    "boyut": "Orta Boy",
    "sicaklik": "Soguk",
    "süt": false
  },
  "fiyat": 45.00,
  "adet": 2,
  "toplamTutar": 90.00,
  "musteri": {
    "ad": "Feyza",
    "odemeYontemi": "Kredi Kartı"
  },
  "hazirMi": false
}
```
#### Açıklama

- **"siparisId": 12345** → Siparişin kimlik numarası.  
- **"urun": {...}** → İç içe nesne, ürünün detaylarını tutuyor.  
  - **"ad": "Filtre Kahve"** → Sipariş edilen ürün.  
  - **"boyut": "Orta Boy"** → Kahvenin boyutu.  
  - **"sicaklik": "Soguk"** → Kahvenin sıcak mı soğuk mu olacağı.  
  - **"süt": false** → Sütsüz kahve seçilmiş.  
- **"fiyat": 45.00** → Bir kahvenin fiyatı.  
- **"adet": 2** → Kaç tane kahve sipariş edildiğini belirtir.  
- **"toplamTutar": 90.00** → İki kahve için toplam ücret.  
- **"musteri": {...}** → Müşteri bilgilerini içerir.  
  - **"ad": "Feyza"** → Siparişi veren kişi.  
  - **"odemeYontemi": "Kredi Kartı"** → Ödeme şekli.  
- **"hazirMi": false** → Sipariş hazır mı? (**Henüz hazırlanıyor**).

  👉 Bu örnekle, API’ye `/api/siparis/12345` şeklinde sorgu attığında sistem sana bu **JSON** çıktısını dönebilir.  

 Aynı yapıyı, bir **kahve zincirinin mobil uygulamasında sipariş takibi** için düşünebilirsin.  
Kullanıcı uygulamadan siparişini görüntüler, backend de bu JSON verisini döndürerek **sipariş detaylarını** sağlar.  

## SOAP ve GraphQL Nedir, REST’ten Farkları

###  SOAP (Simple Object Access Protocol)
- **XML tabanlı** bir iletişim protokolüdür.  
- Daha **katı kurallara** sahiptir (standart yapılar, güvenlik ekleri vs.).  
- Özellikle **bankacılık, finans, telekom** gibi güvenliğin çok önemli olduğu yerlerde tercih edilir.  
- Daha **ağırdır**, öğrenmesi ve kullanması **REST’e göre zordur**.  

 **Benim için:** SOAP bana biraz *“eski usul ama güvenli”* sistemleri hatırlatıyor.  


###  GraphQL
- **Facebook** tarafından geliştirilmiş bir **sorgulama dili**dir.  
- İstemci sadece **ihtiyacı olan veriyi** ister, fazlası gelmez.  
- Tek bir **endpoint** üzerinden çalışır (REST’te olduğu gibi farklı endpointlere gerek kalmaz).  
- Daha **esnek** ve **performanslıdır**, ama öğrenme eğrisi **REST’e göre biraz daha zordur**.  

 **Benim için:** GraphQL bana *“menüden sadece istediğini seçip almak”* gibi geliyor.  


## REST vs SOAP vs GraphQL Karşılaştırma


| Özellik          | REST                        | SOAP                     | GraphQL                               |
|------------------|-----------------------------|--------------------------|---------------------------------------|
| **Veri formatı** | JSON (çoğunlukla)           | XML                      | JSON                                  |
| **Esneklik**     | Orta (endpointlere bağlı)   | Düşük (çok katı)         | Yüksek (tam istenilen veri gelir)     |
| **Kullanım alanı** | Genel web servisleri        | Bankacılık, güvenlik odaklı | Modern web & mobil uygulamalar        |
| **Öğrenme kolaylığı** | Kolay                      | Zor                      | Orta                                  |
| **Performans**   | Genelde iyi                 | Ağır                     | Daha hızlı (fazla veri gelmez)        |



## 4. ASP.NET
## 5. Veritabanı ve ORM
## 6. Güvenlik ve Performans
## 7. Logging ve Hata Yönetimi
## 8. Yazılım Geliştirme Prensipleri
