📚 Sistem Manajemen Perpustakaan (Microservices)
Proyek ini mendemonstrasikan arsitektur sistem informasi perpustakaan modern yang tangguh (resilient). Dibangun dengan ekosistem Spring Boot dan dikelola di atas Kubernetes, sistem ini memisahkan tanggung jawab baca-tulis menggunakan pola CQRS serta dilengkapi dengan observabilitas penuh.

🏗️ Arsitektur & Tumpukan Teknologi
Sistem dirancang dengan pemisahan antara layanan fungsional dan infrastruktur pendukung:

Service Layer: * Domain Services: Buku, Anggota, Pengembalian, dan Notifikasi.

CQRS Implementation: Layanan Peminjaman dipisahkan menjadi model Command (tulis) dan Query (baca).

Infrastructure: * Service Discovery: Eureka Server untuk registrasi layanan otomatis.

Gateway: Spring Cloud Gateway sebagai pintu masuk tunggal (entry point).

Persistence & Messaging:

Databases: Kombinasi MongoDB (untuk skalabilitas) dan H2 Database (untuk performa tinggi).

Broker: RabbitMQ untuk komunikasi asinkron antar layanan (Event-driven).

Ops & Observability:

Orchestration: Kubernetes (K8s) untuk auto-scaling dan self-healing.

Logging: ELK Stack (Elasticsearch, Logstash, Kibana) terintegrasi dengan Filebeat.

Monitoring: Eksportir metrik via Prometheus yang divisualisasikan melalui dasbor Grafana.

Automation: Jenkins sebagai motor utama jalur pipa CI/CD.

🛠️ Prasyarat Lingkungan Development
Sebelum memulai, pastikan mesin pengembangan Anda telah terinstal:

Java Development Kit (JDK) 17

Apache Maven

Git

Docker Desktop (Pastikan fitur Kubernetes sudah diaktifkan)

🚀 Alur Deployment & Operasional
Ikuti urutan langkah berikut untuk menjalankan ekosistem sistem secara utuh:

1. Orkestrasi Container & Database
Lakukan deployment infrastruktur dasar terlebih dahulu. Siapkan instance MongoDB dan RabbitMQ di dalam klaster Kubernetes, kemudian lanjutkan dengan mendepoloy Core Services (Buku, Anggota, Peminjaman, dsb).

2. Konfigurasi Observabilitas (Monitoring)
Aktifkan pemantauan kesehatan sistem dengan mengintegrasikan Prometheus untuk menarik metrik dari setiap pod. Gunakan Grafana untuk membuat visualisasi real-time mengenai performa memori, CPU, dan throughput aplikasi.

3. Agregasi Log Terpusat (Logging)
Setup ELK Stack untuk mengumpulkan jejak log dari berbagai kontainer yang tersebar. Gunakan Filebeat sebagai agen pengumpul agar semua aktivitas sistem dapat ditelusuri melalui satu antarmuka di Kibana.

4. Otomatisasi Pipeline CI/CD
Gunakan Jenkins untuk mengotomatiskan siklus hidup pengembangan. Pipeline ini mencakup proses pengambilan kode dari repositori, kompilasi dengan Maven, pembuatan image Docker, hingga rolling update ke klaster Kubernetes.

📝 Catatan Penting
Setiap layanan memiliki file konfigurasi application.yml yang terintegrasi dengan sistem profil Spring. Pastikan variabel lingkungan untuk koneksi RabbitMQ dan Database sudah sesuai dengan nama service di Kubernetes.
