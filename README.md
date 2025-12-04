# WorkFlow_24523238 – Webhook + OpenAI GPT-4o-Mini (n8n)

Workflow ini menggunakan **Webhook**, **OpenAI GPT-4o-Mini**, dan **Respond to Webhook** untuk membuat endpoint sederhana yang menerima input nama dan membalas dengan pesan sapaan otomatis.

## 📌 Fitur Utama

* Menerima request **POST** ke endpoint webhook (`/ask`)
* Mengambil data dari JSON body (contoh: `name`)
* Mengirim prompt ke model **GPT-4o-Mini**
* Mengembalikan respons dalam format **JSON**

---

## 🏗️ Arsitektur Node

### 1. **Webhook**

* Method: `POST`
* Path: `/ask`
* Mengambil data dari request dan meneruskannya ke node berikutnya.

### 2. **Message a model (OpenAI GPT-4o-Mini)**

* Model: `gpt-4o-mini`
* Template pesan:

  ```
  =Halo {{$json.body.name}}!
  ```
* Menghasilkan output berupa teks balasan model.

### 3. **Respond to Webhook**

* Response mode: JSON
* Body response:

  ```json
  {
    "answer": "{{$json['message']['content']}}"
  }
  ```

---

## 📮 Cara Menggunakan

### 1. **Import Workflow**

* Copy JSON workflow ini ke dalam n8n via:

  * **Import from File**, atau
  * **Import from Clipboard**

### 2. **Aktifkan Webhook**

* Klik **Activate Workflow**.

### 3. **Tes Request**

Gunakan Postman, curl, atau tool lain:

#### Contoh Request:

```bash
curl -X POST https://your-n8n-domain/webhook/ask \
  -H "Content-Type: application/json" \
  -d '{"name": "Azizah"}'
```

## 📦 Struktur File

Workflow JSON lengkap tersimpan di **n8n** dan dapat export ulang bila diperlukan.
