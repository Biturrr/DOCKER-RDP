# Gunakan Ubuntu 20.04 (Focal Fossa) sebagai dasar
FROM ubuntu:20.04

# Terima argumen build-time untuk password, ini lebih aman
ARG SSH_PASSWORD

# Hindari dialog interaktif saat instalasi
ENV DEBIAN_FRONTEND=noninteractive

# Update package list dan install openssh-server, sudo, dan curl
RUN apt-get update && apt-get install -y \
    openssh-server \
    sudo \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Buat user baru bernama 'dockeruser' dengan home directory
RUN useradd -m -s /bin/bash dockeruser

# Atur password untuk 'dockeruser' menggunakan argumen yang diterima
RUN echo "dockeruser:${SSH_PASSWORD}" | chpasswd

# Tambahkan 'dockeruser' ke grup sudo agar bisa menjalankan perintah sebagai root
RUN adduser dockeruser sudo

# Buat direktori yang diperlukan oleh SSH daemon
RUN mkdir /var/run/sshd

# Konfigurasi SSHD
# Izinkan login dengan password dan jangan izinkan login sebagai root (lebih aman)
RUN echo 'PasswordAuthentication yes' >> /etc/ssh/sshd_config && \
    echo 'PermitRootLogin no' >> /etc/ssh/sshd_config

# Buat host keys untuk SSH server
RUN ssh-keygen -A

# Ekspos port 22 di dalam jaringan Docker
EXPOSE 22

# Perintah default yang akan dijalankan saat kontainer dimulai
# Menjalankan SSH daemon di foreground agar kontainer tidak mati
CMD ["/usr/sbin/sshd", "-D"]
