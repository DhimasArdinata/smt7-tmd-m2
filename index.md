---

### **Struktur Presentasi: Standar Sistem Komunikasi 5G**

---

#### **Slide 1: Halaman Judul**

**Tugas 01: Standar Sistem Komunikasi**
### **Analisis Arsitektur Sistem 5G (5GS)**

**(Logo Prodi/Universitas Anda)**

**Kelompok [Nomor Kelompok]:**
*   [Nama Anggota 1]
*   [Nama Anggota 2]
*   [Nama Anggota 3]
*   [Nama Anggota 4]

**Prodi STr. Teknik Telekomunikasi**
**Kelas: [Kelas Anda]**
**Pengampu: Amin Suharjono**
**[Tanggal Presentasi]**

---

#### **Slide 2: Agenda Presentasi**

**Agenda**

1.  **Judul & Ruang Lingkup Standar**
    *   Membedah identitas dan tujuan dari dokumen standar 5G.

2.  **Informasi Umum: Arsitektur & Prinsip Dasar 5G**
    *   Memahami paradigma baru dan komponen utama dalam arsitektur 5G.

3.  **Fitur Unggulan dan Spesifikasi Teknis**
    *   Menyelami fitur-fitur kunci yang mendefinisikan kemampuan 5G.

4.  **Teknologi Terkait Antarmuka Radio (Radio Interface)**
    *   Menganalisis interaksi antara Jaringan Inti (5GC) dan Jaringan Akses Radio (NG-RAN).

5.  **Kesimpulan**

---

### **BAGIAN 1: JUDUL & RUANG LINGKUP STANDAR**

---

#### **Slide 3: Detail Standar Teknologi**

**Judul Standar Teknologi: Arsitektur Sistem 5G**

*   **Judul Resmi:** ETSI TS 123 501 V18.10.0 (2025-07)
*   **Organisasi Pengembang:** 3GPP (3rd Generation Partnership Project)
*   **Referensi:** 3GPP TS 23.501, Release 18 ("5G-Advanced")
*   **Fokus Dokumen:** Mendefinisikan **Arsitektur Stage 2** untuk Sistem 5G (5GS).

**Apa itu Arsitektur "Stage 2"?**
*   **Stage 1:** Kebutuhan layanan dari perspektif pengguna.
*   **Stage 2 (Dokumen ini):** Arsitektur Fungsional. Mendefinisikan blok-blok fungsional (**Network Functions**) dan bagaimana mereka berinteraksi.
*   **Stage 3:** Protokol dan prosedur detail untuk implementasi.

> Dokumen ini adalah "blueprint" arsitektur yang menjadi fondasi bagaimana seluruh ekosistem 5G bekerja.

**[Catatan untuk Presenter]:**
*   Jelaskan bahwa 3GPP adalah badan standardisasi global, dan ETSI adalah salah satu organisasi yang merilisnya untuk regional Eropa.
*   Tekankan bahwa TS 23.501 adalah dokumen paling fundamental untuk memahami arsitektur 5G Core.
*   Sebutkan bahwa Release 18 sering disebut sebagai "5G-Advanced", yang berarti standar ini terus berkembang dengan fitur-fitur baru yang lebih canggih.

---

### **BAGIAN 2: INFORMASI UMUM (OVERVIEW)**

---

#### **Slide 4: Visi & Prinsip Kunci Arsitektur 5G**

**Prinsip Desain Fundamental 5G**
*(berdasarkan Klausul 4.1)*

*   **[Icon Pemisahan]**
    **Separasi Control Plane (CP) & User Plane (UP)**
    Memisahkan fungsi kontrol (signaling) dari fungsi pengiriman data (traffic). Memungkinkan *scaling* independen dan *edge computing*.

*   **[Icon API/Services]**
    **Service-Based Architecture (SBA)**
    Paradigma baru di mana *Network Functions* (NFs) menawarkan "layanan" melalui API, menggantikan antarmuka *point-to-point* yang kaku. Lebih modular dan *cloud-native*.

*   **[Icon Database]**
    **Stateless Network Functions**
    Fungsi jaringan tidak menyimpan *state* secara permanen. Konteks UE disimpan terpusat di UDM, meningkatkan keandalan dan skalabilitas.

