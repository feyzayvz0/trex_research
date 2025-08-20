# trex_research
.NET Backend Geliştirme - Temel Bilgi ve Kavramlar Araştırma Raporu

# .NET Backend Geliştirme – Temel Bilgi ve Kavramlar

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

## 2. .NET Ekosistemi
## 3. Backend Geliştirme Temelleri
## 4. ASP.NET
## 5. Veritabanı ve ORM
## 6. Güvenlik ve Performans
## 7. Logging ve Hata Yönetimi
## 8. Yazılım Geliştirme Prensipleri
