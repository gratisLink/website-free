
<!DOCTYPE html>
<html lang="id" data-bs-theme="light">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ringtone Generator - WhatsApp</title>
    <!-- Bootstrap 5 CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <!-- Bootstrap Icons -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.0/font/bootstrap-icons.css">
    <style>
        :root {
            --whatsapp-green: #25D366;
            --whatsapp-dark: #128C7E;
            --gradient-start: #00c6ff;
            --gradient-end: #0072ff;
        }
        
        body {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            min-height: 100vh;
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
        }
        
        .card {
            border: none;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
            transition: transform 0.3s ease;
        }
        
        .card:hover {
            transform: translateY(-5px);
        }
        
        .card-header {
            background: linear-gradient(135deg, var(--gradient-start), var(--gradient-end));
            color: white;
            font-weight: 700;
            padding: 1.5rem;
        }
        
        .card-body {
            padding: 2rem;
        }
        
        .form-control, .form-select {
            border-radius: 10px;
            padding: 0.75rem 1.25rem;
            border: 2px solid #e1e5ee;
            transition: all 0.3s;
        }
        
        .form-control:focus, .form-select:focus {
            border-color: var(--whatsapp-green);
            box-shadow: 0 0 0 0.25rem rgba(37, 211, 102, 0.25);
        }
        
        .btn-primary {
            background: linear-gradient(135deg, var(--whatsapp-green), var(--whatsapp-dark));
            border: none;
            border-radius: 10px;
            padding: 0.75rem;
            font-weight: 600;
            letter-spacing: 0.5px;
            transition: all 0.3s;
        }
        
        .btn-primary:hover {
            background: linear-gradient(135deg, var(--whatsapp-dark), #0d6e5f);
            transform: translateY(-2px);
        }
        
        .feature-icon {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--gradient-start), var(--gradient-end));
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 1rem;
        }
        
        .feature-icon i {
            font-size: 1.75rem;
            color: white;
        }
        
        .voice-option {
            border-radius: 15px;
            cursor: pointer;
            transition: all 0.3s;
            border: 2px solid transparent;
        }
        
        .voice-option.active {
            border-color: var(--whatsapp-green);
            background-color: rgba(37, 211, 102, 0.1);
        }
        
        .voice-option:hover {
            background-color: rgba(0, 0, 0, 0.03);
        }
        
        .preview-box {
            background-color: #f8f9fa;
            border-radius: 15px;
            padding: 1.5rem;
            margin-top: 1.5rem;
        }
        
        .step-card {
            border-left: 4px solid var(--whatsapp-green);
            transition: transform 0.3s;
        }
        
        .step-card:hover {
            transform: translateX(5px);
        }
        
        .theme-toggle {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 1000;
        }
        
        /* Developer Profile Styles */
        .developer-card {
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            border: none;
        }
        
        .developer-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.15);
        }
        
        /*.developer-header {
            background: linear-gradient(135deg, #6a11cb 0%, #2575fc 100%);
            padding: 1.5rem;
            text-align: center;
            color: white;
        }*/

        .developer-header {
            background: linear-gradient(135deg, #6a11cb 0%, #2575fc 100%);
            padding: 2.5rem 1rem 3rem; /* tambahkan padding bawah agar teks tidak tertutup */
            text-align: center;
            color: white;
            position: relative;
            z-index: 0;
        }
        
        /*.profile-img-container {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            border: 4px solid white;
            margin: -80px auto 20px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            background-color: white;
        }*/

        .profile-img-container {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            border: 4px solid white;
            margin: -20px auto 10px; /* kurangi dari -80px agar tidak menutupi teks */
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            background-color: white;
            position: relative;
            z-index: 1; /* supaya selalu di atas */
        }

        
        .profile-img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        /*.developer-body {
            padding: 2rem 1.5rem 1.5rem;
            text-align: center;
        }*/

        .developer-body {
            padding: 1.5rem;
            text-align: center;
        }
        
        .social-links {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 1rem;
        }
        
        .social-icon {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            background: #f0f2f5;
            color: #4e4e4e;
            transition: all 0.3s ease;
        }
        
        .social-icon:hover {
            transform: translateY(-3px);
            background: #e4e6eb;
        }
    </style>
</head>
<body>
    <div class="container py-5">
        <div class="row justify-content-center">
            <div class="col-lg-10">
                <!-- Developer Profile Card -->
                <div class="developer-card mb-5">
                    <div class="developer-header">
                        <h2 class="mb-0">Developer</h2>
                    </div>
                    <div class="card-body position-relative">
                        <div class="profile-img-container mb-3">
                            <img src="" alt="Hadi Susanto" class="profile-img">
                        </div>
                        <div class="developer-body">
                            <h3 class="mb-2">Hadi Susanto</h3>
                            <p class="text-muted mb-3">Full Stack Developer</p>
                            <p class="mb-4">Membuat solusi inovatif dengan teknologi terkini</p>
                            
                            <div class="social-links">
                                <a href="#" class="social-icon">
                                    <i class="bi bi-github"></i>
                                </a>
                                <a href="#" class="social-icon">
                                    <i class="bi bi-linkedin"></i>
                                </a>
                                <a href="#" class="social-icon">
                                    <i class="bi bi-twitter"></i>
                                </a>
                                <a href="#" class="social-icon">
                                    <i class="bi bi-instagram"></i>
                                </a>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Main Application Card -->
                <div class="card">
                    <div class="card-header text-center">
                        <h1 class="mb-0"><i class="bi bi-whatsapp me-2"></i>WhatsApp Ringtone Generator</h1>
                        <p class="mb-0">Buat ringtone kustom dengan suara AI</p>
                    </div>
                    
                    <div class="card-body">
                        
                        
                        <form method="POST">
                            
                            <div class="alert alert-success mt-3">
                                <i class="bi bi-check-circle-fill me-2"></i>
                                Ringtone berhasil dibuat! Download akan dimulai secara otomatis...
                            </div>
                            
                            <div class="mb-4">
                                <label for="text" class="form-label fw-bold">Teks Ringtone</label>
                                <textarea class="form-control" name="text" placeholder="Contoh: Ada WhatsApp baru masuk" rows="3" required>Reminder, Outlet yang tidak bisa di visit, mulai di cek, dan di tolak, kasi alasan yang tepat karena datanya disubmit jam 2:30 siang</textarea>
                                <div class="form-text">Masukkan teks yang ingin diubah menjadi suara</div>
                            </div>
                            
                            <div class="mb-4">
                                <label class="form-label fw-bold">Pilih Jenis Suara</label>
                                <div class="row g-3">
                                    <div class="col-md-6">
                                        <div class="voice-option p-3 text-center active" onclick="selectVoice('pria')">
                                            <div class="mb-2">
                                                <i class="bi bi-gender-male" style="font-size: 2rem; color: #0d6efd;"></i>
                                            </div>
                                            <h5 class="mb-1">Suara Pria</h5>
                                            <p class="mb-0 text-muted">Suara natural dan jelas</p>
                                            <input type="radio" class="btn-check" name="gender" id="pria" value="pria" autocomplete="off" checked>
                                            <label class="btn btn-sm btn-outline-primary mt-2" for="pria">Pilih</label>
                                        </div>
                                    </div>
                                    
                                    <div class="col-md-6">
                                        <div class="voice-option p-3 text-center " onclick="selectVoice('wanita')">
                                            <div class="mb-2">
                                                <i class="bi bi-gender-female" style="font-size: 2rem; color: #d63384;"></i>
                                            </div>
                                            <h5 class="mb-1">Suara Wanita</h5>
                                            <p class="mb-0 text-muted">Suara ramah dan lembut</p>
                                            <input type="radio" class="btn-check" name="gender" id="wanita" value="wanita" autocomplete="off" >
                                            <label class="btn btn-sm btn-outline-primary mt-2" for="wanita">Pilih</label>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            
                            <div class="d-grid mb-4">
                                <button type="submit" class="btn btn-primary btn-lg">
                                    <i class="bi bi-music-note-beamed me-2"></i>Buat Ringtone Sekarang
                                </button>
                            </div>
                        </form>
                        
                        <div class="preview-box">
                            <h5 class="fw-bold mb-3"><i class="bi bi-lightning-charge me-2"></i>Contoh Ringtone Populer</h5>
                            <div class="d-flex flex-wrap gap-2">
                                <button class="btn btn-sm btn-outline-secondary" onclick="setText('Ada pesan WhatsApp baru')">Ada pesan WhatsApp baru</button>
                                <button class="btn btn-sm btn-outline-secondary" onclick="setText('Kamu dapat pesan baru nih')">Kamu dapat pesan baru nih</button>
                                <button class="btn btn-sm btn-outline-secondary" onclick="setText('Hai, ada yang kirim pesan')">Hai, ada yang kirim pesan</button>
                                <button class="btn btn-sm btn-outline-secondary" onclick="setText('Ding! Pesan baru masuk')">Ding! Pesan baru masuk</button>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="mt-4">
                    <h3 class="text-center mb-4">Cara Menggunakan</h3>
                    <div class="row g-4">
                        <div class="col-md-4">
                            <div class="card step-card h-100">
                                <div class="card-body">
                                    <div class="feature-icon">
                                        <i class="bi bi-keyboard"></i>
                                    </div>
                                    <h5 class="card-title text-center">1. Buat Ringtone</h5>
                                    <p class="card-text">Masukkan teks dan pilih jenis suara yang diinginkan, lalu klik tombol "Buat Ringtone"</p>
                                </div>
                            </div>
                        </div>
                        
                        <div class="col-md-4">
                            <div class="card step-card h-100">
                                <div class="card-body">
                                    <div class="feature-icon">
                                        <i class="bi bi-download"></i>
                                    </div>
                                    <h5 class="card-title text-center">2. Download File</h5>
                                    <p class="card-text">File ringtone akan otomatis terdownload dalam format MP3</p>
                                </div>
                            </div>
                        </div>
                        
                        <div class="col-md-4">
                            <div class="card step-card h-100">
                                <div class="card-body">
                                    <div class="feature-icon">
                                        <i class="bi bi-phone"></i>
                                    </div>
                                    <h5 class="card-title text-center">3. Atur di WhatsApp</h5>
                                    <p class="card-text">Buka WhatsApp > Pengaturan > Notifikasi > Suara notifikasi > Pilih file</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <footer class="mt-5 text-center text-muted">
                    <p>© 2023 WhatsApp Ringtone Generator | Dibuat oleh Hadi Susanto</p>
                </footer>
            </div>
        </div>
    </div>
    
    <button class="btn btn-dark theme-toggle rounded-circle p-2" onclick="toggleTheme()">
        <i class="bi bi-moon-stars"></i>
    </button>
    
    <!-- Bootstrap JS Bundle -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    
    <script>
        // Fungsi untuk memilih suara
        function selectVoice(voice) {
            document.querySelectorAll('.voice-option').forEach(el => {
                el.classList.remove('active');
            });
            event.currentTarget.classList.add('active');
            document.getElementById(voice).checked = true;
        }
        
        // Fungsi untuk mengatur teks dari contoh
        function setText(text) {
            document.querySelector('textarea[name="text"]').value = text;
        }
        
        // Fungsi toggle tema gelap/terang
        function toggleTheme() {
            const htmlEl = document.documentElement;
            const currentTheme = htmlEl.getAttribute('data-bs-theme');
            const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
            
            htmlEl.setAttribute('data-bs-theme', newTheme);
            document.querySelector('.theme-toggle i').className = 
                newTheme === 'dark' ? 'bi bi-sun' : 'bi bi-moon-stars';
        }
    </script>

    
    <script>
        // Auto-trigger download
        window.onload = function() {
            setTimeout(function() {
                window.location.href = "/download/7d3d63bfa70a4b54884524ac6d994ae3.mp3";
            }, 1000);
            
            // Schedule cleanup after 5 minutes
            setTimeout(function() {
                fetch('/cleanup/7d3d63bfa70a4b54884524ac6d994ae3.mp3')
                    .then(response => response.text())
                    .then(data => console.log('File cleaned up:', data))
                    .catch(error => console.error('Cleanup error:', error));
            }, 300000); // 5 minutes
        };
    </script>
    

</body>
</html>
