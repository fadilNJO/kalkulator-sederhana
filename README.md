<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Praktik Mandiri - Halaman Web Sederhana</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
            background: white;
            border-radius: 15px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            overflow: hidden;
            transform: translateY(0);
            transition: transform 0.3s ease;
        }

        .container:hover {
            transform: translateY(-5px);
        }

        .header {
            background: linear-gradient(45deg, #ff6b6b, #ffa500);
            color: white;
            padding: 40px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .header::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: repeating-linear-gradient(
                45deg,
                transparent,
                transparent 10px,
                rgba(255,255,255,0.1) 10px,
                rgba(255,255,255,0.1) 20px
            );
            animation: slidePattern 20s linear infinite;
        }

        @keyframes slidePattern {
            0% { transform: translateX(-50px); }
            100% { transform: translateX(50px); }
        }

        .header h1 {
            font-size: 3em;
            margin-bottom: 10px;
            position: relative;
            z-index: 1;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .header p {
            font-size: 1.2em;
            position: relative;
            z-index: 1;
            opacity: 0.9;
        }

        .content {
            padding: 40px;
        }

        .section {
            margin-bottom: 40px;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 0.8s ease forwards;
        }

        .section:nth-child(2) { animation-delay: 0.2s; }
        .section:nth-child(3) { animation-delay: 0.4s; }
        .section:nth-child(4) { animation-delay: 0.6s; }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .section h2 {
            color: #667eea;
            font-size: 2.2em;
            margin-bottom: 20px;
            position: relative;
            padding-bottom: 10px;
        }

        .section h2::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 60px;
            height: 3px;
            background: linear-gradient(45deg, #ff6b6b, #ffa500);
            border-radius: 2px;
        }

        .section p {
            font-size: 1.1em;
            margin-bottom: 20px;
            color: #555;
            text-align: justify;
        }

        .image-gallery {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }

        .image-placeholder {
            height: 200px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.1em;
            font-weight: bold;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.3);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            cursor: pointer;
        }

        .image-placeholder:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
        }

        .button-container {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
            margin: 30px 0;
        }

        .btn {
            padding: 15px 30px;
            border: none;
            border-radius: 25px;
            font-size: 1em;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            position: relative;
            overflow: hidden;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.5s;
        }

        .btn:hover::before {
            left: 100%;
        }

        .btn-primary {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            box-shadow: 0 4px 15px rgba(102, 126, 234, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(102, 126, 234, 0.4);
        }

        .btn-secondary {
            background: linear-gradient(45deg, #ff6b6b, #ffa500);
            color: white;
            box-shadow: 0 4px 15px rgba(255, 107, 107, 0.3);
        }

        .btn-secondary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(255, 107, 107, 0.4);
        }

        .btn-success {
            background: linear-gradient(45deg, #4ecdc4, #44a08d);
            color: white;
            box-shadow: 0 4px 15px rgba(78, 205, 196, 0.3);
        }

        .btn-success:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(78, 205, 196, 0.4);
        }

        .interactive-demo {
            background: #f8f9fa;
            padding: 30px;
            border-radius: 12px;
            margin: 30px 0;
            border-left: 5px solid #667eea;
        }

        .color-changer {
            margin: 20px 0;
        }

        .color-options {
            display: flex;
            gap: 10px;
            margin: 15px 0;
        }

        .color-btn {
            width: 40px;
            height: 40px;
            border: none;
            border-radius: 50%;
            cursor: pointer;
            transition: transform 0.2s ease;
            box-shadow: 0 2px 8px rgba(0,0,0,0.2);
        }

        .color-btn:hover {
            transform: scale(1.1);
        }

        .counter {
            background: white;
            padding: 20px;
            border-radius: 8px;
            text-align: center;
            margin: 20px 0;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        .counter-display {
            font-size: 3em;
            font-weight: bold;
            color: #667eea;
            margin: 10px 0;
        }

        .footer {
            background: #2c3e50;
            color: white;
            text-align: center;
            padding: 30px;
            font-size: 1.1em;
        }

        .hidden {
            display: none;
        }

        .fade-in {
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @media (max-width: 768px) {
            .header h1 {
                font-size: 2em;
            }
            
            .section h2 {
                font-size: 1.8em;
            }
            
            .button-container {
                justify-content: center;
            }
            
            .btn {
                flex: 1;
                min-width: 120px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header class="header">
            <h1>Selamat Datang!</h1>
            <p>Praktik Mandiri - Membuat Halaman Web Sederhana</p>
        </header>

        <main class="content">
            <section class="section">
                <h2>Tentang Halaman Ini</h2>
                <p>
                    Halaman web ini dibuat sebagai contoh praktik mandiri yang menggabungkan HTML, CSS, dan JavaScript. 
                    Di sini Anda akan melihat berbagai elemen seperti heading, paragraf, gambar, dan tombol yang telah 
                    distilisasi dengan CSS dan diberi interaktivitas menggunakan JavaScript.
                </p>
                <p>
                    Setiap elemen pada halaman ini dirancang untuk memberikan pengalaman visual yang menarik sekaligus 
                    mendemonstrasikan kemampuan dasar pengembangan web modern.
                </p>
            </section>

            <section class="section">
                <h2>Galeri Gambar</h2>
                <p>Berikut adalah contoh penempatan gambar dalam layout grid responsif:</p>
                <div class="image-gallery">
                    <div class="image-placeholder" onclick="changeImageColor(this)">
                        🖼️ Gambar 1<br><small>Klik untuk mengubah warna</small>
                    </div>
                    <div class="image-placeholder" onclick="changeImageColor(this)">
                        🎨 Gambar 2<br><small>Klik untuk mengubah warna</small>
                    </div>
                    <div class="image-placeholder" onclick="changeImageColor(this)">
                        📸 Gambar 3<br><small>Klik untuk mengubah warna</small>
                    </div>
                    <div class="image-placeholder" onclick="changeImageColor(this)">
                        🌟 Gambar 4<br><small>Klik untuk mengubah warna</small>
                    </div>
                </div>
            </section>

            <section class="section">
                <h2>Tombol Interaktif</h2>
                <p>Cobalah berbagai tombol di bawah ini untuk melihat interaktivitas JavaScript:</p>
                
                <div class="button-container">
                    <button class="btn btn-primary" onclick="showAlert('Halo! Ini adalah pesan dari tombol pertama!')">
                        Tampilkan Pesan
                    </button>
                    <button class="btn btn-secondary" onclick="toggleVisibility('hiddenText')">
                        Tampilkan/Sembunyikan Teks
                    </button>
                    <button class="btn btn-success" onclick="changeBackgroundColor()">
                        Ubah Warna Latar
                    </button>
                </div>

                <div id="hiddenText" class="hidden">
                    <p style="margin-top: 20px; padding: 15px; background: #e8f5e8; border-radius: 8px; border-left: 4px solid #4ecdc4;">
                        🎉 <strong>Selamat!</strong> Anda berhasil menampilkan teks tersembunyi ini menggunakan JavaScript!
                    </p>
                </div>
            </section>

            <section class="section">
                <h2>Demo Interaktif</h2>
                <div class="interactive-demo">
                    <h3>Penghitung Sederhana</h3>
                    <div class="counter">
                        <div class="counter-display" id="counterValue">0</div>
                        <div class="button-container">
                            <button class="btn btn-primary" onclick="incrementCounter()">Tambah (+)</button>
                            <button class="btn btn-secondary" onclick="decrementCounter()">Kurang (-)</button>
                            <button class="btn btn-success" onclick="resetCounter()">Reset</button>
                        </div>
                    </div>

                    <div class="color-changer">
                        <h3>Pengubah Warna Teks</h3>
                        <p id="colorText">Klik salah satu warna di bawah untuk mengubah warna teks ini!</p>
                        <div class="color-options">
                            <button class="color-btn" style="background: #ff6b6b;" onclick="changeTextColor('#ff6b6b')"></button>
                            <button class="color-btn" style="background: #4ecdc4;" onclick="changeTextColor('#4ecdc4')"></button>
                            <button class="color-btn" style="background: #45b7d1;" onclick="changeTextColor('#45b7d1')"></button>
                            <button class="color-btn" style="background: #f7b731;" onclick="changeTextColor('#f7b731')"></button>
                            <button class="color-btn" style="background: #5f27cd;" onclick="changeTextColor('#5f27cd')"></button>
                            <button class="color-btn" style="background: #00d2d3;" onclick="changeTextColor('#00d2d3')"></button>
                        </div>
                    </div>
                </div>
            </section>
        </main>

        <footer class="footer">
            <p>© 2024 Praktik Mandiri Web Development | Dibuat dengan ❤️ menggunakan HTML, CSS & JavaScript</p>
        </footer>
    </div>

    <script>
        // Counter functionality
        let counterValue = 0;

        function incrementCounter() {
            counterValue++;
            updateCounterDisplay();
        }

        function decrementCounter() {
            counterValue--;
            updateCounterDisplay();
        }

        function resetCounter() {
            counterValue = 0;
            updateCounterDisplay();
        }

        function updateCounterDisplay() {
            document.getElementById('counterValue').textContent = counterValue;
            document.getElementById('counterValue').className = 'counter-display fade-in';
        }

        // Alert functionality
        function showAlert(message) {
            alert(message);
        }

        // Toggle visibility
        function toggleVisibility(elementId) {
            const element = document.getElementById(elementId);
            if (element.classList.contains('hidden')) {
                element.classList.remove('hidden');
                element.classList.add('fade-in');
            } else {
                element.classList.add('hidden');
                element.classList.remove('fade-in');
            }
        }

        // Background color changer
        const backgroundColors = [
            'linear-gradient(135deg, #667eea 0%, #764ba2 100%)',
            'linear-gradient(135deg, #f093fb 0%, #f5576c 100%)',
            'linear-gradient(135deg, #4facfe 0%, #00f2fe 100%)',
            'linear-gradient(135deg, #43e97b 0%, #38f9d7 100%)',
            'linear-gradient(135deg, #fa709a 0%, #fee140 100%)',
            'linear-gradient(135deg, #a8edea 0%, #fed6e3 100%)'
        ];
        let currentBgIndex = 0;

        function changeBackgroundColor() {
            currentBgIndex = (currentBgIndex + 1) % backgroundColors.length;
            document.body.style.background = backgroundColors[currentBgIndex];
        }

        // Image color changer
        const imageColors = [
            'linear-gradient(45deg, #667eea, #764ba2)',
            'linear-gradient(45deg, #ff6b6b, #ffa500)',
            'linear-gradient(45deg, #4ecdc4, #44a08d)',
            'linear-gradient(45deg, #f093fb, #f5576c)',
            'linear-gradient(45deg, #4facfe, #00f2fe)',
            'linear-gradient(45deg, #43e97b, #38f9d7)'
        ];

        function changeImageColor(element) {
            const randomColor = imageColors[Math.floor(Math.random() * imageColors.length)];
            element.style.background = randomColor;
            element.style.transform = 'scale(1.1)';
            setTimeout(() => {
                element.style.transform = 'scale(1)';
            }, 200);
        }

        // Text color changer
        function changeTextColor(color) {
            const textElement = document.getElementById('colorText');
            textElement.style.color = color;
            textElement.style.transform = 'scale(1.05)';
            setTimeout(() => {
                textElement.style.transform = 'scale(1)';
            }, 200);
        }

        // Add some dynamic effects on page load
        window.addEventListener('load', function() {
            console.log('Halaman web berhasil dimuat!');
            
            // Add welcome message after page loads
            setTimeout(() => {
                const header = document.querySelector('.header p');
                header.style.opacity = '0';
                setTimeout(() => {
                    header.textContent = 'Selamat belajar dan berkreasi! 🚀';
                    header.style.opacity = '1';
                }, 300);
            }, 2000);
        });

        // Add hover effects for sections
        document.querySelectorAll('.section').forEach(section => {
            section.addEventListener('mouseenter', function() {
                this.style.transform = 'translateX(10px)';
                this.style.transition = 'transform 0.3s ease';
            });
            
            section.addEventListener('mouseleave', function() {
                this.style.transform = 'translateX(0)';
            });
        });
    </script>
</body>
</html>
