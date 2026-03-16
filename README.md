<iframe src="https://msha.ke/debeatzgh#entertainments-hub" width="100%" height="400" frameborder="0" allowfullscreen></iframe>






<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stream Hub | AppDateGH Collab</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;700;800&display=swap');

        :root {
            --yt-red: #ff0000;
            --accent-cyan: #00f2ff;
            --wa-green: #25D366;
            --glass-card: rgba(255, 255, 255, 0.03);
        }

        body { background: #000; font-family: 'Plus Jakarta Sans', sans-serif; margin: 0; }

        /* 1. FLOATING LAUNCHER (LEFT-MIDDLE) */
        #playlist-launcher {
            position: fixed;
            left: 20px;
            top: 80%;
            transform: translateY(-50%);
            width: 50px;
            height: 50px;
            background: var(--yt-red);
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            z-index: 9999;
            box-shadow: 0 0 25px rgba(255, 0, 0, 0.4);
            animation: heartbeat 1.5s infinite;
        }

        @keyframes heartbeat {
            0%, 100% { transform: translateY(-50%) scale(1); }
            15% { transform: translateY(-50%) scale(1.1); }
        }

        /* 2. OVERLAY MODAL */
        #stream-overlay {
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.95);
            backdrop-filter: blur(25px);
            display: none;
            z-index: 10000;
            padding: 15px;
            opacity: 0;
            transition: opacity 0.5s ease;
        }

        #stream-overlay.active { display: flex; justify-content: center; align-items: center; opacity: 1; }

        .cinema-container {
            width: 100%;
            max-width: 1000px;
            height: 95vh;
            background: #0a0a0a;
            border-radius: 25px;
            border: 1px solid rgba(255,255,255,0.08);
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            position: relative;
        }

        /* 3. COLLAB FORM SECTION */
        #collab-form-area {
            background: #0f0f0f;
            padding: 30px;
            border-top: 1px solid rgba(255,255,255,0.05);
        }

        .input-group {
            background: var(--glass-card);
            border: 1px solid rgba(255,255,255,0.1);
            border-radius: 12px;
            padding: 12px 15px;
            margin-bottom: 15px;
            transition: 0.3s;
        }

        .input-group:focus-within { border-color: var(--accent-cyan); box-shadow: 0 0 15px rgba(0,242,255,0.1); }

        .input-group input, .input-group textarea {
            background: transparent; border: none; color: white; width: 100%; outline: none; font-size: 14px;
        }

        .send-btn {
            background: var(--accent-cyan);
            color: #000;
            width: 100%;
            padding: 14px;
            border-radius: 12px;
            font-weight: 800;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: 0.3s;
        }
        .send-btn:hover:not(:disabled) { background: #fff; transform: translateY(-2px); }

        /* 4. SUCCESS STATE WHATSAPP LINK */
        #wa-redirect {
            display: none;
            margin-top: 20px;
            background: rgba(37, 211, 102, 0.1);
            border: 1px solid var(--wa-green);
            padding: 15px;
            border-radius: 12px;
            text-align: center;
        }

        .wa-btn {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            background: var(--wa-green);
            color: white;
            padding: 8px 20px;
            border-radius: 8px;
            font-weight: 700;
            margin-top: 10px;
            text-decoration: none;
            font-size: 13px;
        }

        /* 5. IFRAME & CLOSE */
        #stream-frame { width: 100%; height: 450px; border: none; flex-shrink: 0; }
        .close-icon { position: absolute; top: 15px; right: 20px; color: #fff; font-size: 30px; cursor: pointer; z-index: 100; opacity: 0.6; }

        @media (max-width: 768px) {
            .cinema-container { height: 100vh; border-radius: 0; }
            #stream-frame { height: 350px; }
        }
    </style>
</head>
<body>

    <div id="playlist-launcher" onclick="toggleStream()">
        <i class="fab fa-youtube text-white text-xl"></i>
    </div>

    <div id="stream-overlay">
        <div class="cinema-container">
            <span class="close-icon" onclick="toggleStream()">&times;</span>

            <iframe id="stream-frame" src=""></iframe>

            <div id="collab-form-area">
                <div class="text-center mb-6">
                    <h3 class="text-white font-bold text-xl flex justify-center items-center gap-3">
                        <i class="fas fa-handshake text-cyan-400"></i> Collaboration Node
                    </h3>
                    <p class="text-gray-500 text-[10px] uppercase tracking-widest mt-1">Direct Link to: debeatz4@gmail.com</p>
                </div>
                
                <form id="collab-form" action="https://formspree.io/f/mqakpppq" method="POST">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div class="input-group">
                            <input type="text" name="name" placeholder="Full Name / Brand" required>
                        </div>
                        <div class="input-group">
                            <input type="email" name="email" placeholder="Your Email Address" required>
                        </div>
                    </div>
                    
                    <div class="input-group">
                        <textarea name="message" placeholder="Proposal: How would you like to collaborate on the Entertainment Repo?" rows="4" required></textarea>
                    </div>
                    
                    <button type="submit" id="submit-btn" class="send-btn">Transmit Proposal</button>
                    
                    <div id="wa-redirect">
                        <p class="text-white text-sm font-bold">Proposal Sent Successfully! 🚀</p>
                        <p class="text-gray-400 text-[11px] mt-1">If my email reply is delayed, feel free to reach out directly for a faster response.</p>
                        <a href="https://wa.me/233270201181?text=Hi%20AppDateGH,%20I%20just%20sent%20a%20collaboration%20proposal%20through%20your%20repo%20portal." class="wa-btn" target="_blank">
                            <i class="fab fa-whatsapp"></i> Chat on WhatsApp
                        </a>
                    </div>
                </form>
            </div>
        </div>
    </div>

    <script>
        const overlay = document.getElementById('stream-overlay');
        const frame = document.getElementById('stream-frame');
        const repoUrl = "https://debeatzgh1.github.io/appdategh/";
        const form = document.getElementById('collab-form');
        const waBox = document.getElementById('wa-redirect');
        const btn = document.getElementById('submit-btn');

        function toggleStream() {
            if (overlay.style.display === 'flex') {
                overlay.classList.remove('active');
                setTimeout(() => { overlay.style.display = 'none'; frame.src = ""; }, 400);
                document.body.style.overflow = 'auto';
            } else {
                overlay.style.display = 'flex';
                setTimeout(() => overlay.classList.add('active'), 10);
                frame.src = repoUrl;
                document.body.style.overflow = 'hidden';
            }
        }

        // Formspree Handling
        async function handleSubmit(event) {
            event.preventDefault();
            btn.disabled = true;
            btn.innerText = "Transmitting...";
            
            const data = new FormData(event.target);
            
            fetch(event.target.action, {
                method: form.method,
                body: data,
                headers: { 'Accept': 'application/json' }
            }).then(response => {
                if (response.ok) {
                    btn.style.display = 'none';
                    waBox.style.display = 'block';
                    form.reset();
                } else {
                    btn.innerText = "Retry Transmission";
                    btn.disabled = false;
                }
            }).catch(error => {
                btn.innerText = "Connection Error";
                btn.disabled = false;
            });
        }

        form.addEventListener("submit", handleSubmit);
        overlay.onclick = (e) => { if (e.target === overlay) toggleStream(); };
    </script>
</body>
</html>


<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>YouTube Playlist Modal</title>

<style>
/* Floating Button */
.yt-float-btn {
  position: fixed;
  right: 14px;
  top: 90%;
  transform: translateY(-50%);
  background: #ff0000;
  color: #fff;
  padding: 10px 14px;
  border-radius: 999px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  z-index: 9999;
  box-shadow: 0 8px 20px rgba(0,0,0,.35);
  transition: transform .25s ease;
}
.yt-float-btn:hover {
  transform: translateY(-50%) scale(1.05);
}

/* Modal Overlay */
#yt-modal {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,.8);
  z-index: 100000;
}

