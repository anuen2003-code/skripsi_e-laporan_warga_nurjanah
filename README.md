
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>E-Laporan RW 002 Kelurahan Gandasari Kota Tangerang</title>
    <style>
        body {
            font-family: 'ArialBold', sans-serif;
            background: linear-gradient(135deg, #CADCFC, #8AB6F9);
            margin: 0;
            padding: 0;
            color: #333;
            overflow-x: hidden;
        }
        .header {
            text-align: center;
            padding: 20px;
            background: linear-gradient(157, 191, 235) #CADCFC(30, 146, 255, 0.5) #8AB6F9(146, 10, 187, 0.5) ;
            border-radius: 15px 15px 0 0;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        .header img {
            width: 80px;
            height: auto;
            margin-bottom: 10px;
        }
        .container {
            max-width: 900px;
            margin: 20px auto;
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            padding: 30px;
            animation: fadeIn 1s ease-in;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        h1, h2, h3 {
            text-align: center;
            color: #00246B;
        }
        h1 {
            font-size: 24px;
            margin-bottom: 10px;
        }
        form {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        input, select, textarea, button {
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            transition: all 0.3s;
        }
        input:focus, select:focus, textarea:focus {
            border-color: #4CAF50;
            box-shadow: 0 0 10px rgba(76, 175, 80, 0.5);
        }
        button {
            background: linear-gradient(135deg, #4CAF50, #66BB6A);
            color: white;
            border: none;
            cursor: pointer;
            font-weight: bold;
        }
        button:hover {
            transform: scale(1.05);
        }
        .hidden {
            display: none;
        }
        .section {
            margin-top: 30px;
        }
        .schedule-list, .report-list {
            margin-top: 20px;
        }
        .schedule-item, .report-item {
            background: #f9f9f9;
            padding: 15px;
            margin: 10px 0;
            border-radius: 8px;
            border-left: 5px solid #2196F3;
        }
        .logout {
            text-align: center;
            margin-top: 20px;
        }
        .logout button {
            background: #f44336;
        }
        .logout button:hover {
            background: #d32f2f;
        }
        .tabs {
            display: flex;
            justify-content: center;
            margin-bottom: 20px;
        }
        .tab {
            padding: 10px 20px;
            background: #ddd;
            border: none;
            cursor: pointer;
            border-radius: 8px 8px 0 0;
            margin: 0 5px;
            transition: background 0.3s;
        }
        .tab.active {
            background: #4CAF50;
            color: white;
        }
        .tab-content {
            display: none;
        }
        .tab-content.active {
            display: block;
        }
    </style>
</head>
<body>
    <div class="header">
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/5a/Logo_Kota_Tangerang.png/200px-Logo_Kota_Tangerang.png" alt="Logo Kota Tangerang">
        <h1>Sistem E-Laporan Kegiatan RW 002 Kelurahan Gandasari Kota Tangerang</h1>
    </div>
    
    <div class="container">
        <!-- Menu Login -->
        <div id="login-section">
            <h2>Login</h2>
            <form id="login-form">
                <select id="user-type" required>
                    <option value="">Pilih Jenis Pengguna</option>
                    <option value="rw">RW (Pengelola)</option>
                    <option value="warga">Warga</option>
                </select>
                <input type="text" id="nama" placeholder="Nama Lengkap" required>
                <input type="text" id="nik" placeholder="Nomor NIK" required pattern="\d{16}" title="NIK harus 16 digit angka">
                <button type="submit">Login</button>
            </form>
        </div>
        
        <!-- Halaman Utama Setelah Login -->
        <div id="main-section" class="hidden">
            <h2 id="welcome-message"></h2>
            
            <!-- Tabs untuk Navigasi -->
            <div class="tabs">
                <button class="tab active" onclick="showTab('jadwal')">Jadwal Kegiatan</button>
                <button class="tab" onclick="showTab('laporan')">Laporan Kegiatan</button>
                <button class="tab" id="buat-jadwal-tab" onclick="showTab('buat-jadwal')" class="hidden">Buat Jadwal</button>
            </div>
            
            <!-- Konten Tab Jadwal Kegiatan -->
            <div id="jadwal" class="tab-content active">
                <h3>Jadwal Kegiatan RW 002</h3>
                <div id="schedule-list" class="schedule-list"></div>
            </div>
            
            <!-- Konten Tab Laporan Kegiatan -->
            <div id="laporan" class="tab-content">
                <h3>Laporan Kegiatan</h3>
                <form id="report-form">
                    <select id="kegiatan" required>
                        <option value="">Pilih Jenis Kegiatan</option>
                        <option value="Posyandu">Posyandu</option>
                        <option value="Gotong Royong">Gotong Royong</option>
                        <option value="Musyawarah">Musyawarah</option>
                        <option value="Kegiatan Sosial Lain">Kegiatan Sosial Lain</option>
                        <option value="Kegiatan Keamanan">Kegiatan Keamanan</option>
                        <option value="Kegiatan Pendidikan">Kegiatan Pendidikan</option>
                    </select>
                    <textarea id="deskripsi" placeholder="Deskripsi Kegiatan (misalnya: Tanggal, Peserta, Hasil)" rows="4" required></textarea>
                    <button type="submit">Kirim Laporan</button>
                </form>
                <div id="report-list" class="report-list hidden">
                    <h4>Daftar Laporan</h4>
                    <div id="reports"></div>
                </div>
            </div>
            
            <!-- Konten Tab Buat Jadwal (Hanya RW) -->
            <div id="buat-jadwal" class="tab-content">
                <h3>Buat Jadwal Kegiatan</h3>
                <form id="schedule-form">
                    <input type="text" id="schedule-title" placeholder="Judul Kegiatan" required>
                    <input type="datetime-local" id="schedule-date" required>
                    <textarea id="schedule-desc" placeholder="Deskripsi Jadwal" rows="3" required></textarea>
                    <button type="submit">Buat Jadwal</button>
                </form>
            </div>
            
            <div class="logout">
                <button id="logout-btn">Logout</button>
            </div>
        </div>
    </div>

    <script>
        const loginSection = document.getElementById('login-section');
        const mainSection = document.getElementById('main-section');
        const buatJadwalTab = document.getElementById('buat-jadwal-tab');
        const reportList = document.getElementById('report-list');
        const welcomeMessage = document.getElementById('welcome-message');
        const scheduleList = document.getElementById('schedule-list');
        const reportsDiv = document.getElementById('reports');
        let currentUser = null;
        let schedules = JSON.parse(localStorage.getItem('rw-schedules')) || [];
        let reports = JSON.parse(localStorage.getItem('rw-reports')) || [];

        // Fungsi Login
        document.getElementById('login-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const userType = document.getElementById('user-type').value;
            const nama = document.getElementById('nama').value;
            const nik = document.getElementById('nik').value;
            
            if (nik.length !== 16 || isNaN(nik)) {
                alert('NIK harus 16 digit angka!');
                return;
            }
            
            currentUser = { type: userType, nama, nik };
            loginSection.classList.add('hidden');
            mainSection.classList.remove('hidden');
            welcomeMessage.textContent = `Selamat datang, ${nama} (${userType})!`;
            
            if (userType === 'rw') {
                buatJadwalTab.classList.remove('hidden');
                reportList.classList.remove('hidden');
                displayReports();
            }
            displaySchedules();
        });

        // Fungsi Tampilkan Tab
        function showTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(content => content.classList.remove('active'));
            document.querySelectorAll('.tab').forEach(tab => tab.classList.remove('active'));
            document.getElementById(tabId).classList.add('active');
            event.target.classList.add('active');
        }

        // Fungsi Buat Jadwal (Hanya RW)
        document.getElementById('schedule-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const title = document.getElementById('schedule-title').value;
            const date = document.getElementById('schedule-date').value;
            const desc = document.getElementById('schedule-desc').value;
            
            const schedule = {
                id: Date.now(),
                title,
                date,
                desc,
                createdBy: currentUser.nama
            };
            
            schedules.push(schedule);
            localStorage.setItem('rw-schedules', JSON.stringify(schedules));
            
            alert('Jadwal berhasil dibuat!');
            document.getElementById('schedule-form').reset();
            displaySchedules();
        });

        // Fungsi Tampilkan Jadwal
        function displaySchedules() {
            scheduleList.innerHTML = '';
            schedules.forEach(schedule => {
                const item = document.createElement('div');
                item.className = 'schedule-item';
                item.innerHTML = `
                    <strong>${schedule.title}</strong><br>
                    <small>${new Date(schedule.date).toLocaleString()}</small><br>
                    ${schedule.desc}<br>
                    <em>Dibuat oleh: ${schedule.createdBy}</em>
                `;
                scheduleList.appendChild(item);
            });
        }

        // Fungsi Kirim Laporan
        document.getElementById('report-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const kegiatan = document.getElementById('kegiatan').value;
            const deskripsi = document.getElementById('deskripsi').value;
            
            const report = {
                id: Date.now(),
                user: currentUser.nama,
                kegiatan,
                deskripsi,
                date: new Date().toLocaleString()
            };
            
            reports.push(report);
            localStorage.setItem('rw-reports', JSON.stringify(reports));
            
            alert('Laporan berhasil dikirim!');
            document.getElementById('report-form').reset();
            
            if (currentUser.type === 'rw') {
                displayReports();
            }
        });

        // Fungsi Tampilkan Laporan (Hanya RW)
        function displayReports() {
            reportsDiv.innerHTML = '';
            reports.forEach(report => {
                const item = document.createElement('div');
                item.className = 'report-item';
                item.innerHTML = `
                    <strong>${report.kegiatan}</strong> oleh ${report.user}<br>
                    <small>${report.date}</small><br>
                    ${report.deskripsi}
                `;
                reportsDiv.appendChild(item);
            });
        }

        // Fungsi Logout
        document.getElementById('logout-btn').addEventListener('click', function() {
            currentUser = null;
            mainSection.classList.add('hidden');
            loginSection.classList.remove('hidden');
            buatJadwalTab.classList.add('hidden');
            reportList.classList.add('hidden');
            document.getElementById('login-form').reset();
        });
    </script>
</body>
</html>
