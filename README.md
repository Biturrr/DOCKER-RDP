<p align="center">
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/ubuntu/ubuntu-plain-wordmark.svg" alt="Ubuntu" width="180"/>
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original-wordmark.svg" alt="Docker" width="200"/>
  <br>
  <h1>Personal Ubuntu SSH Server, Anywhere!</h1>
  <p>Jalankan server Ubuntu 20.04 pribadi Anda di dalam Docker dan akses melalui SSH dari mana saja di dunia, berkat tunnel instan dari Playit.gg.</p>
</p>

<p align="center">
    <img src="https://img.shields.io/badge/Ubuntu-20.04_LTS-E95420?style=for-the-badge&logo=ubuntu" alt="Ubuntu Version">
    <img src="https://img.shields.io/badge/Docker%20Compose-Ready-blue?style=for-the-badge&logo=docker" alt="Docker Compose">
    <img src="https://img.shields.io/badge/Access-SSH-lightgrey?style=for-the-badge&logo=openssh" alt="SSH Access">
    <img src="https://img.shields.io/badge/Status-Active-success?style=for-the-badge" alt="Project Status">
</p>

---

Selamat datang di cara termudah untuk memiliki lingkungan shell Linux pribadi yang dapat diakses secara global. Proyek ini menggunakan `Dockerfile` untuk membangun image Ubuntu 20.04 kustom yang sudah dilengkapi dengan server SSH, lalu `Docker Compose` mengorkestrasi semuanya bersama tunnel `playit.gg` yang aman.

## 🚀 Fitur Andalan

* ⚡ **Server Pribadi Instan**: Dapatkan shell Ubuntu 20.04 yang berfungsi penuh dalam hitungan menit.
* 🔧 **Image Kustom**: `Dockerfile` disertakan agar Anda bisa dengan mudah memodifikasi dan menambahkan software sesuai kebutuhan.
* 🌐 **Akses Global via SSH**: Tidak perlu IP publik atau konfigurasi router yang rumit. Cukup gunakan alamat dari `playit.gg`.
* 🐳 **Orkestrasi Docker Compose**: Setup dua kontainer yang kompleks menjadi sangat sederhana dengan satu file `docker-compose.yml`.
* 🔒 **Keamanan Terisolasi**: Berjalan di dalam kontainer Docker yang terisolasi dan tidak mengekspos port apa pun ke host Anda.
* 💾 **Penyimpanan Persisten**: `Home directory` Anda disimpan dalam volume, sehingga file Anda aman bahkan setelah kontainer di-restart.

##  diagrama Arsitektur

```mermaid
graph TD
    A[👨‍💻 Anda] -->|Klien SSH| B(🌐 Internet);
    B --> C{🌍 Playit.gg Cloud};
    subgraph "🐳 Mesin Docker Anda"
        C <--> D[Tunnel Container];
        D -->|Koneksi Internal Docker| E[Ubuntu SSH Server (Custom Build)];
    end

    style A fill:#D6EAF8,stroke:#333,stroke-width:2px
    style C fill:#D5F5E3,stroke:#333,stroke-width:2px
    style D fill:#FCF3CF,stroke:#333,stroke-width:2px
    style E fill:#FADBD8,stroke:#333,stroke-width:2px
