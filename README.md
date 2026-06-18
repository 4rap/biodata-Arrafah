<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Arrafah Praeijes · 3D Pink White</title>
    <!-- Font & Icons -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,400;14..32,600;14..32,800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #fce4ec; /* soft pink base */
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            font-family: 'Inter', sans-serif;
            padding: 20px;
        }

        /* 3D card container – pink & white with depth */
        .card-3d {
            background: #ffffff;
            max-width: 720px;
            width: 100%;
            border-radius: 48px 48px 48px 48px;
            padding: 40px 36px 48px;
            box-shadow: 
                0 30px 45px -20px rgba(233, 30, 99, 0.4),
                0 20px 30px -10px rgba(0,0,0,0.08),
                inset 0 -6px 0 #f8bbd0,
                inset 0 6px 12px rgba(255,255,255,0.7);
            transform: perspective(1200px) rotateX(2deg) rotateY(-1deg) rotateZ(0.5deg);
            transition: transform 0.2s ease, box-shadow 0.2s;
            border: 1px solid rgba(255, 255, 255, 0.6);
            backdrop-filter: blur(2px);
            position: relative;
        }

        /* 3D pink accent layer (simulated depth) */
        .card-3d::before {
            content: '';
            position: absolute;
            inset: -8px -8px 8px 8px;
            border-radius: 56px;
            background: linear-gradient(145deg, #f8bbd0, #f06292);
            z-index: -1;
            transform: translateZ(-20px);
            opacity: 0.3;
            filter: blur(4px);
        }

        /* 3D pink glow */
        .card-3d::after {
            content: '';
            position: absolute;
            inset: 0;
            border-radius: 48px;
            background: radial-gradient(circle at 80% 10%, rgba(255,255,255,0.8), transparent 60%);
            pointer-events: none;
            mix-blend-mode: soft-light;
        }

        /* profile header */
        .profile-badge {
            display: flex;
            align-items: center;
            gap: 16px;
            margin-bottom: 28px;
            flex-wrap: wrap;
        }

        .avatar-3d {
            width: 80px;
            height: 80px;
            background: linear-gradient(145deg, #fce4ec, #f8bbd0);
            border-radius: 30px 30px 30px 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 34px;
            font-weight: 800;
            color: #ad1457;
            box-shadow: 
                0 16px 24px -8px rgba(233, 30, 99, 0.3),
                inset 0 -4px 0 #f06292,
                inset 0 4px 10px rgba(255,255,255,0.8);
            transform: rotate(-2deg) perspective(400px) rotateY(4deg);
            transition: transform 0.2s;
            border: 2px solid rgba(255,255,255,0.6);
        }

        .name-title {
            flex: 1;
        }

        .name-title h1 {
            font-size: 2rem;
            font-weight: 800;
            letter-spacing: -0.02em;
            color: #3e2723;
            text-shadow: 0 4px 8px rgba(233, 30, 99, 0.1);
            background: linear-gradient(135deg, #ad1457, #880e4f);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .name-title .panggilan {
            font-size: 1.1rem;
            font-weight: 600;
            color: #6d4c41;
            background: #fce4ec;
            display: inline-block;
            padding: 4px 16px;
            border-radius: 40px;
            letter-spacing: 0.3px;
            box-shadow: inset 0 -2px 0 #f8bbd0;
            backdrop-filter: blur(4px);
            -webkit-text-fill-color: #4e342e;
        }

        .info-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px 20px;
            background: #fce4ec70;
            padding: 20px 18px;
            border-radius: 36px;
            backdrop-filter: blur(4px);
            box-shadow: inset 0 2px 8px rgba(255,255,255,0.6), 0 8px 18px rgba(233,30,99,0.08);
            border: 1px solid rgba(255,255,255,0.5);
            margin-bottom: 30px;
            transform: perspective(600px) rotateX(0.5deg);
        }

        .info-item {
            display: flex;
            align-items: center;
            gap: 8px;
            font-weight: 500;
            color: #3e2723;
            background: rgba(255,255,255,0.5);
            padding: 8px 14px;
            border-radius: 60px;
            backdrop-filter: blur(2px);
            border: 1px solid rgba(255,255,255,0.6);
            box-shadow: 0 2px 6px rgba(0,0,0,0.02);
            transition: all 0.1s ease;
        }

        .info-item i {
            color: #d81b60;
            width: 22px;
            font-size: 1.1rem;
            text-shadow: 0 2px 4px rgba(233,30,99,0.2);
        }

        .info-item span {
            font-weight: 600;
            color: #880e4f;
        }

        /* project link – 3D pink white, animasi bergerak saat ditekan */
        .project-link-wrapper {
            margin: 28px 0 22px;
            display: flex;
            justify-content: center;
        }

        .project-btn {
            display: inline-flex;
            align-items: center;
            gap: 14px;
            background: #ffffff;
            padding: 18px 38px;
            border-radius: 80px;
            font-weight: 700;
            font-size: 1.3rem;
            color: #880e4f;
            text-decoration: none;
            box-shadow: 
                0 12px 20px -6px #f06292,
                0 0 0 2px rgba(255,255,255,0.5),
                inset 0 -6px 0 #f8bbd0,
                inset 0 6px 16px #ffffff;
            transform: perspective(800px) rotateX(1deg) rotateY(2deg) translateZ(4px);
            transition: all 0.15s cubic-bezier(0.2, 0.9, 0.4, 1.2);
            border: 2px solid rgba(255,255,255,0.8);
            letter-spacing: 0.5px;
            backdrop-filter: blur(2px);
            position: relative;
        }

        .project-btn i {
            font-size: 1.8rem;
            color: #d81b60;
            filter: drop-shadow(0 4px 6px rgba(233,30,99,0.3));
            transition: transform 0.2s;
        }

        .project-btn .fa-arrow-right {
            font-size: 1.5rem;
            transition: transform 0.2s;
        }

        /* animasi bergerak jika ditekan (active) */
        .project-btn:active {
            transform: perspective(800px) rotateX(3deg) rotateY(-4deg) scale(0.96) translateZ(-10px);
            box-shadow: 0 4px 8px rgba(233, 30, 99, 0.3), inset 0 2px 8px #f8bbd0;
            transition-duration: 0.06s;
            background: #fce4ec;
        }

        /* juga ada efek hover */
        .project-btn:hover {
            transform: perspective(800px) rotateX(1deg) rotateY(6deg) scale(1.02) translateZ(10px);
            box-shadow: 0 20px 28px -10px #f06292, 0 0 0 4px rgba(255,255,255,0.7);
            background: #fff5f7;
        }

        .project-btn:active i {
            transform: rotate(12deg) scale(0.9);
        }

        .project-btn:active .fa-arrow-right {
            transform: translateX(8px) scale(0.9);
        }

        /* extra info : hobby, cita2 */
        .extra-hobby {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 12px 20px;
            margin-top: 18px;
            padding-top: 16px;
            border-top: 2px dashed #f8bbd0;
        }

        .hobby-tag {
            background: #ffffffd9;
            backdrop-filter: blur(4px);
            padding: 10px 24px;
            border-radius: 60px;
            font-weight: 600;
            color: #4e342e;
            border: 1px solid white;
            box-shadow: 0 6px 14px rgba(233,30,99,0.06);
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 1rem;
        }

        .hobby-tag i {
            color: #d81b60;
        }

        .footer-caption {
            margin-top: 28px;
            text-align: center;
            font-size: 0.9rem;
            color: #795548;
            background: rgba(255,255,255,0.5);
            padding: 8px 16px;
            border-radius: 60px;
            backdrop-filter: blur(4px);
            border: 1px solid rgba(255,255,255,0.8);
            letter-spacing: 0.3px;
            display: inline-block;
            width: auto;
            margin-left: auto;
            margin-right: auto;
        }

        .footer-wrap {
            text-align: center;
        }

        /* responsive */
        @media (max-width: 540px) {
            .card-3d {
                padding: 28px 18px 32px;
            }
            .info-grid {
                grid-template-columns: 1fr;
            }
            .name-title h1 {
                font-size: 1.8rem;
            }
            .project-btn {
                padding: 14px 28px;
                font-size: 1.1rem;
            }
            .avatar-3d {
                width: 64px;
                height: 64px;
                font-size: 28px;
            }
        }

        /* 3d pink white subtle movement */
        .card-3d {
            animation: float3d 6s infinite alternate ease-in-out;
        }

        @keyframes float3d {
            0% { transform: perspective(1200px) rotateX(2deg) rotateY(-1deg) rotateZ(0.5deg) translateY(0px); }
            100% { transform: perspective(1200px) rotateX(1deg) rotateY(2deg) rotateZ(1deg) translateY(-6px); }
        }

        /* link visited tetap pink */
        .project-btn:visited {
            color: #880e4f;
        }

        .highlight-pink {
            background: #f8bbd0;
            padding: 0 6px;
            border-radius: 20px;
        }
    </style>
</head>
<body>
    <div class="card-3d">
        <!-- Avatar + Nama -->
        <div class="profile-badge">
            <div class="avatar-3d">⛵</div>
            <div class="name-title">
                <h1>Arrafah Praeijes</h1>
                <div class="panggilan"><i class="fas fa-heart" style="color:#d81b60; margin-right: 8px;"></i> arap</div>
            </div>
        </div>

        <!-- Data diri grid -->
        <div class="info-grid">
            <div class="info-item"><i class="fas fa-map-pin"></i> <span>Jakarta</span></div>
            <div class="info-item"><i class="fas fa-calendar-alt"></i> <span>Agustus</span> (8)</div>
            <div class="info-item"><i class="fas fa-hard-hat"></i> <span>Civil Engineer</span></div>
            <div class="info-item"><i class="fas fa-fish"></i> <span>Mancing</span> 🎣</div>
        </div>

        <!-- Project Link: Aplikasi Jajan + animasi saat ditekan -->
        <div class="project-link-wrapper">
            <a href="https://4rap.github.io/quiz/" target="_blank" class="project-btn" id="jajanLink">
                <i class="fas fa-store"></i> 
                Aplikasi Jajan
                <i class="fas fa-arrow-right"></i>
            </a>
        </div>

        <!-- penjelasan tambahan : link bisa ditekan -->
        <div style="text-align: center; margin-top: -8px; font-size: 0.95rem; color: #6d4c41; background: rgba(255,255,240,0.3); padding: 4px 14px; border-radius: 50px; backdrop-filter: blur(2px); display: inline-block; margin-left: auto; margin-right: auto; width: fit-content; border: 1px solid rgba(255,255,255,0.5);">
            <i class="fas fa-hand-pointer" style="color: #d81b60;"></i> klik link — animasi bergerak
        </div>

        <!-- Hobby & cita-cita detail (reinforce) -->
        <div class="extra-hobby">
            <span class="hobby-tag"><i class="fas fa-fish"></i> Hobby: Mancing</span>
            <span class="hobby-tag"><i class="fas fa-building"></i> Cita-cita: Civil Engineer</span>
        </div>

        <!-- footer (bulan lahir, nama panggilan) -->
        <div class="footer-wrap">
            <div class="footer-caption">
                <i class="fas fa-star" style="color: #d81b60;"></i> Lahir: Jakarta · Agustus (8) · panggilan arap
            </div>
        </div>
    </div>

    <!-- optional: menambah efek sound? tidak, hanya visual -->
    <!-- script untuk memastikan link memiliki animasi tambahan saat ditekan (sudah via css) -->
    <script>
        // tambahan sedikit interaksi: jika link ditekan, muncul feedback kecil (opsional)
        const link = document.getElementById('jajanLink');
        link.addEventListener('mousedown', function(e) {
            // animasi tambahan via class, tapi CSS sudah handle :active
            // kita tambahkan efek getaran halus pada card (hanya untuk demonstrasi)
            const card = document.querySelector('.card-3d');
            card.style.transform = 'perspective(1200px) rotateX(3deg) rotateY(-3deg) scale(0.99)';
            setTimeout(() => {
                card.style.transform = '';
            }, 120);
        });
        // pastikan setelah lepas kembali normal
        link.addEventListener('mouseup', function() {
            const card = document.querySelector('.card-3d');
            card.style.transform = '';
        });
        // jika click diluar, reset
        document.addEventListener('mouseup', function() {
            const card = document.querySelector('.card-3d');
            if (card) card.style.transform = '';
        });
    </script>
</body>
</html>
