# Terraform Nedir?

```bash
 Terraform, Infrastructure As A Code yani Altyapı sağlayıcıdır.
 Platform oluşturup o platform üzerinde servisleri yönetmemizi sağlar.
 Servis sağlayıcılar üzerinde yapılan işlemleri kısaltır.
 Yapılan işlemleri manuel olarak yapmayız. < Declaretive
 Açık kaynak kodludur.
```


## Terraform Kurulum


### Windows
```bash
 https://www.terraform.io/downloads > Amd64
 İnidirilen dosya zip olarak iner, zip açılır.
 Zipin icindeki terraform.exe çalışılan directoryde olması gerekir.
 C:\Users\example\example2
 Çalışılan dizinde CMD açılır ve terraform init komutu ile başlatılmış olur.
```

### Linux (Debian/Ubuntu)
```bash
 curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
 sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
 sudo apt-get update && sudo apt-get install terraform
```

### Amazon-Linux
```bash
 sudo yum install -y yum-utils
 sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
 sudo yum -y install terraform
```

### MacOS
```bash
 brew tap hashicorp/tap
 brew install hashicorp/tap/terraform
```


# AWS CLI

* Örneğin AWS içinde çalışıyorsak bunu bildirmenin birden fazla yolu vardır.
  -  Bunlardan biri AWS CLI yüklü olması durumunda oluşan .aws klasörünün içinde,
  -  Config ve Credentials dosyalarına Access Key ve Secret Access Key düzenlemesi yapılmalıdır.
  -  Terraform main.tf içinde provider kısmında Access ve Secret Access Key'i açıkça yazmak güvenli olmayabilir.
  -  Sonuncu yol ise CMD ekranından bildirmektir.

```bash
 setx AWS_PROFILE user1

 aws configure --profile "user1"
  -  Gerekli bilgileri girdikten sonra config ve credentials içine eklenmiş olur.
 
 aws configure list
  -  Belirtilmiş kullanıcıları listeler.
```


## Terraform Ne Zaman Kullanılır?

```bash
Provisioning Infastructure 
 > DevOps Team.

Application Deploying
 > Developer Team.
```

### Kullanım Alanları (AWS)

* VPC ve alt kümelerini (subnet, security group) oluştururken,
* AWS kullanıcı oluştururken,
  - Oluşan kullanıcıyla bağlantılı izinleri oluştururken,
* Sunucuları spin ederken,
* Docker yüklemek için kullanır.

## Terraform & Ansible Farkları

* Terraform
  -  Infrastructure provisioning tool < Altyapı sağlama aracı.
  -  Orchestration yeteneği daha gelişmiştir.

* Ansible
  -  Configuration tool olarak kullanılır.
  -  İlk etapta infrastructure oluşur ardından oluşan infrastructure configure edilir.
  -  Terraforma göre eskidir.

* Benzerlikler
  -  İkiside IAC (İnfrastructure As Code) altyapı sağlayıcıdır.
  -  Yapılandırılıp yönetmeyi sağlar.


### Terraform Çalışma Prensibi

* Core
  -  Declaretive kullanılarak Terraform'a emirler verilir.
  -  main.tf configuration files.

* State
  -  Tetikleyici denebilir.
  -  Terraform ne ile çalışacak sorusuna cevaptır.
  -  Çalıştıracağı materyal "state" olarak adlandırılır.
  -  Terraform'un başlangıç noktasıdır.
  -  Emirleri State'ten Core'ya götürür ve başlamış olur.


## Terraform Çalışma Alanları

### Providers

* Hangi servis sağlayıcı ile iletişime geçmek istiyorsak onu bu alanda belirtiriz.
  -  AWS, Azure, GoogleCloud.
* Terraform'u kullanrak herhangi bir servis sağlayıcıya emir vermek istiyorsak o servisin provider'ini indirmek gerekir.
  -  AWS CLI vs..
* Çalışılan 'Region' belirtilmelidir.
```bash

provider "aws" {
    region = "us-east-1"   
}
```
* main.tf'e tanımlandıktan sonra CMD'ye "terraform init" ile bildirmek gereklidir.
* Bu sayede AWS'ye emir verebiliriz.

### Resources

* Manuel yapılan işlemleri otomatik olarak yapılan yerdir.
* Altyapı parçasını tanımlar fiziksel bir bileşen olur.
* Fonksiyondur.
* Hangi servis kullanılmak istenirse bu alanda belirtilir.
  -  VPC, S3, EC2.
* Provider en başta sabittir ve onun altına Resource'ler tanımlanır.

### Variable

* Değişkenler olarak tanımlanır.
* Variable'ler variable.tf isimle bir dosya altında toplanır.
* Karışıklığı engellemesi açısından önemlidir.
* Uzun kod bloklarında değişken tanımlaması kolay olur.
* Değişkenler; String, List ve Object olmak üzere üç farklı şekilde tanımlabilir.
* Daha sonra 'main.tf' te çağılır.
  -  vpc_id = var.vpc_id < şeklinde kullanımı vardır.

### terraform.tfvars

* Variable'daki değişkenlerin değerlerini tutan bir dosyadır.
* Karmaşık yapılı gözüken sistemlerde çok büyük kolaylık sağlar.
* Tanımlanan değişkenlerin değerleri tek bir dosyada olmuş olur.


```bash

Başlangıç için karmaşık gözüksede eğlenceli bir konudur.
Bu bilgiler tamamen giriş amaçlı ve bakış açısı kazandırmak amacı ile yazılmıştır.
Başlangıç seviyesi için bilinmesi gereken temel unsurlar belirtilmiştir.
```

* GitHub: https://github.com/UgurBzkrt/TerraformGH
* Medium: https://medium.com/@ugurbzkrt
