<p align="center">
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original-wordmark.svg" alt="Docker" width="200"/>
  <br>
  <h1>Secure RDP over Internet with Playit.gg</h1>
  <p>Akses lingkungan desktop pribadi Anda dari mana saja secara aman menggunakan Docker dan tunnel instan dari Playit.gg.</p>
</p>

<p align="center">
    <img src="https://img.shields.io/badge/Docker%20Compose-v3.8-blue?style=for-the-badge&logo=docker" alt="Docker Compose Version">
    <img src="https://img.shields.io/badge/Status-Active-success?style=for-the-badge" alt="Project Status">
    <img src="https://img.shields.io/docker/pulls/linuxserver/rdesktop?style=for-the-badge&logo=docker" alt="Docker Pulls">
    <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License">
</p>

---

## 🚀 Fitur Utama

Proyek ini memungkinkan Anda untuk menjalankan desktop Linux (XFCE) di dalam kontainer Docker dan mengaksesnya melalui RDP dari mana saja di dunia tanpa perlu konfigurasi port forwarding atau IP publik yang rumit.

* ✨ **Zero-Config Tunneling**: Langsung online dengan `playit.gg` tanpa pengaturan router.
* 🐳 **Sepenuhnya Terkontainerisasi**: Seluruh setup (RDP & Tunnel) diatur oleh Docker Compose.
* 🔒 **Aman Secara Default**: Tidak ada port yang diekspos ke publik. Kredensial disimpan dengan aman di file `.env`.
* 💾 **Penyimpanan Persisten**: Data dan konfigurasi desktop Anda akan tetap ada bahkan setelah restart.
* 🌐 **Akses Global**: Hubungkan RDP Anda dari jaringan mana pun selama ada koneksi internet.

##  diagrama Arsitektur

Berikut adalah gambaran sederhana tentang bagaimana semua komponen terhubung:

```mermaid
graph TD
    A[👨‍💻 Anda] -->|Klien RDP| B(🌐 Internet);
    B --> C{🌍 Playit.gg Cloud};
    subgraph "🐳 Mesin Docker Anda"
        C <--> D[Tunnel Container];
        D -->|Koneksi Internal Docker| E[RDP Desktop Container];
    end

    style A fill:#D6EAF8,stroke:#333,stroke-width:2px
    style C fill:#D5F5E3,stroke:#333,stroke-width:2px
    style D fill:#FCF3CF,stroke:#333,stroke-width:2px
    style E fill:#FADBD8,stroke:#333,stroke-width:2px
