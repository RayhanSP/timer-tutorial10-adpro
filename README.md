"# timer-tutorial10-adpro

## Experiment 1.2: Understanding how it works

Pada eksperimen ini, program berhasil dijalankan dengan output yang sesuai. Output \"hey hey\" muncul lebih dahulu karena perintah `println!(\"Rayhan's Komputer: hey hey\")` langsung dieksekusi oleh thread utama sebelum executor mulai bekerja. Sementara itu, task yang didaftarkan melalui `spawner.spawn(...)` hanya dimasukkan ke dalam queue dan baru diproses ketika `executor.run()` dipanggil. Di dalam task tersebut, output \"howdy!\" dicetak, diikuti oleh jeda dua detik dari `TimerFuture`, dan akhirnya output \"done!\" muncul. Gambar di bawah ini memberikan ilustrasi bagaimana executor dan spawner bekerja untuk menangani future yang dijalankan.

![Understanding How It Works](image/understandingHowItWorks.png)

## Experiment 1.3: Multiple Spawn and removing drop

### Multiple Spawn:
![Multiple Spawn](image/withDrop.png)
Dengan multiple spawn, task berjalan secara bersamaan. Hal ini terlihat dari output yang menunjukkan bahwa urutan penyelesaian task tidak selalu sesuai dengan urutan deklarasi di kode. Executor memproses task yang tersedia di queue secara paralel, sehingga hasilnya bisa berbeda setiap kali dijalankan.

### Without Drop Spawner:
![Without Drop Spawner](image/withoutDrop.png)
Ketika `drop(spawner)` dihapus, program tetap berjalan karena spawner terus menunggu untuk mengeksekusi tugas baru. Tanpa `drop(spawner)`, executor tidak mengetahui bahwa tidak ada lagi tugas yang akan datang, sehingga program tidak akan berhenti secara otomatis.
"