*   **[Icon Konektivitas]**
    **Converged Core untuk Beragam Akses**
    Satu jaringan inti (5GC) yang dapat diakses melalui berbagai teknologi: 5G NR, Wi-Fi, dan bahkan jaringan kabel.

**[Catatan untuk Presenter]:**
*   Ini adalah slide konsep tingkat tinggi. Jelaskan setiap poin sebagai evolusi signifikan dari arsitektur 4G/LTE.
*   Contoh untuk CP/UP separation: UPF bisa diletakkan di dekat pabrik untuk latensi super rendah (URLLC), sementara AMF/SMF bisa tetap terpusat.
*   Untuk SBA, jelaskan analogi seperti arsitektur *microservices* di dunia IT, yang membuat jaringan lebih lincah.

---

#### **Slide 5: Service-Based Architecture (SBA) - Sebuah Paradigma Baru**

**[Diagram sederhana: 4G vs 5G]**
*   **Kiri (4G):** Tunjukkan beberapa boks (MME, SGW, PGW) yang terhubung dengan garis-garis kaku berlabel (S11, S5, dll). Beri label "Arsitektur Point-to-Point".
*   **Kanan (5G):** Tunjukkan beberapa boks (AMF, SMF, PCF) yang terhubung ke sebuah "bus" atau "awan" sentral berlabel "Service Bus / SBI". Beri label "Service-Based Architecture".

**Komponen Utama SBA:**
*   **Network Function (NF):** Entitas fungsional (misal: AMF, SMF) yang menyediakan layanan.
*   **NF Service:** Kemampuan yang diekspos oleh sebuah NF.
*   **NF Repository Function (NRF):** Berfungsi sebagai "Yellow Pages". NF mendaftarkan layanannya di NRF, dan NF lain dapat menemukan layanan yang mereka butuhkan melalui NRF.

**Keuntungan:**
*   **Fleksibilitas:** Mudah menambah atau memperbarui fungsi jaringan.
*   **Skalabilitas:** Dapat di-scale secara dinamis seperti aplikasi cloud.
*   **Efisiensi:** Mendorong penggunaan kembali (reusability) fungsi.

**[Catatan untuk Presenter]:**
*   Gunakan slide ini untuk menjelaskan secara mendalam apa itu SBA karena ini adalah inti dari arsitektur 5GC.
*   Tekankan bahwa NRF adalah "otak" dari *service discovery*, yang memungkinkan fleksibilitas ini. Tanpa NRF, SBA tidak akan efisien.

---

#### **Slide 6: Arsitektur Sistem 5G (5GS) - Non-Roaming**

**[Diagram arsitektur yang disederhanakan dari Klausul 4.2.3, Figure 4.2.3-1]**
*(Diagram harus menunjukkan hubungan antara komponen utama)*

**Alur Utama:**
*   **UE (User Equipment):** Perangkat pengguna.
*   **NG-RAN (Next-Gen Radio Access Network):** Jaringan akses radio 5G.
*   **UPF (User Plane Function):** Gerbang lalu lintas data ke jaringan eksternal (DN).
*   **AMF (Access & Mobility Function):** Titik terminasi untuk sinyal kontrol dari UE dan RAN.
*   **SMF (Session Management Function):** Mengelola sesi data PDU.
*   **UDM, PCF, AUSF, NRF:** Fungsi pendukung di *control plane*.

**Antarmuka Kunci:**
*   **N1:** Antara UE dan AMF (membawa pesan NAS).
*   **N2:** Antara NG-RAN dan AMF (kontrol).
*   **N3:** Antara NG-RAN dan UPF (data pengguna).
*   **N4:** Antara SMF dan UPF (instruksi untuk penanganan data).
*   **N6:** Antara UPF dan Data Network (misalnya, Internet).

**[Catatan untuk Presenter]:**
*   Gunakan diagram untuk menjelaskan alur sinyal dan data.
*   Contoh: "Ketika UE ingin membuat koneksi data, ia mengirim pesan NAS melalui antarmuka **N1** ke **AMF**. AMF kemudian berkomunikasi dengan **SMF**. SMF lalu memberikan instruksi ke **UPF** melalui antarmuka **N4** untuk menyiapkan jalur data. Data pengguna kemudian mengalir dari **NG-RAN** ke **UPF** melalui tunnel **N3** dan keluar ke Internet melalui **N6**."

