# 🛍️ **Trendyol Clone - Client & API App**  

🚀 **Amaç:**  
Bu proje, **Trendyol.com** e-ticaret platformunun temel özelliklerini klonlamak amacıyla geliştirilmiştir. **Mikro servis mimarisi**, **OAuth2 kimlik doğrulama**, **RBAC yetkilendirme**, ve **API erişim yönetimi** gibi modern yazılım mimarileri kullanılmıştır.

---

## 📌 **İçindekiler**
1. [Genel Bakış](#genel-bakış)  
2. [Teknik Mimarisi](#teknik-mimarisi)  
3. [Özellikler](#özellikler)  
4. [Kurulum ve Çalıştırma](#kurulum-ve-çalıştırma)  
5. [Veritabanı Tasarımı](#veritabanı-tasarımı)  
6. [Yetkilendirme (RBAC) Sistemi](#yetkilendirme-rbac-sistemi)  
7. [Çözülen Problemler](#çözülen-problemler)  
8. [Yol Haritası](#yol-haritası)  
9. [Katkıda Bulunma](#katkıda-bulunma)  
10. [Lisans](#lisans)  

---

## 🔍 **Genel Bakış**
Bu proje, **full-stack** bir e-ticaret uygulamasının **client** ve **API** taraflarını içeren bir klondur. Projede, satıcıların ürün ekleyebileceği, müşterilerin satın alabileceği ve adminlerin sistemi yönetebileceği bir yapı bulunmaktadır.

**Teknolojiler:**
- Backend: **.NET Core, CQRS, MongoDB, PostgreSQL**
- Frontend: **React.js, Next.js, Tailwind CSS**
- Kimlik Doğrulama: **OAuth2, JWT**
- Mesajlaşma: **Kafka / RabbitMQ, SignalR**
- Önbellekleme: **Redis**
- Konteyner: **Docker & Kubernetes**
- **API Gateway Pattern**
- **Onion Mimari**
- **Anlık veri transferi için Kafka ve Debezium**

---

## 🏗️ **Teknik Mimarisi**
Projede **mikro servis mimarisi** kullanılmaktadır. Her servis bağımsız olarak geliştirilmiş ve ölçeklenebilir bir yapıdadır.  

📌 **Ana servisler:**  
✅ **Auth Service**: Kimlik doğrulama ve token yönetimi  
✅ **User Service**: Kullanıcı yönetimi ve roller  
✅ **Product Service**: Ürünler ve stok yönetimi  
✅ **Order Service**: Sipariş yönetimi  
✅ **Payment Service**: Ödeme entegrasyonu  
✅ **Notification Service**: Email & SMS bildirimleri (SignalR destekli)  
✅ **Chat Service**: Anlık mesajlaşma (SignalR destekli)  

---

## 🚀 **Özellikler**
✅ OAuth2 ile güvenli giriş/çıkış  
✅ JWT ile kimlik doğrulama  
✅ Role-Based Access Control (RBAC)  
✅ API Access Key yönetimi  
✅ Yetkilendirme mekanizmaları  
✅ Store oluşturma ve yönetme  
✅ Ürün ekleme, silme ve güncelleme  
✅ Sipariş oluşturma ve takibi  
✅ Anlık bildirimler ve mesajlaşma (SignalR)  
✅ Gerçek zamanlı veri senkronizasyonu (Kafka + Debezium)  

---

## ⚙️ **Kurulum ve Çalıştırma**
### **1. Gereksinimler**
- [.NET 8 SDK](https://dotnet.microsoft.com/)
- [Node.js & NPM](https://nodejs.org/)
- [Docker](https://www.docker.com/)
- [PostgreSQL](https://www.postgresql.org/)
- [MongoDB](https://www.mongodb.com/)

### **2. Çalıştırma Adımları**
1. **Backend’i Çalıştırın**  
```bash
cd Trendyol-Clone-Api
dotnet run
```
2. **Frontend’i Çalıştırın**  
```bash
cd Trendyol-Clone-Client
npm install
npm run dev
```

---

## 🛠️ **Veritabanı Tasarımı**
📌 **User Servisi için SQL Veritabanı Şeması**  

| **Tablo**       | **Açıklama** |
|-----------------|-------------|
| `users`        | Kullanıcı bilgileri |
| `roles`        | Kullanıcı rollerini tutar |
| `permissions`  | Yetkilendirme sistemini yönetir |
| `user_roles`   | Kullanıcı-rol ilişkisi |
| `role_permissions` | Roller için yetkiler |
| `stores`       | Kullanıcılara ait mağazalar |
| `user_api_keys` | API Access Key yönetimi |

👉 **[Detaylı SQL Kodları İçin Tıklayın](#)**  

---

## 🔐 **Yetkilendirme (RBAC) Sistemi**
Bu proje, **Role-Based Access Control (RBAC)** modelini kullanır.  

Örnek Yetkilendirme Akışı:  
✅ **Ali** → Seller rolüne sahiptir.  
✅ **Seller rolü** → "product", "create" yetkisine sahiptir.  
✅ **Ali** ürün ekleyebilir, ancak siparişleri silemez.  

### **Örnek Roller ve Yetkiler**
| **Rol**   | **Yetkiler** |
|-----------|-------------|
| Admin    | Tüm sistem yönetimi |
| Seller   | Ürün ekleme/güncelleme/silme |
| Customer | Ürün satın alma |

👉 **[RBAC Detaylı Şema İçin Tıklayın](#)**  

---

## 🛠️ **Çözülen Problemler**
Bu projeyi geliştirirken karşılaşılan bazı teknik problemler ve çözümleri:  

✅ **OAuth2 ile Token Yönetimi:** MongoDB'de refresh token saklama  
✅ **PostgreSQL Performans Optimizasyonu:** Indexleme, FK ilişkileri  
✅ **API Access Key Güvenliği:** HMAC & Expiry mekanizması  
✅ **Yetkilendirme Cache Yönetimi:** Redis ile RBAC sonuçlarını cache’leme  
✅ **Event-Driven Mimari:** RabbitMQ ile yetkilendirme olaylarını takip etme  
✅ **Anlık Veri Senkronizasyonu:** Kafka + Debezium ile veri akışı sağlama  

👉 **[Daha Fazla Teknik Problem ve Çözümü İçin Tıklayın](#)**
