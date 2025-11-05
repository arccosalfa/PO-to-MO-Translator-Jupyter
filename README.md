# 🌍 PO to MO Türkçe Çeviri Aracı (Jupyter Edition)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Platform](https://img.shields.io/badge/Platform-Jupyter-orange)
![License](https://img.shields.io/badge/License-Free-green)

Bu Jupyter Notebook, `.po` uzantılı çeviri dosyalarını otomatik olarak Türkçeye çevirip `.mo` formatında **Türkçe yama** haline getirir.  
Oyunlar, yazılımlar veya web uygulamalarında kullanılan dil dosyalarını hızlıca çevirmek için tasarlanmıştır.

---

## 🚀 Özellikler

- 📦 `.po` dosyalarını yükler ve otomatik olarak Türkçeye çevirir  
- ⚙️ Çevrilen dosyayı `.mo` olarak derler (uygulamalar tarafından doğrudan okunabilir)  
- 🌐 **Google Translate Gizli API** kullanır (`translate.googleapis.com`)  
- 🧩 Kod parçalarını, HTML tag’lerini ve özel değişkenleri korur  
- ⚡ **20 thread** ile paralel (çoklu) çeviri yapar  
- 💾 Her 1000 çeviride otomatik checkpoint kaydı  
- 🧠 Boş, sembol veya özel formatlı metinleri otomatik atlar  

---

## 🧠 Çalışma Mantığı

1. `.po` dosyası (`EN.po`) Jupyter ortamında yüklenir.  
2. Her satırdaki `msgid` ve `msgstr` değerleri incelenir.  
3. Normal metinler Google Translate API’ye gönderilir ve Türkçeye çevrilir.  
4. Özel ifadeler (`{}`, `<<m:...>>`, `<b>...</b>` vb.) korunur.  
5. Çevrilmiş metinler yeni `.po` dosyasına (`TR_FULL.po`) yazılır.  
6. Son olarak `.mo` dosyası (`TR_FULL.mo`) oluşturulur.  

---

## ⚙️ Kullanılan Teknolojiler

| Kütüphane | Görevi |
|------------|---------|
| `polib` | `.po` / `.mo` dosyalarını okuma ve yazma |
| `requests` | Google Translate API çağrısı |
| `re` | Regex filtreleme |
| `concurrent.futures` | Çoklu iş parçacığı (multi-thread çeviri) |
| `time` | Zaman ölçümü ve gecikme kontrolü |

---

## 🌐 Kullanılan API

> **Google Translate Gizli API (Unofficial)**  
> `https://translate.googleapis.com/translate_a/single?client=gtx&sl=en&tl=tr&dt=t&q=...`

Bu API, tarayıcıda Google Translate kullandığında arka planda yapılan çağrıyla aynıdır.  
- ✅ Ücretsizdir  
- ✅ API anahtarı gerekmez  
- ⚠️ Fazla kullanımda IP sınırına takılabilir  

---

## 🔧 Kullanım (Jupyter Üzerinde)

1. Gerekli kütüphaneleri yükle:
   ```bash
   pip install polib requests