---

#### **Slide 7: Komponen Inti (Network Functions - NFs)**

| Kategori       | Fungsi (NF)                                  | Deskripsi Singkat                                                                       |
| :------------- | :------------------------------------------- | :-------------------------------------------------------------------------------------- |
| **Control Plane** | **AMF** (Access & Mobility Mgmt)             | Mengelola registrasi, mobilitas, dan koneksi UE. Pintu gerbang N1/N2.                  |
|                | **SMF** (Session Management)                 | Membuat, memodifikasi, dan menghapus PDU Session. Mengalokasikan IP & memilih UPF.      |
|                | **UDM** (Unified Data Management)            | Database utama untuk data pelanggan dan profil.                                         |
|                | **PCF** (Policy Control Function)            | Menyediakan aturan kebijakan (QoS, charging) ke SMF.                                    |
|                | **AUSF** (Authentication Server)             | Melakukan fungsi otentikasi.                                                            |
|                | **NRF** (NF Repository Function)             | Mendukung *service discovery* antar NF.                                                 |
|                | **NSSF** (Network Slice Selection)           | Membantu AMF dalam memilih Network Slice yang tepat.                                    |
| **User Plane** | **UPF** (User Plane Function)                | Meneruskan, memeriksa, dan menerapkan aturan QoS pada paket data pengguna.              |

**[Catatan untuk Presenter]:**
*   Jelaskan secara singkat peran masing-masing NF. Anda bisa memberikan analogi dari 4G jika audiens familiar (misalnya, AMF mengambil sebagian peran MME; SMF mengambil peran manajemen sesi dari MME, SGW-C, dan PGW-C).
*   Tekankan bahwa hanya UPF yang berada di jalur data pengguna secara langsung. Ini penting untuk performa dan latensi.

---

### **BAGIAN 3: FITUR UNGGULAN & SPESIFIKASI**

---

#### **Slide 8: Fitur Unggulan 1: Network Slicing**

**Konsep: Satu Jaringan Fisik, Banyak Jaringan Virtual**
*(berdasarkan Klausul 5.15)*

**[Diagram konseptual: Sebuah infrastruktur fisik 5G di bawah, dengan 3 "slice" virtual di atasnya: satu untuk Mobile Broadband (eMBB), satu untuk mobil otonom (URLLC), satu untuk sensor IoT (mMTC)]**

**Spesifikasi Teknis:**
*   **Identifikasi Slice:** Menggunakan **S-NSSAI** (*Single Network Slice Selection Assistance Information*).
    *   **SST (Slice/Service Type):** Tipe layanan (e.g., eMBB, URLLC).
    *   **SD (Slice Differentiator):** Pembeda opsional.
*   **Fungsi Kunci:** **NSSF (Network Slice Selection Function)** membantu AMF memilih *slice* yang diizinkan untuk UE berdasarkan langganan dan kebijakan jaringan.
*   **Kapasitas UE:** UE dapat terhubung ke hingga **8 network slices** secara bersamaan.

**Manfaat:**
*   **Kustomisasi Layanan:** Mengoptimalkan sumber daya untuk kasus penggunaan spesifik.
*   **Isolasi:** Performa satu *slice* tidak terpengaruh oleh *slice* lain.
*   **Peluang Bisnis Baru:** Menawarkan "Network as a Service" untuk berbagai industri.

**[Catatan untuk Presenter]:**
*   Network Slicing adalah salah satu *selling point* utama 5G. Berikan contoh nyata:
    *   Slice untuk event besar (konser): bandwidth tinggi (eMBB).
    *   Slice untuk pabrik pintar: latensi sangat rendah & keandalan tinggi (URLLC).
    *   Slice untuk smart city: koneksi masif untuk jutaan sensor (mMTC).

---

#### **Slide 9: Fitur Unggulan 2: Model QoS Berbasis Aliran (Flow-Based)**

**Dari Bearer (4G) ke QoS Flow (5G)**
*(berdasarkan Klausul 5.7)*

