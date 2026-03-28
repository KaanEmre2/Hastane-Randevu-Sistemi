# Hastane Randevu Sistemi

Programlama ve Yazılım Laboratuvarı kapsamında geliştirilen, hastaların doktor randevusu alabildiği, doktorların kendi panelinden randevularını görebildiği ve yöneticinin doktor yönetimi yapabildiği web uygulaması.

## Özellikler

- **Hasta:** Kayıt, giriş, bölüm ve doktor seçerek randevu alma, randevuları görüntüleme ve iptal etme
- **Doktor:** Giriş, profil ve çalışma saatleri, geçmiş ve gelecek randevular
- **Yönetici:** Giriş, doktor listesi, yeni doktor ekleme, doktor silme, bölüm bilgileri

## Teknolojiler

| Bileşen | Kullanım |
|--------|----------|
| Python 3 | Sunucu tarafı |
| Flask | Web çatısı |
| PostgreSQL | Veritabanı (`psycopg2`) |
| HTML / Jinja2 şablonları | Arayüz |

## Gereksinimler

- Python 3.10+ önerilir
- PostgreSQL sunucusu
- `emre_odev` şeması altında tanımlı tablolar: `hasta`, `doktor`, `bolum`, `randevu`, `admin` (uygulama bu şemaya göre sorgular çalıştırır)

## Kurulum

1. Depoyu klonlayın veya projeyi indirin.

2. Sanal ortam oluşturup etkinleştirin (isteğe bağlı ama önerilir):

   ```bash
   python -m venv .venv
   .venv\Scripts\activate
   ```

3. Bağımlılıkları yükleyin:

   ```bash
   pip install flask psycopg2-binary werkzeug
   ```

4. PostgreSQL’de veritabanını ve `emre_odev` şemasını hazırlayın; tablolar projenizin SQL tanımlarıyla uyumlu olmalıdır.

5. Veritabanı bağlantı bilgilerini `my_flask_app/app.py` içindeki `DatabaseManager` kurulumunda güncelleyin (`host`, `port`, `database`, `user`, `password`).

## Yönetici hesabı (isteğe bağlı)

İlk admin kaydı veya şifre güncellemesi için:

```bash
cd my_flask_app
python crate_admin.py
```

Script içindeki e-posta ve şifreyi kendi ortamınıza göre düzenleyebilirsiniz.

## Çalıştırma

```bash
cd my_flask_app
python app.py
```

Tarayıcıda varsayılan adres: `http://127.0.0.1:5000`

## Önemli yollar

| Yol | Açıklama |
|-----|----------|
| `/` | Ana sayfa (kayıt) |
| `/login` | Hasta girişi |
| `/dashboard` | Hasta paneli |
| `/appointment` | Randevu alma |
| `/doctor_login` | Doktor girişi |
| `/admin_login` | Yönetici girişi |

## Proje yapısı

```
my_flask_app/
├── app.py              # Flask uygulaması ve iş mantığı
├── crate_admin.py      # Admin oluşturma / güncelleme yardımcı scripti
└── templates/          # HTML şablonları
```

## Güvenlik notu

Geliştirme için `app.py` içinde sabit `secret_key` ve veritabanı şifreleri bulunabilir. Canlı ortamda ortam değişkenleri (ör. `FLASK_SECRET_KEY`, `DATABASE_URL`) kullanın ve bu değerleri repoda paylaşmayın.

## Katkıda bulunanlar

- 230502029
- 230502015

---

*Programlama–Yazılım Lab — Proje 3*
