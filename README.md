<!DOCTYPE html>
<html lang="id" style="scroll-behavior: smooth;">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Website Pribadi - Nazwa Tri Mifthah Siregar</title>
    <style>
        :root{
        --primary:#cb1193;
        --accent:#ff4da6;
        --bg:#f8f9fc;
        --card:#fff;
        --muted:#e5e7eb;
        }
        *{box-sizing:border-box}
        body {
        font-family: "Poppins", Arial, sans-serif;
        margin: 0;
        background: var(--bg);
        color: #222;
        overflow-x: hidden;
        scroll-behavior: smooth;
        }

        /* ========== Navbar ========== */
        nav {
        position: sticky;
        top: 0;
        background: var(--primary);
        padding: 12px 0;
        box-shadow: 0 4px 12px rgba(0,0,0,0.08);
        z-index: 120;
        }
        nav ul {
        list-style: none;
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        gap: 12px;
        margin: 0;
        padding: 0;
        }
        nav a {
        text-decoration: none;
        color: white;
        font-weight: 600;
        padding: 8px 14px;
        border-radius: 20px;
        transition: 180ms ease;
        display: inline-block;
        }
        nav a:hover { background: rgba(255,255,255,0.12); }
        nav a.active {
        background: white;
        color: var(--primary);
        box-shadow: 0 2px 8px rgba(0,0,0,0.06);
        }

        /* ========== Header ========== */
        header {
        background: linear-gradient(135deg, var(--primary), #eae8ea);
        color: white;
        padding: 2.5rem 1rem;
        border-bottom-left-radius: 40px;
        border-bottom-right-radius: 40px;
        box-shadow: 0 4px 12px rgba(0,0,0,0.08);
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 1.5rem;
        flex-wrap: wrap;
        text-align: left;
        }
        .profile-pic {
        width: 160px;
        height: 160px;
        object-fit: cover;
        border-radius: 18px;
        border: 4px solid #fff;
        box-shadow: 0 6px 12px rgba(0,0,0,0.12);
        flex-shrink: 0;
        }
        .header-text h1 { margin: 0; font-size: 2.1rem; }
        .header-text p { margin-top: 8px; font-style: italic; opacity: .95; }

        .container { max-width: 950px; margin: 2rem auto; padding: 0 1rem; }
        section {
        background: var(--card);
        padding: 1.4rem;
        margin-bottom: 1.6rem;
        border-radius: 14px;
        box-shadow: 0 6px 16px rgba(0,0,0,0.06);
        transition: transform .18s;
        }
        section:hover { transform: translateY(-4px); }
        h2 {
        margin-top: 0;
        color: #9f0f78;
        border-bottom: 2px solid #f1f1f2;
        padding-bottom: 8px;
        }
        
        ul.pills { list-style:none; padding:0; display:flex; flex-wrap:wrap; gap:10px; margin:0; }
        ul.pills li {
        background:#eef2ff;
        padding:8px 14px;
        border-radius:20px;
        font-weight:600;
        color:#6b1a5a;
        cursor:pointer;
        transition:.18s;
        }
        ul.pills li:hover { transform: translateY(-3px); background: var(--primary); color: white; }

        table { width:100%; border-collapse:collapse; margin-top:1rem; border-radius:10px; overflow:hidden; }
        th, td { padding:12px; text-align:center; border:1px solid var(--muted); }
        th { background: var(--primary); color: #fff; }
        tr:nth-child(even){ background:#fbfbfc; }

        .skill { margin: 10px 0; }
        .skill-name { font-weight:600; margin-bottom:6px; }
        .progress { background: #eee; border-radius:10px; overflow:hidden; height:12px; }
        .progress-bar { height:100%; text-align:right; padding-right:6px; color:white; font-size:11px; line-height:12px; background: linear-gradient(90deg,var(--primary),var(--accent)); }

        /* ========== Welcome popup ========== */
        .welcome-popup {
        position: fixed; inset:0; display:flex; align-items:center; justify-content:center;
        background: rgba(0,0,0,0.45); z-index: 300; opacity:0; visibility:hidden; transition: .35s;
        }
        .welcome-popup.active { opacity:1; visibility:visible; }
        .welcome-box {
        background: #fff; padding: 28px; border-radius:14px; max-width:420px; text-align:center; box-shadow: 0 10px 32px rgba(0,0,0,0.18);
        }
        .btn { background:var(--primary); color:white; border:none; padding:8px 14px; border-radius:8px; cursor:pointer; font-weight:600;}
        .btn:hover{ filter:brightness(.95) }

        /* ========== Hobi popup  ========== */
        .hobi-popup {
        position: fixed; inset:0; display:flex; align-items:center; justify-content:center;
        background: rgba(0,0,0,0.75); z-index: 290; opacity:0; visibility:hidden; transition:.25s;
        padding:20px;
        }
        .hobi-popup.active { opacity:1; visibility:visible; }
        .hobi-modal {
        max-width:920px; width:100%; background:#fff; border-radius:12px; padding:16px; box-shadow:0 10px 40px rgba(0,0,0,0.25);
        display:flex; gap:12px; align-items:center;
        flex-wrap:wrap;
        }
        .hobi-modal img { max-width: 420px; width:100%; border-radius:10px; display:block; }
        .hobi-info { flex:1; min-width:220px; }
        .hobi-close { background:#ddd; color:#222; border:none; padding:8px 12px; border-radius:8px; cursor:pointer; }
        .hobi-caption { margin-top:8px; font-weight:600; color: #333; }
        .hobi-note { margin-top:6px; font-size:.95rem; color:#555; }

        /* ========== Flower falling ========== */
        .flower {
        position: fixed; top: -10px; pointer-events: none; font-size:20px; animation: fall linear forwards;
        transform-origin: center; z-index: 250;
        filter: drop-shadow(0 4px 6px rgba(0,0,0,0.12));
        }
        @keyframes fall {
        to { transform: translateY(110vh) rotate(360deg); opacity:0; }
        }

        @media (max-width: 768px) {
        header { flex-direction: column; text-align:center; gap:12px; }
        .profile-pic { width:120px; height:120px; }
        .hobi-modal { flex-direction:column; align-items:center; padding:12px }
        .hobi-modal img { max-width:90%; }
        }
    </style>
    </head>
    <body>

    <!-- ===== Welcome popup ===== -->
    <div class="welcome-popup" id="welcomePopup" role="dialog" aria-modal="true" aria-label="Sambutan">
        <div class="welcome-box">
        <h2>Selamat Datang! 👋</h2>
        <p>Halo, ini adalah website pribadi saya. Semoga betah menjelajahi profil saya 😊</p>
        <div style="margin-top:12px;">
            <button class="btn" onclick="closePopup()">Masuk</button>
        </div>
        </div>
    </div>

    <!-- ===== Navbar ===== -->
    <nav>
        <ul>
        <li><a href="#home" class="active">Home</a></li>
        <li><a href="#identitas">Identitas</a></li>
        <li><a href="#hobi">Hobi</a></li>
        <li><a href="#pendidikan">Pendidikan</a></li>
        <li><a href="#skill">Skill</a></li>
        <li><a href="#jadwal">Jadwal</a></li>
        <li><a href="#cv">CV</a></li>
        <li><a href="#kontak">Kontak</a></li>
        <li><a href="#mengenal">Mengenal Web</a></li>
        <li><a href="#cara">Cara Membuat Web</a></li>
        <li><a href="#kesan">Kesan & Pesan</a></li>
        </ul>
    </nav>

    <!-- ===== Header ===== -->
    <header id="home">
        <img src="./img/FOTO NONFORMAL.jpg" alt="Foto Profil Nazwa Tri Mifthah Siregar" class="profile-pic" />
        <div class="header-text">
        <h1>Nazwa Tri Mifthah Siregar</h1>
        <p>“Jangan takut gagal, itu adalah bagian dari kesuksesan.”</p>
        </div>
    </header>

    <main class="container">
        <!-- IDENTITAS -->
        <section id="identitas">
        <h2>Identitas</h2>
        <p><strong>Nama:</strong> Nazwa Tri Mifthah Siregar</p>
        <p><strong>NIM:</strong> 241401106</p>
        <p><strong>Kelas:</strong> Kom A</p>
        </section>

<!-- HOBI -->
<section id="hobi">
    <h2>Hobi</h2>
    <ul class="pills" style="cursor: default;">
        <li>Membaca</li>
        <li>Menulis</li>
        <li>Desain Web</li>
        <li>Fotografi</li>
    </ul>
    <p style="margin-top:10px; color:#555;">Berikut beberapa hobi saya yang sering saya lakukan di waktu luang.</p>
</section>

        <!-- PENDIDIKAN -->
        <section id="pendidikan">
        <h2>Pendidikan</h2>
        <table>
            <tr><th>Tingkat</th><th>Nama Sekolah</th><th>Tahun</th></tr>
            <tr><td>TK</td><td> TK/PAUD Kemala Bhayangkari</td><td>2012 - 2013</td></tr>
            <tr><td>SD</td><td>SDN 101110 </td><td>2013 - 2018</td></tr>
            <tr><td>SMP</td><td>SMP Swasta Nurul Ilmi Padangsidimpuan</td><td>2018 - 2021</td></tr>
            <tr><td>SMA</td><td>SMA Swasta Nurul Ilmi Padangsidimpuan</td><td>2021 - 2024</td></tr>
            <tr><td>Kuliah</td><td>Universitas Sumatera Utara</td><td>2023 - Sekarang</td></tr>
        </table>
        </section>

        <!-- SKILL -->
        <section id="skill">
        <h2>Skill</h2>
        <div class="skill">
            <div class="skill-name">HTML</div>
            <div class="progress"><div class="progress-bar" style="width:70%;">70%</div></div>
        </div>
        <div class="skill">
            <div class="skill-name">CSS</div>
            <div class="progress"><div class="progress-bar" style="width:85%;">70%</div></div>
        </div>
        <div class="skill">
            <div class="skill-name">JavaScript</div>
            <div class="progress"><div class="progress-bar" style="width:75%;">75%</div></div>
        </div>
        <div class="skill">
            <div class="skill-name">Word</div>
            <div class="progress"><div class="progress-bar" style="width:70%;">90%</div></div>
        </div>
        <div class="skill">
            <div class="skill-name">Desain</div>
            <div class="progress"><div class="progress-bar" style="width:70%;">90%</div></div>
        </div>
        </section>

        <!-- JADWAL PERKULIAHAN -->
<section id="jadwal">
    <h2>Jadwal Kuliah</h2>
    <table>
        <tr>
        <th>Hari</th>
        <th>Mata Kuliah</th>
        <th>Waktu</th>
        </tr>
        <tr>
        <td>Senin</td>
        <td>Lab Basis Data</td>
        <td>08:20 - 10:00</td>
        </tr>
        <td>Senin</td>
        <td>Cultural Awreness</td>
        <td>10:30 - 13:00</td>
        </tr>
        <td>Selasa</td>
        <td>IELTS Preparation</td>
        <td>08:20 - 10:00</td>
        </tr>
        <td>Selasa</td>
        <td>Lab Struktur Data</td>
        <td>10:30 - 12:10</td>
        </tr>
        <td>Selasa</td>
        <td>Kecerdasan Buatan</td>
        <td>13:50 - 16:20</td>
        </tr>
        <td>Rabu</td>
        <td>Pemrograman Web</td>
        <td>08:00 - 10:30</td>
        </tr>
        <tr>
        <td>Rabu</td>
        <td>Basis Data</td>
        <td>14:40 - 17:10</td>
        </tr>
        <td>Kamis</td>
        <td>Etika Profesi</td>
        <td>08:00 - 09:40</td>
        </tr>
        <tr>
        <td>Jumat</td>
        <td>Wirausaha Digital</td>
        <td>08:00 - 09:40</td>
        </tr>
        <td>Jumat</td>
        <td>LabPemrograman Web</td>
        <td>10:30 - 12:10</td>
        </tr>
        <td>Jumat</td>
        <td>Struktur Data</td>
        <td>13:50 - 16:20</td>
        </tr>
    </table>
</section>


        <!-- CV -->
        <section id="cv">
        <h2>Curriculum Vitae</h2>
        <p>Berisi riwayat pendidikan, pengalaman, dan keterampilan saya dalam dunia akademik dan non-akademik.</p>
        <!-- Pastikan file CV ada di folder tempat sama atau perbarui link -->
        <p><a href="cv terbaru nazwa tri mifthah_page-0001.jpg" target="_blank" style="text-decoration:none; color:var(--primary); font-weight:600;">Lihat CV Saya (klik untuk buka)</a></p>

        <!-- Jika ada file gambar jadwal semester (jaga agar id unik) -->
        <div style="margin-top:12px;">
            <strong>Portofolio </strong>
            <p><a href="NAZWA TRI MIFTHAH PORTOFOLIO ATAU CV_compressed.pdf" target="_blank" style="text-decoration:none; color:var(--primary); font-weight:600;">Lihat portofolio saya</a></p>
        </div>
        </section>

        <!-- KONTAK -->
        <section id="kontak">
        <h2>Kontak</h2>
        <p>Email: <a href="mailto:nazwatrimifthahsiregar@gmail.com" style="color:var(--primary); text-decoration:none;">nazwatrimifthahsiregar@gmail.com</a></p>
        <p>Instagram: <a href="https://instagram.com/" target="_blank" style="color:var(--primary); text-decoration:none;">@nazwa_trimiftah</a></p>
        </section>
        
<!-- SECTION: Mengenal HTML, CSS, JavaScript & Tailwind -->
<section id="pengenalan">
    <h1>🧠 Mengenal HTML, CSS, JavaScript & Tailwind</h1>

    <!-- HTML -->
    <div class="bagian">
        <h2>1️⃣ HTML (HyperText Markup Language)</h2>
        <p>
            HTML merupakan <b>bahasa dasar</b> yang digunakan untuk membangun struktur dari sebuah halaman web.
            Di dalamnya terdapat berbagai elemen seperti judul, paragraf, gambar, tabel, hingga tautan.
        </p>
        <p>
            Setiap bagian pada website — seperti header, artikel, dan footer — dibuat menggunakan tag HTML.
            Oleh karena itu, HTML sering disebut sebagai <b>“kerangka atau tulang”</b> dari sebuah website.
        </p>
        <pre><code>&lt;h1&gt;Selamat Datang di Website Saya&lt;/h1&gt;
&lt;p&gt;Ini adalah paragraf pembuka.&lt;/p&gt;
&lt;img src="foto.jpg" alt="Foto Profil"&gt;</code></pre>

<div class="video-container">
    <p>🎥 Tonton video penjelasan CSS di bawah ini:</p>
    <iframe width="560" height="315" src="https://youtu.be/0oA1Z6UKM5M?si=yw8GsAG5lVoC93SJ"
        title="Video CSS" frameborder="0" allowfullscreen></iframe>
</div>

    <!-- CSS -->
    <div class="bagian">
        <h2>2️⃣ CSS (Cascading Style Sheets)</h2>
        <p>
            Setelah struktur dibuat dengan HTML, langkah berikutnya adalah mempercantik tampilan menggunakan CSS.
            CSS berfungsi untuk <b>mengatur warna, ukuran, tata letak, font, dan gaya visual</b> dari elemen-elemen HTML.
        </p>
        <p>
            CSS bekerja seperti pakaian atau kulit pada tubuh manusia — memberi tampilan luar yang indah tanpa mengubah struktur dalamnya.
        </p>
        <pre><code>body {
    background-color: #f7f0ff;
    font-family: "Poppins", sans-serif;
}
h1 {
    color: #6a0dad;
    text-align: center;
}</code></pre>

<div class="video-container">
    <p>🎥 Tonton video penjelasan CSS di bawah ini:</p>
    <iframe width="560" height="315" src="https://www.youtube.com/embed/71a2zeC71gk"
        title="Video CSS" frameborder="0" allowfullscreen></iframe>
</div>

    <!-- JavaScript -->
    <div class="bagian">
        <h2>3️⃣ JavaScript</h2>
        <p>
            Jika HTML adalah kerangka dan CSS adalah penampilan, maka JavaScript adalah <b>otak dan tenaga penggerak</b> dari sebuah website.
            JavaScript membuat halaman web menjadi <b>dinamis dan interaktif</b> — misalnya tombol yang bisa diklik,
            tampilan yang berubah otomatis, atau animasi yang bergerak.
        </p>
        <p>
            Dengan JavaScript, website tidak hanya menampilkan informasi, tetapi juga dapat berinteraksi dengan pengguna.
        </p>
        <pre><code>&lt;button onclick="alert('Halo, selamat datang!')"&gt;Klik Saya&lt;/button&gt;</code></pre>

<div class="video-container">
    <p>🎥 Tonton video penjelasan HTML di bawah ini:</p>
    <iframe width="560" height="315" src="https://www.youtube.com/embed/0oA1Z6UKM5M"
        title="Video HTML" frameborder="0" allowfullscreen></iframe>
</div>


    <!-- Tailwind CSS -->
    <div class="bagian">
        <h2>4️⃣ Tailwind CSS</h2>
        <p>
            Tailwind CSS adalah <b>framework modern</b> berbasis CSS yang dirancang agar proses pembuatan desain web menjadi lebih cepat dan efisien.
        </p>
        <p>
            Framework ini sangat populer di kalangan web developer karena hasil tampilannya sudah <b>modern, rapi, dan responsif</b>.
        </p>
        <pre><code>&lt;h1 class="text-3xl font-bold text-purple-600 text-center"&gt;Halo Dunia!&lt;/h1&gt;
&lt;p class="text-gray-700 text-base"&gt;Ini contoh tampilan dengan Tailwind CSS.&lt;/p&gt;</code></pre>

<div class="video-container">
    <p>🎥 Tonton video penjelasan Tailwind CSS di bawah ini:</p>
    <iframe width="560" height="315" src="https://www.youtube.com/embed/DenUCuq4G04"
        title="Video Tailwind CSS" frameborder="0" allowfullscreen></iframe>
</div>

</section>
<div class="bagian">
        <h2>📋 Kesimpulan</h2>
        <p>
        Keempat komponen di atas saling melengkapi dalam pembuatan website.
        HTML membentuk strukturnya, CSS mempercantik tampilannya, JavaScript membuatnya interaktif, dan Tailwind mempercepat proses desainnya.
        </p>

        <table>
        <tr>
            <th>Teknologi</th>
            <th>Fungsi Utama</th>
            <th>Analogi</th>
        </tr>
        <tr>
            <td>HTML</td>
            <td>Membentuk struktur halaman</td>
            <td>Tulang & Kerangka</td>
        </tr>
        <tr>
            <td>CSS</td>
            <td>Memberi warna dan gaya tampilan</td>
            <td>Kulit & Pakaian</td>
        </tr>
        <tr>
            <td>JavaScript</td>
            <td>Menambahkan interaksi dan logika</td>
            <td>Otak & Gerakan</td>
        </tr>
        <tr>
            <td>Tailwind CSS</td>
            <td>Mempercepat desain dengan class siap pakai</td>
            <td>Alat bantu styling instan</td>
        </tr>
        </table>
    </div>
</section>

        <!-- CARA -->
    <section id="cara">
    <h2>Tata Cara Membuat Desain Sederhana</h2>
    <p>
        Mendesain sebuah tampilan web atau karya visual sederhana tidak memerlukan alat yang rumit.
        Yang penting adalah memahami langkah-langkah dasar agar hasilnya tetap menarik, rapi, dan mudah digunakan.
    </p>
    <ol>
        <li>
        <strong>Tentukan Tujuan Desain</strong>  
        Pahami dulu apa yang ingin kamu buat — apakah itu tampilan web pribadi, poster digital, atau kartu ucapan.
        Tujuan yang jelas akan membantu menentukan warna, font, dan gaya desain yang sesuai.
        </li>
        <li>
        <strong>Buat Sketsa atau Rancangan Kasar</strong>  
        Sebelum mulai di komputer, buat sketsa tata letak di kertas atau aplikasi seperti Figma dan Canva.
        Tentukan posisi judul, gambar, dan teks agar desain terlihat seimbang.
        </li>
        <li>
        <strong>Pilih Warna dan Font yang Serasi</strong>  
        Gunakan kombinasi warna yang harmonis dan font yang mudah dibaca.  
        Misalnya, warna utama (primer) untuk menonjolkan judul, dan warna lembut untuk latar belakang.
        </li>
        <li>
        <strong>Gunakan Elemen Visual Secukupnya</strong>  
        Tambahkan ikon, foto, atau ilustrasi, tetapi jangan berlebihan.
        Desain yang sederhana lebih mudah dipahami dan enak dilihat.
        </li>
        <li>
        <strong>Atur Keseimbangan dan Jarak</strong>  
        Pastikan setiap elemen memiliki jarak yang cukup agar tidak terlihat sesak.
        Gunakan “ruang kosong” (white space) agar tampilan terasa bersih dan profesional.
        </li>
        <li>
        <strong>Uji dan Perbaiki</strong>  
        Lihat kembali hasil desainmu di berbagai ukuran layar atau minta pendapat teman.
        Jika ada bagian yang kurang rapi, lakukan penyesuaian hingga terlihat pas.
        </li>
        <li>
        <strong>Simpan dan Gunakan Desainmu</strong>  
        Setelah selesai, simpan hasil desain dalam format yang sesuai (misalnya .png, .jpg, atau .html).
        Kamu bisa menggunakannya untuk proyek pribadi atau mempublikasikannya secara online.
        </li>
    </ol>
    <p>
        Dengan mengikuti langkah-langkah ini, kamu bisa membuat desain sederhana yang tetap terlihat profesional,
        indah, dan mencerminkan kepribadianmu sendiri 🌸
    </p>
</section>

<!-- 🔹 3. Kesan dan Pesan Belajar Pemrograman Web -->
<section id="kesan">
    <h2>Kesan dan Pesan Belajar Pemrograman Web</h2>
    <p><b>Kesan:</b> Belajar pemrograman web selama ini cukup membuat saya paham ditambah dengan adanya penjelasan di Lab Pemrograman Web yang diawalnya memang terlihat rumit dan susah buat di mengerti, tapi semakin lama semakin menarik karena bisa langsung melihat hasilnya di browser dan ternyata bahasa ya tidak terlalu sulit dibanding dengan yang lain.</p>
    </section>
    <section id="pesan">
    <h2>Kesan dan Pesan Belajar Pemrograman Web</h2>
    <p><b>Pesan:</b> Jangan takut mencoba, belajar terus sampai website mu ga error lagi 💻✨.</p>
</section>
    </main>

    <!-- ========== Scripts ========== -->
    <script>
        /* =======================
        IMPORTANT: Image files
        Place these images inside ./img/ folder:
        - FOTO NONFORMAL.jpg
        - membaca.jpg
        - menulis.jpg
        - desainweb.jpg
        - fotografi.jpg
        Also keep CV and JADWAL files (names as used in links), or update hrefs.
        ======================= */

        // Welcome popup
        const welcomePopup = document.getElementById('welcomePopup');
        function closePopup() { welcomePopup.classList.remove('active'); }

        // Show welcome when page loads
        window.addEventListener('load', () => {
        setTimeout(()=> welcomePopup.classList.add('active'), 300);
        // start flower generation (random interval)
        scheduleNextFlower();
        });

        /* ========== Hobi gallery logic ========== */
        const hobiMap = {
        membaca: {
            title: 'Membaca',
            note: 'Dokumentasi kegiatan membaca — buku favorit & catatan.',
            imgs: ['./img/membaca.jpg']
        },
        menulis: {
            title: 'Menulis',
            note: 'Contoh tulisan dan proses kreatif menulis.',
            imgs: ['./img/menulis.jpg']
        },
        desainweb: {
            title: 'Desain Web',
            note: 'Portofolio desain web: mockup & implementasi.',
            imgs: ['./img/desainweb.jpg']
        },
        fotografi: {
            title: 'Fotografi',
            note: 'Hasil jepretan & proses editing fotografi.',
            imgs: ['./img/fotografi.jpg']
        }
        };

        const hobiPopup = document.getElementById('hobiPopup');
        const hobiImg = document.getElementById('hobiImg');
        const hobiTitle = document.getElementById('hobiTitle');
        const hobiNote = document.getElementById('hobiNote');
        let currentHobiKey = null;

        function showHobi(key){
        const data = hobiMap[key];
        if(!data){
            alert('Maaf, dokumentasi untuk hobi ini belum tersedia.');
            return;
        }
        currentHobiKey = key;
        // Use first image by default (you can expand to gallery controls)
        hobiImg.src = data.imgs[0];
        hobiImg.alt = data.title + ' - dokumentasi';
        hobiTitle.textContent = data.title;
        hobiNote.textContent = data.note;
        hobiPopup.classList.add('active');
        hobiPopup.setAttribute('aria-hidden','false');
        }
        function closeHobi(){
        hobiPopup.classList.remove('active');
        hobiPopup.setAttribute('aria-hidden','true');
        // optional: clear src to stop loading
        setTimeout(()=> { hobiImg.src = ''; }, 300);
        }
        // close when clicking outside modal
        hobiPopup.addEventListener('click', closeHobi);
        // close on Escape key
        document.addEventListener('keydown', (e)=> { if(e.key === 'Escape') closeHobi(); });

        /* ========== Flower falling effect ========== */
        function createFlower(){
        const el = document.createElement('div');
        el.className = 'flower';
        // emoji alternatives: 🌸 🌺 🌷 🌼
        const emojis = ['🌸','🌺','🌷','🌼'];
        el.textContent = emojis[Math.floor(Math.random()*emojis.length)];
        // random horizontal start
        const left = Math.random() * 100;
        el.style.left = left + 'vw';
        // random size
        const size = 14 + Math.random()*20;
        el.style.fontSize = size + 'px';
        // random duration
        const duration = 4 + Math.random()*6; // seconds
        el.style.animationDuration = duration + 's';
        // slight horizontal drift using transform translateX at end via CSS not possible easily, so animate via CSS translateY + rotate, then add tiny CSS for initial rotate
        el.style.transform = `translateY(-10px) rotate(${Math.random()*60 - 30}deg)`;
        document.body.appendChild(el);
        // remove after animation ends (duration + small buffer)
        setTimeout(()=> {
            el.remove();
        }, (duration + 0.8) * 1000);
        }
        function scheduleNextFlower(){
        // random interval between 400ms and 1400ms
        const ms = 400 + Math.random()*1000;
        setTimeout(()=> {
            createFlower();
            scheduleNextFlower();
        }, ms);
        }

        /* ========== Nav active on scroll ========== */
        const navLinks = Array.from(document.querySelectorAll('nav a'));
        const sections = navLinks.map(a => document.querySelector(a.getAttribute('href')));
        function onScrollActive(){
        const offset = window.innerHeight * 0.25;
        let currentIndex = 0;
        for(let i=0;i<sections.length;i++){
            const sec = sections[i];
            if(!sec) continue;
            const rect = sec.getBoundingClientRect();
            if(rect.top - offset <= 0) currentIndex = i;
        }
        navLinks.forEach((a, idx) => {
            a.classList.toggle('active', idx === currentIndex);
        });
        }
        document.addEventListener('scroll', onScrollActive, {passive:true});
        window.addEventListener('load', onScrollActive);

        /* Optional: Smooth active link click (browser handles href anchors, but ensure small offset compensation if header sticky) */
        navLinks.forEach(a => {
        a.addEventListener('click', (e) => {
            // allow default to jump; but compensate for sticky header by small scroll if needed
            setTimeout(onScrollActive, 200);
        });
        });

    </script>
</body>
</html>