**Konsep:**
*   Setiap paket data pengguna dipetakan ke sebuah **QoS Flow**, bukan *EPS Bearer* yang lebih kaku.
*   Memberikan kontrol kualitas layanan yang lebih granular dan dinamis.

**Spesifikasi Teknis:**
*   **Identifikasi:**
    *   **QFI (QoS Flow Identifier):** Mengidentifikasi QoS Flow di dalam tunnel N3.
    *   **5QI (5G QoS Identifier):** Merepresentasikan sekumpulan parameter QoS (standar 1-9 atau dinamis).
*   **Parameter Kunci yang direpresentasikan oleh 5QI:**
    *   **Resource Type:** GBR (Guaranteed Bit Rate) atau Non-GBR.
    *   **Packet Delay Budget (PDB):** Target maksimal latensi.
    *   **Packet Error Rate (PER):** Target maksimal packet loss.
*   **Reflective QoS:** UE dapat secara otomatis memetakan trafik *uplink* ke QoS Flow yang sama dengan trafik *downlink* yang diterima, mengurangi beban signaling.

**[Catatan untuk Presenter]:**
*   Jelaskan perbedaan mendasar dengan 4G. Di 4G, semua trafik dalam satu bearer (misalnya, untuk internet) mendapat perlakuan yang sama. Di 5G, dalam satu PDU Session (koneksi internet), video call bisa mendapat QoS Flow dengan prioritas tinggi, sementara browsing biasa mendapat prioritas lebih rendah.

---

#### **Slide 10: Fitur Unggulan 3: Manajemen Sesi & Kontinuitas**

**PDU Session: Lebih dari Sekadar Koneksi Internet**
*(berdasarkan Klausul 5.6)*

**1. Tipe PDU Session:**
*   **IP (IPv4, IPv6, IPv4v6):** Untuk akses internet standar.
*   **Ethernet:** Untuk layanan seperti koneksi LAN virtual (*enterprise networking*).
*   **Unstructured:** Untuk transfer data tanpa header IP, misalnya untuk beberapa skenario IoT atau *untethered XR*.

**2. Session and Service Continuity (SSC) Mode:**
*   **[Icon Gembok] SSC Mode 1 (IP Address Preservation):**
    *   PDU Session Anchor (UPF) tetap sama. Alamat IP dipertahankan saat UE bergerak. Mirip dengan 4G.

*   **[Icon Panah Putus-Sambung] SSC Mode 2 (Break Before Make):**
    *   Koneksi lama dilepas sebelum koneksi baru dibuat. Anchor UPF dan alamat IP dapat berubah.

*   **[Icon Dua Panah Paralel] SSC Mode 3 (Make Before Break):**
    *   Koneksi baru (Anchor UPF baru, IP baru) dibuat **sebelum** koneksi lama dilepas.
    *   Memastikan kontinuitas layanan yang mulus. Krusial untuk *edge computing* di mana UE harus terhubung ke UPF terdekat.

**[Catatan untuk Presenter]:**
*   Jelaskan bahwa tipe PDU Session Ethernet & Unstructured membuka peluang baru di luar smartphone.
*   Fokus pada SSC Mode 3 sebagai inovasi penting. Contoh: UE bergerak dari satu *edge data center* ke *edge data center* lain. Dengan SSC Mode 3, sesi aplikasi tidak terputus karena koneksi ke *edge* baru sudah siap sebelum koneksi lama dilepas.

---

### **BAGIAN 4: TEKNOLOGI TERKAIT RADIO INTERFACE**

---

#### **Slide 12: Interaksi Core Network (5GC) dengan Radio (NG-RAN)**

**[Diagram yang menunjukkan blok 5GC dan blok NG-RAN, dengan antarmuka N2 dan N3 yang jelas di antara keduanya]**

**Antarmuka Kunci:**
*   **N2 (Control Plane): Antara NG-RAN ↔ AMF**
    *   Membawa pesan NAS (N1) antara UE dan AMF.
    *   Manajemen koneksi dan konteks UE (setup, modifikasi, rilis).
    *   Sinyal untuk *handover*.
    *   Pengiriman informasi bantuan dari AMF ke RAN.

*   **N3 (User Plane): Antara NG-RAN ↔ UPF**
    *   Tunnel GTP-U yang membawa seluruh paket data pengguna.
    *   Setiap paket di dalam tunnel memiliki header yang berisi **QFI (QoS Flow Identifier)**.