/* Modal Box */
.yt-modal-box {
  width: 96%;
  height: 92%;
  margin: 3% auto;
  background: #000;
  border-radius: 18px;
  overflow: hidden;
  position: relative;
}

/* Close Button */
.yt-close {
  position: absolute;
  top: 10px;
  right: 14px;
  font-size: 28px;
  color: #fff;
  cursor: pointer;
  z-index: 10;
}

/* Iframe */
.yt-frame {
  width: 100%;
  height: 100%;
  border: none;
}
</style>
</head>

<body>

<!-- Floating Button -->
<div class="yt-float-btn" onclick="openYT()">
▶ Watch Playlist
</div>

<!-- Modal -->
<div id="yt-modal">
  <div class="yt-modal-box">
    <span class="yt-close" onclick="closeYT()">✖</span>

    <iframe
      class="yt-frame"
      src=""
      allow="autoplay; encrypted-media; fullscreen"
      allowfullscreen>
    </iframe>
  </div>
</div>

<script>
function openYT() {
  const modal = document.getElementById("yt-modal");
  const iframe = modal.querySelector("iframe");

  iframe.src =
    "https://www.youtube.com/embed/videoseries?list=PLMOQxjh_hNfRbNjMEMpG_wBsf4NODJGEG&autoplay=1";

  modal.style.display = "block";
}

function closeYT() {
  const modal = document.getElementById("yt-modal");
  const iframe = modal.querySelector("iframe");

  iframe.src = "";
  modal.style.display = "none";
}
</script>

</body>
</html>
