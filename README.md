# inter-processor-communication

---

### 🔁 OpenAMP Üzerinden Mesaj Akışı:

1. ✅ **CM7**, `OPENAMP_send()` fonksiyonu ile `"Merhaba"` mesajını gönderir.
2. ✅ **CM4**, bu mesajı `rpmsg_recv_callback()` içinde alır.

   * Alınca UART ile terminale `"Merhaba"` yazar.
   * Ardından yine `OPENAMP_send()` ile `"Merhaba aldim"` mesajını geri yollar.
3. ✅ **CM7**, gelen `"Merhaba aldim"` mesajını kendi `rpmsg_recv_callback()` fonksiyonu ile alır ve terminale yazar.

---

🧩 Yani:
**Her iki mesaj da OpenAMP üzerinden RPMsg ile taşınır.** UART sadece terminalde yazı göstermek için kullanılır, veri iletiminde görevli değildir.