**Prinsip Pemisahan:**
*   NG-RAN tidak perlu tahu detail fungsi-fungsi di dalam 5GC (selain AMF dan UPF).
*   AMF bertindak sebagai titik kontak tunggal untuk semua urusan *control plane* dari RAN.

**[Catatan untuk Presenter]:**
*   Jelaskan bagaimana pemisahan ini membuat arsitektur lebih bersih. NG-RAN hanya perlu "berbicara" dengan AMF untuk kontrol dan UPF untuk data.
*   Tekankan lagi pentingnya QFI di tunnel N3, karena inilah cara NG-RAN tahu cara memprioritaskan paket data yang berbeda di antarmuka radio yang terbatas.

---

#### **Slide 13: Peran 5GC dalam Manajemen Sumber Daya Radio**

**Bagaimana Core Network Membantu Jaringan Radio**

**1. Penegakan QoS (QoS Enforcement):**
*   **SMF** mengirimkan **QoS Profile** (berisi 5QI, ARP, GFBR/MFBR) ke NG-RAN (melalui AMF).
*   **NG-RAN** kemudian bertanggung jawab menerjemahkan QoS Profile ini menjadi konfigurasi teknis radio, seperti:
    *   Konfigurasi **Data Radio Bearer (DRB)**.
    *   Prioritas penjadwalan (*scheduling weights*).
    *   Konfigurasi protokol RLC dan HARQ.

**2. Dukungan untuk RRC Inactive State:**
*   Untuk memungkinkan transisi cepat dari *idle* ke *aktif*, 5G memperkenalkan *RRC Inactive*.
*   **AMF** memberikan **"RRC Inactive Assistance Information"** ke NG-RAN, yang berisi:
    *   Registration Area yang dialokasikan untuk UE.
    *   Konfigurasi *paging* dan DRX UE.
    *   Informasi MICO mode.
*   Informasi ini membantu **NG-RAN** membuat keputusan cerdas tentang kapan dan bagaimana cara memindahkan UE ke state `RRC_INACTIVE`.

**[Catatan untuk Presenter]:**
*   Slide ini menunjukkan bahwa 5GC tidak hanya pasif, tetapi secara aktif memberikan informasi ke RAN untuk membantu optimisasi.
*   Jelaskan bahwa `RRC_INACTIVE` adalah fitur penting untuk efisiensi daya pada perangkat IoT dan juga mengurangi latensi koneksi untuk smartphone.

---

#### **Slide 14: Kesimpulan**

**Kesimpulan: Arsitektur 5G yang Fleksibel dan Berorientasi Layanan**

1.  **Paradigma Baru:** 5G memperkenalkan **Service-Based Architecture (SBA)** dan **pemisahan Control/User Plane**, menciptakan fondasi yang modular, skalabel, dan siap untuk cloud.

2.  **Berpusat pada Layanan:** Fitur seperti **Network Slicing** dan **Flow-Based QoS** memungkinkan penyesuaian jaringan secara granular untuk memenuhi kebutuhan beragam layanan, mulai dari *streaming video* hingga kontrol robot industri.

3.  **Kontinuitas dan Fleksibilitas:** **SSC Mode 3** dan dukungan untuk berbagai tipe PDU Session (IP, Ethernet, Unstructured) memastikan kontinuitas layanan yang tinggi dan membuka peluang untuk kasus penggunaan di luar seluler tradisional.

4.  **Sinergi Core & Radio:** Arsitektur 5G mendefinisikan interaksi yang cerdas antara **5GC** dan **NG-RAN** melalui antarmuka N2/N3, memungkinkan optimisasi *end-to-end* yang lebih baik.

> Arsitektur 5G bukan sekadar evolusi, melainkan sebuah platform fundamental yang dirancang untuk mendukung inovasi layanan di masa depan.

---

#### **Slide 15: Referensi & Tanya Jawab**

**Referensi Utama**

*   **ETSI TS 123 501 V18.10.0 (2025-07)**
    *   *5G; System architecture for the 5G System (5GS) (3GPP TS 23.501 version 18.10.0 Release 18)*

**Terima Kasih**
### **Ada Pertanyaan?**

---
