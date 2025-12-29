# Mitra-Line-App

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mitra Line - Fashion Modern</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css" />
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        /* --- CSS HEADER (Bagian 1) --- */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Poppins', 'Segoe UI', sans-serif; background-color: #f4f7f6; }

        .main-header {
            width: 100%; height: 200px; display: flex; justify-content: center;
            align-items: center; background: #ffffff; position: relative;
            overflow: hidden; box-shadow: 0 10px 30px rgba(0,0,0,0.05);
            border-bottom: 4px solid #ececec;
        }
        .main-header::before, .main-header::after {
            content: ""; position: absolute; width: 300px; height: 300px;
            border-radius: 50%; background: linear-gradient(135deg, rgba(76, 175, 80, 0.05), rgba(33, 150, 243, 0.05));
            z-index: 0;
        }
        .main-header::before { top: -150px; left: -100px; }
        .main-header::after { bottom: -150px; right: -100px; }

        .title {
            font-size: clamp(2.5rem, 8vw, 4.5rem); font-weight: 700;
            letter-spacing: -1px; z-index: 1; text-align: center;
            animation: colorChange 12s infinite;
        }
        @keyframes colorChange {
            0%, 100% { color: #90EE90; } 16% { color: #006400; }
            33% { color: #ADD8E6; } 50% { color: #00008B; }
            66% { color: #FFB6C1; } 83% { color: #8B0000; }
        }

        /* --- CSS BODY & MENU (Bagian 2) --- */
        :root {
            --primary-color: #ffffff;
            --shadow-color: rgba(0, 0, 0, 0.3);
            --ml-primary: #2563eb;
            --ml-text: #334155;
            --ml-bg: #ffffff;
            --ml-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
            --ml-radius: 12px;
        }

        .main-container { width: 100%; max-width: 1200px; margin: 0 auto; padding: 20px; }

        .swiper { width: 100%; border-radius: 15px; box-shadow: 0 10px 30px var(--shadow-color); overflow: hidden; background: #fff; margin-bottom: 30px; }
        .swiper-slide img { display: block; width: 100%; height: auto; object-fit: contain; }

        .ml-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 15px; padding: 10px 0; }
        @media (min-width: 768px) { .ml-grid { grid-template-columns: repeat(6, 1fr); } }

        .ml-item {
            background: var(--ml-bg); border-radius: var(--ml-radius); padding: 15px 10px;
            text-align: center; text-decoration: none !important; color: var(--ml-text) !important;
            box-shadow: var(--ml-shadow); transition: all 0.3s ease; border: 1px solid #e2e8f0;
            display: flex; flex-direction: column; align-items: center; justify-content: center; cursor: pointer;
        }
        .ml-item:hover { transform: translateY(-3px); border-color: var(--ml-primary); }
        .ml-icon svg { width: 28px; height: 28px; fill: var(--ml-primary); margin-bottom: 8px; }
        .ml-text { font-size: 14px; font-weight: 600; }

        /* Modal Styles */
        .ml-modal { display: none; position: fixed; z-index: 99999; left: 0; top: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); backdrop-filter: blur(3px); align-items: center; justify-content: center; }
        .ml-modal.active { display: flex; }
        .ml-modal-content { background: #fff; width: 90%; max-width: 500px; border-radius: 16px; padding: 25px; position: relative; animation: slideUp 0.3s ease-out; max-height: 80vh; overflow-y: auto; }
        @keyframes slideUp { from { transform: translateY(20px); opacity: 0; } to { transform: translateY(0); opacity: 1; } }
        .ml-close { position: absolute; top: 15px; right: 20px; font-size: 28px; cursor: pointer; color: #aaa; }
        .ml-cat-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
        .ml-cat-btn, .ml-soc-btn { display: flex; flex-direction: column; align-items: center; padding: 12px; background: #f8fafc; border: 1px solid #e2e8f0; border-radius: 8px; text-decoration: none; color: #475569; font-size: 13px; transition: 0.2s; }
        .ml-cat-btn:hover, .ml-soc-btn:hover { background: var(--ml-primary); color: #fff; }
        .ml-soc-btn svg { width: 32px; height: 32px; margin-bottom: 8px; fill: var(--ml-primary); }
        .ml-soc-btn:hover svg { fill: #fff; }
        .ml-faq-item { margin-bottom: 10px; border: 1px solid #e2e8f0; border-radius: 8px; overflow: hidden; }
        .ml-faq-q { background: #f8fafc; padding: 12px 15px; cursor: pointer; font-weight: 600; display: flex; justify-content: space-between; }
        .ml-faq-a { max-height: 0; overflow: hidden; transition: max-height 0.3s ease; padding: 0 15px; font-size: 14px; color: #64748b; }
        .ml-faq-item.open .ml-faq-a { padding: 15px; max-height: 200px; }

        /* --- CSS FOOTER (Bagian 3) --- */
        footer { background-color: #f9f9f9; padding-top: 40px; border-top: 1px solid #ddd; margin-top: 40px; }
        .footer-container { max-width: 1100px; margin: 0 auto; padding: 0 20px; }
        .contact-section h3 { font-size: 1.2rem; margin-bottom: 15px; }
        .contact-item { display: flex; align-items: center; margin-bottom: 12px; text-decoration: none; color: #444; width: fit-content; }
        .contact-item i { width: 30px; font-size: 1.2rem; margin-right: 10px; }
        .legal-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; padding: 20px 0; border-top: 1px solid #eee; text-align: center; }
        .legal-link { text-decoration: none; color: #666; font-size: 0.9rem; }
        .copyright-bar { background-color: #1b5e20; color: #000000; text-align: center; padding: 15px 0; font-weight: bold; }
        @media (max-width: 600px) { .legal-grid { grid-template-columns: 1fr; } .main-header { height: 150px; } }
    </style>
</head>
<body>

    <header class="main-header">
        <h1 class="title">Mitra Line</h1>
    </header>

    <div class="main-container">
        
        <div class="swiper">
            <div class="swiper-wrapper">
                <div class="swiper-slide"><img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgCuHQ0RbijXWvsORUx_gPvMB6qw27dLHy59AawiKZSlwgq7PdfAOPeKIV3qeKtFBFYzibeSiYxX0YZz-HdHhn-GZr9abeSyVpgFe8GVARWUpfdpwV4cZUW2VzaC_yM_PoZepxmp6n85MQKFkcngiDlD99ODPPssP8_MVrVyJP1aC6QSoCar4jMR30ReA4/s720/1000104457.webp" alt="Slide 1"></div>
                <div class="swiper-slide"><img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjbE0wrbGe3EImYiNWapec5OcakPY8t5cR5mXMhA9PEjlr9s03HkYQs3Klm2NZ9-9HR_epo0hhaJmO0vDsgyn_unNMSe0hJiJrCO2CTcriM004ysiBC3RrDTPIbfXjfkJhSaMxaTQlV0YyOpEahEHclZn3JOlQRvLF50h7jqVwZ61xgjNIfeYgEyXa-J3Q/s720/1000104456.webp" alt="Slide 2"></div>
                <div class="swiper-slide"><img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhWxsiQZ688yoIRDnx8suLdACDN2uZPIG4aNnsXv6Zbblne0TXAsufXEjgux-i2oMyCCF2yCr7mja_AAXgP0Ps2a0VUiXlQHbzZhhiWoHEcuVR6hLgGMwbuN_nR9YB1b4fvzYIIzmtHC3wPmoKQHsmWPFudNm-7R83xwlYTN9DH6mqrZiy8ZpxfFW3d9IU/s720/1000104455.webp" alt="Slide 3"></div>
                <div class="swiper-slide"><img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg35eD4pMP7PV3IYhjfPDZJbD9MHvu86c-oTKEdeWGD40fz3zhRCvVWbLMqF9lzEq1VDJA7ugVt-0sRl7dZYA81wDJs2AlSOQtu2GId_2ShJ05Dylf200__y32M2BveDoDH0HI7uN5xee_Upkh9rBDonVcY7mHg7HQudxqpdq3Y0RBdcX0OAwKA_pckPI4/s720/1000104454.webp" alt="Slide 4"></div>
            </div>
            <div class="swiper-pagination"></div>
            <div class="swiper-button-prev"></div>
            <div class="swiper-button-next"></div>
        </div>

        <div class="ml-grid">
            <a href="https://www.mitraline.id" class="ml-item">
                <div class="ml-icon"><svg viewBox="0 0 24 24"><path d="M10 20v-6h4v6h5v-8h3L12 3 2 12h3v8z"/></svg></div>
                <div class="ml-text">Home</div>
            </a>
            <a href="https://mitraline.id/toko-baju-online-murah" class="ml-item">
                <div class="ml-icon"><svg viewBox="0 0 24 24"><path d="M20 4H4v2h16V4zm1 10v-2l-1-5H4l-1 5v2h1v6h10v-6h4v6h2v-6h1zm-9 4H6v-4h6v4z"/></svg></div>
                <div class="ml-text">Toko</div>
            </a>
            <div class="ml-item" onclick="openMlModal('modal-kategori')">
                <div class="ml-icon"><svg viewBox="0 0 24 24"><path d="M4 11h5V5H4v6zm0 7h5v-6H4v6zm6 0h5v-6h-5v6zm6 0h5v-6h-5v6zm-6-7h5V5h-5v6zm6-6v6h5V5h-5z"/></svg></div>
                <div class="ml-text">Kategori</div>
            </div>
            <a href="https://mitraline.id/contact" class="ml-item">
                <div class="ml-icon"><svg viewBox="0 0 24 24"><path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg></div>
                <div class="ml-text">Contact</div>
            </a>
            <a href="https://wa.me/c/62817184949" class="ml-item" target="_blank">
                <div class="ml-icon"><svg viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 14H9v-2h2v2zm0-4H9V7h2v5z"/></svg></div>
                <div class="ml-text">Catalog</div>
            </a>
            <div class="ml-item" onclick="openMlModal('modal-faq')">
                <div class="ml-icon"><svg viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 17h-2v-2h2v2zm2.07-7.75l-.9.92C13.45 12.9 13 13.5 13 15h-2v-.5c0-1.1.45-2.1 1.17-2.83l1.24-1.26c.37-.36.59-.86.59-1.41 0-1.1-.9-2-2-2s-2 .9-2 2H8c0-2.21 1.79-4 4-4s4 1.79 4 4c0 .88-.36 1.68-.93 2.25z"/></svg></div>
                <div class="ml-text">Faq</div>
            </div>
            <div class="ml-item" onclick="openMlModal('modal-medsos')">
                <div class="ml-icon"><svg viewBox="0 0 24 24"><path d="M18 16.08c-.76 0-1.44.3-1.96.77L8.91 12.7c.05-.23.09-.46.09-.7s-.04-.47-.09-.7l7.05-4.11c.54.5 1.25.81 2.04.81 1.66 0 3-1.34 3-3s-1.34-3-3-3-3 1.34-3 3c0 .24.04.47.09.7L8.04 9.81C7.5 9.31 6.79 9 6 9c-1.66 0-3 1.34-3 3s1.34 3 3 3c.79 0 1.5-.31 2.04-.81l7.12 4.16c-.05.21-.08.43-.08.65 0 1.61 1.31 2.92 2.92 2.92 1.61 0 2.92-1.31 2.92-2.92s-1.31-2.92-2.92-2.92z"/></svg></div>
                <div class="ml-text">Media Social</div>
            </div>
        </div>

    </div>

    <div id="modal-kategori" class="ml-modal" onclick="closeMlModal(event, this)">
        <div class="ml-modal-content">
            <span class="ml-close" onclick="closeMlModalBtn('modal-kategori')">&times;</span>
            <h3 class="ml-modal-title">Pilih Kategori Fashion</h3>
            <div class="ml-cat-grid">
                <a href="https://mitraline.id/topik/fashion/fashion" class="ml-cat-btn">Fashion</a>
                <a href="https://mitraline.id/topik/fashion/fesyen" class="ml-cat-btn">Fesyen</a>
                <a href="https://mitraline.id/topik/fashion/hoodie" class="ml-cat-btn">Hoodie</a>
                <a href="https://mitraline.id/topik/fashion/model-celana" class="ml-cat-btn">Model Celana</a>
                <a href="https://mitraline.id/topik/fashion/model-hoodie" class="ml-cat-btn">Model Hoodie</a>
                <a href="https://mitraline.id/topik/fashion/model-jaket" class="ml-cat-btn">Model Jaket</a>
                <a href="https://mitraline.id/topik/fashion/model-sepatu" class="ml-cat-btn">Model Sepatu</a>
                <a href="https://mitraline.id/topik/fashion/parfum" class="ml-cat-btn">Parfum</a>
                <a href="https://mitraline.id/topik/fashion/bisnis-sandal" class="ml-cat-btn">Sandal</a>
                <a href="https://mitraline.id/topik/fashion/sweater" class="ml-cat-btn">Sweater</a>
                <a href="https://mitraline.id/topik/fashion/toko-online" class="ml-cat-btn">Toko Online</a>
            </div>
        </div>
    </div>

    <div id="modal-faq" class="ml-modal" onclick="closeMlModal(event, this)">
        <div class="ml-modal-content">
            <span class="ml-close" onclick="closeMlModalBtn('modal-faq')">&times;</span>
            <h3 class="ml-modal-title">FAQ - Mitra Line</h3>
            <div class="ml-faq-container">
                <div class="ml-faq-item">
                    <div class="ml-faq-q" onclick="toggleFaq(this)">Apa itu Mitra Line?<span>+</span></div>
                    <div class="ml-faq-a">Mitra Line adalah pusat fashion online terpercaya yang menyediakan berbagai kebutuhan fashion modern.</div>
                </div>
                <div class="ml-faq-item">
                    <div class="ml-faq-q" onclick="toggleFaq(this)">Bagaimana cara pemesanan?<span>+</span></div>
                    <div class="ml-faq-a">Anda bisa memesan langsung melalui website pada menu Toko atau hubungi kami via WhatsApp di menu Catalog.</div>
                </div>
            </div>
        </div>
    </div>

    <div id="modal-medsos" class="ml-modal" onclick="closeMlModal(event, this)">
        <div class="ml-modal-content">
            <span class="ml-close" onclick="closeMlModalBtn('modal-medsos')">&times;</span>
            <h3 class="ml-modal-title">Hubungi Media Social</h3>
            <div class="ml-cat-grid">
                <a href="https://www.facebook.com/mitraline9" class="ml-soc-btn" target="_blank"><i class="fab fa-facebook" style="font-size: 2rem; margin-bottom: 5px;"></i> Facebook</a>
                <a href="https://instagram.com/mitraline9" class="ml-soc-btn" target="_blank"><i class="fab fa-instagram" style="font-size: 2rem; margin-bottom: 5px;"></i> Instagram</a>
                <a href="https://wa.me/628136552469" class="ml-soc-btn" target="_blank"><i class="fab fa-whatsapp" style="font-size: 2rem; margin-bottom: 5px;"></i> WhatsApp</a>
            </div>
        </div>
    </div>

    <footer>
        <div class="footer-container">
            <div class="contact-section">
                <h3>Hubungi:</h3>
                <a href="https://wa.me/628136552469" class="contact-item"><i class="fab fa-whatsapp" style="color: #25D366;"></i> WhatsApp</a>
                <a href="mailto:official@mitraline.co.id" class="contact-item"><i class="fas fa-envelope" style="color: #EA4335;"></i> Email</a>
                <a href="tel:+628561113949" class="contact-item"><i class="fas fa-phone-alt" style="color: #34A853;"></i> Telephone</a>
            </div>
            <div class="legal-grid">
                <a href="https://mitraline.id/kebijakan-privasi" class="legal-link">Kebijakan Privasi</a>
                <a href="https://mitraline.id/terms-of-use" class="legal-link">Terms of Use</a>
                <a href="https://mitraline.id/sitemap" class="legal-link">Sitemap</a>
            </div>
        </div>
        <div class="copyright-bar">©️ 2026 By Mitra Line</div>
    </footer>

    <script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>
    <script>
        const swiper = new Swiper('.swiper', {
            loop: true, autoplay: { delay: 3500 },
            pagination: { el: '.swiper-pagination', clickable: true },
            navigation: { nextEl: '.swiper-button-next', prevEl: '.swiper-button-prev' },
        });

        function openMlModal(id) {
            const m = document.getElementById(id);
            m.style.display = 'flex';
            setTimeout(() => m.classList.add('active'), 10);
            document.body.style.overflow = 'hidden';
        }

        function closeMlModalBtn(id) {
            const m = document.getElementById(id);
            m.classList.remove('active');
            setTimeout(() => m.style.display = 'none', 300);
            document.body.style.overflow = 'auto';
        }

        function closeMlModal(e, el) { if (e.target === el) closeMlModalBtn(el.id); }
        function toggleFaq(el) { el.parentElement.classList.toggle('open'); }
    </script>
</body>
</html>
