
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sleek Floating Banner</title>
    <style>
        /* Modern CSS reset for consistency */
        *, *::before, *::after {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            min-height: 200vh; /* Adds scrollable height to visualize the fixed positioning */
            background-color: #121212; /* A dark, neutral background */
            color: #fff;
        }

        /* MAIN FLOATING BANNER CONTAINER
           Fixed to the top center of the screen
        */
        #sleek-floating-banner {
            position: fixed;
            top: 20px; /* Slight offset from the top border */
            left: 50%;
            transform: translateX(-50%); /* Centers horizontally */
            width: 340px; /* Compact, friendly width for desktop/mobile */
            height: 52px;
            background: rgba(30, 30, 30, 0.9); /* Dark semi-transparent background */
            backdrop-filter: blur(10px); /* Modern 'glassmorphism' effect */
            -webkit-backdrop-filter: blur(10px); /* Safari support */
            border: 1px solid rgba(255, 255, 255, 0.1); /* Subtle outline */
            border-radius: 50px; /* Fully rounded edges for a sleek pill look */
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5); /* Strong shadow for depth */
            display: flex;
            align-items: center;
            justify-content: space-between; /* Icon+Text on left, button on right */
            padding: 0 6px 0 16px; /* Optimized padding for the components */
            z-index: 10000; /* Ensures it stays above all other content */
            overflow: hidden; /* Needed for the marquee slide effect */
            
            /* Entry animation */
            animation: bannerEntry 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
            opacity: 0;
            transition: all 0.3s ease;
        }

        /* Hover effect to highlight the interactive nature */
        #sleek-floating-banner:hover {
            transform: translateX(-50%) scale(1.03);
            border-color: #FF1493; /* DeepPink border highlight on hover */
        }

        /* Banner entry animation (slides in and bounces slightly) */
        @keyframes bannerEntry {
            from { top: -60px; opacity: 0; }
            to { top: 20px; opacity: 1; }
        }

        /* --- MARQUEE SLIDER STYLES --- */
        .banner-text-slider {
            flex: 1;
            height: 22px; /* Set height to constrain the text */
            overflow: hidden; /* Masks text outside the area */
            position: relative;
            margin-right: 12px;
        }

        .slide-inner {
            display: flex;
            flex-direction: column; /* Stacks text vertically for sliding */
            animation: verticalSlide 8s cubic-bezier(0.645, 0.045, 0.355, 1) infinite;
        }

        /* Text element properties */
        .slide-inner span {
            height: 22px; /* Matches parent height */
            color: rgba(255, 255, 255, 0.9); /* Slightly off-white for better readability */
            font-size: 0.8rem;
            font-weight: 600; /* Semi-bold */
            display: flex;
            align-items: center;
            gap: 8px; /* Gap for the indicator dot */
            white-space: nowrap; /* Prevents text wrapping */
        }

        /* Color highlight for key inscriptions */
        .highlight-text {
            color: #FF1493; /* DeepPink */
        }

        /* Subtle animated dot for live status feel */
        .live-dot {
            width: 7px;
            height: 7px;
            background-color: #FF1493;
            border-radius: 50%;
            box-shadow: 0 0 10px rgba(255, 20, 147, 0.8);
            animation: pulseDot 1.5s infinite;
        }

        /* Pulse animation for the live dot */
        @keyframes pulseDot {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.3; transform: scale(1.2); }
        }

        /* Vertical Slide Keyframes:
           4 states (3 texts + return to 1). 
           Uses percentages to control pause duration at each state.
        */
        @keyframes verticalSlide {
            0%, 22% { transform: translateY(0); } /* Pauses on Text 1 */
            33%, 55% { transform: translateY(-22px); } /* Slides to and Pauses on Text 2 */
            66%, 88% { transform: translateY(-44px); } /* Slides to and Pauses on Text 3 */
            100% { transform: translateY(0); } /* Loops back to Text 1 smoothly */
        }

        /* --- BUTTON STYLES --- */
        .launch-btn {
            background-color: #FF1493; /* Vibrant DeepPink for main color */
            color: #fff;
            padding: 9px 20px;
            border-radius: 25px; /* Rounded pill style to match banner */
            font-size: 0.75rem;
            font-weight: 900; /* Extra bold text for contrast */
            border: none;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 1px;
            text-decoration: none; /* Removes underline for <a> tags */
            display: flex;
            align-items: center;
            gap: 6px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(255, 20, 147, 0.3); /* Soft DeepPink glow */
        }

        /* Button interaction effects */
        .launch-btn:hover {
            background-color: #ff50ac; /* Lighter DeepPink on hover */
            transform: translateY(-1px);
            box-shadow: 0 6px 20px rgba(255, 20, 147, 0.5); /* Stronger DeepPink glow */
        }

        .launch-btn:active {
            transform: translateY(1px) scale(0.98); /* Click interaction feedback */
        }

        /* --- SVG ICON STYLE --- */
        .arrow-icon {
            width: 13px;
            height: 13px;
            fill: none;
            stroke: currentColor; /* Matches text color (#fff) */
            stroke-width: 3;
            transition: transform 0.3s ease;
        }

        /* Hover animation specifically for the icon */
        .launch-btn:hover .arrow-icon {
            transform: translateX(3px); /* Arrow nudges right on hover */
        }
    </style>
</head>
<body>

    <div id="sleek-floating-banner" onclick="openHomeLink()">
        <div class="banner-text-slider">
            <div class="slide-inner">
                <span>
                    <div class="live-dot"></div> 
                    DeBeatz<span class="highlight-text">GH</span> Resource Hub
                </span>
                <span>
                    <div class="live-dot"></div>
                    Lifestyle <span class="highlight-text">&</span> Strategy
                </span>
                <span>
                    <div class="live-dot"></div>
                    Latest updates are <span class="highlight-text">Live</span>
                </span>
            </div>
        </div>

        <button class="launch-btn" onclick="openHomeLink(event)">
            OPEN 
            <svg class="arrow-icon" viewBox="0 0 24 24" aria-hidden="true">
                <path d="M5 12h14M12 5l7 7-7 7"/>
            </svg>
        </button>
    </div>

    <script>
        /**
         * Opens the specified URL in a new tab without navigating
         * away from the current page.
         * @param {Event} e - Optional event object to prevent bubbling.
         */
        function openHomeLink(e) {
            // Check if event exists and stop propagation so clicking the button
            // doesn't also trigger the banner's onclick.
            if (e && e.stopPropagation) {
                e.stopPropagation();
            }
            
            // window.open(url, '_blank') opens in a new tab.
            window.open("https://debeatzgh1.github.io/appdategh", "_blank");
        }
    </script>

</body>
</html>




<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeBeatzGH | Media Hub</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;800&display=swap');

        :root {
            --yt-red: #FF0000;
            --glass-bg: rgba(15, 15, 15, 0.7);
            --card-bg: rgba(255, 255, 255, 0.03);
            --border: rgba(255, 255, 255, 0.1);
        }

        body {
            background-color: #0a0a0a;
            color: #fff;
            font-family: 'Plus Jakarta Sans', sans-serif;
            margin: 0;
            overflow-x: hidden;
        }

        /* Gradient Background */
        .bg-glow {
            position: fixed;
            top: 0; left: 50%; transform: translateX(-50%);
            width: 100vw; height: 100vh;
            background: radial-gradient(circle at 50% -20%, #2a0a0a 0%, #0a0a0a 70%);
            z-index: -1;
        }

        /* --- NAV TABS --- */
        .nav-container {
            position: sticky; top: 0; z-index: 100;
            background: rgba(10, 10, 10, 0.8);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid var(--border);
        }

        .tab-link {
            position: relative;
            padding: 1.5rem 1rem;
            font-size: 0.85rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1px;
            color: #888;
            transition: 0.3s;
            cursor: pointer;
        }

        .tab-link.active { color: #fff; }
        .tab-link.active::after {
            content: '';
            position: absolute; bottom: -1px; left: 0;
            width: 100%; height: 2px;
            background: var(--yt-red);
            box-shadow: 0 0 10px var(--yt-red);
        }

        /* --- VIDEO CARDS --- */
        .video-card {
            background: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: 16px;
            overflow: hidden;
            transition: 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .video-card:hover {
            transform: translateY(-8px);
            border-color: rgba(255, 0, 0, 0.4);
            background: rgba(255, 255, 255, 0.05);
        }

        .iframe-container {
            position: relative;
            width: 100%;
            padding-bottom: 56.25%; /* 16:9 Aspect Ratio */
        }

        .iframe-container iframe {
            position: absolute; top: 0; left: 0;
            width: 100%; height: 100%;
            border: none;
        }

        /* --- CHANNEL HEADER --- */
        .channel-header {
            padding: 80px 20px 40px;
            text-align: center;
        }

        .avatar {
            width: 100px; height: 100px;
            border-radius: 50%;
            border: 3px solid var(--yt-red);
            margin: 0 auto 20px;
            box-shadow: 0 0 30px rgba(255, 0, 0, 0.2);
        }

        .sub-btn {
            background: #fff;
            color: #000;
            padding: 10px 24px;
            border-radius: 50px;
            font-weight: 800;
            font-size: 0.8rem;
            transition: 0.3s;
        }
        .sub-btn:hover { background: var(--yt-red); color: #fff; transform: scale(1.05); }

        .content-section { display: none; animation: fadeInUp 0.6s ease forwards; }
        .content-section.active { display: block; }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>

    <div class="bg-glow"></div>

    <header class="channel-header">
        <div class="avatar flex items-center justify-center bg-[#111]">
            <i class="fab fa-youtube text-4xl text-red-600"></i>
        </div>
        <h1 class="text-3xl font-extrabold tracking-tighter mb-2">DeBeatzGH</h1>
        <p class="text-gray-400 text-sm mb-6">Digital Content Strategist & Tech Enthusiast</p>
        <div class="flex justify-center gap-4">
            <a href="https://youtube.com/@debeatzgh?sub_confirmation=1" target="_blank" class="sub-btn">SUBSCRIBE</a>
            <a href="https://youtube.com/@debeatzgh/community" target="_blank" class="px-6 py-2 rounded-full border border-white/10 text-xs font-bold hover:bg-white/5 transition">VIEW COMMUNITY</a>
        </div>
    </header>

    <nav class="nav-container">
        <div class="max-w-4xl mx-auto flex justify-around">
            <div class="tab-link active" onclick="switchTab('videos', this)">Videos</div>
            <div class="tab-link" onclick="switchTab('playlist', this)">Playlist</div>
            <div class="tab-link" onclick="switchTab('community', this)">Community</div>
        </div>
    </nav>

    <main class="max-w-6xl mx-auto p-6">
        
        <section id="videos" class="content-section active">
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <div class="video-card">
                    <div class="iframe-container">
                        <iframe src="https://www.youtube.com/embed?listType=user_uploads&list=debeatzgh" allowfullscreen></iframe>
                    </div>
                    <div class="p-4">
                        <h3 class="font-bold text-sm mb-1">Latest Uploads</h3>
                        <p class="text-[10px] text-gray-500 uppercase tracking-widest">Main Channel Feed</p>
                    </div>
                </div>
            </div>
        </section>

        <section id="playlist" class="content-section">
            <div class="video-card w-full max-w-4xl mx-auto">
                <div class="iframe-container">
                    <iframe src="https://www.youtube.com/embed/videoseries?list=PLMOQxjh_hNfRbNjMEMpG_wBsf4NODJGEG" allowfullscreen></iframe>
                </div>
                <div class="p-6 flex justify-between items-center">
                    <div>
                        <h2 class="text-xl font-bold">Featured Playlist</h2>
                        <p class="text-sm text-gray-400">Curated tech & creative series</p>
                    </div>
                    <a href="https://youtube.com/playlist?list=PLMOQxjh_hNfRbNjMEMpG_wBsf4NODJGEG" target="_blank" class="text-red-500 text-xs font-bold hover:underline">OPEN IN YOUTUBE</a>
                </div>
            </div>
        </section>

        <section id="community" class="content-section">
            <div class="max-w-2xl mx-auto space-y-6">
                <div class="p-8 border border-dashed border-white/20 rounded-3xl text-center">
                    <i class="fas fa-users text-4xl text-gray-700 mb-4"></i>
                    <h3 class="text-lg font-bold mb-2">YouTube Community Feed</h3>
                    <p class="text-sm text-gray-500 mb-6">Direct posts, polls, and updates from DeBeatzGH are hosted on YouTube's community tab.</p>
                    <a href="https://youtube.com/@debeatzgh/community" target="_blank" class="inline-block bg-white/5 border border-white/10 px-8 py-3 rounded-full text-xs font-bold hover:bg-white/10 transition">
                        GO TO COMMUNITY POSTS
                    </a>
                </div>
            </div>
        </section>

    </main>

    <script>
        function switchTab(tabId, el) {
            // Update Tab Links
            document.querySelectorAll('.tab-link').forEach(tab => tab.classList.remove('active'));
            el.classList.add('active');

            // Update Content Sections
            document.querySelectorAll('.content-section').forEach(section => section.classList.remove('active'));
            document.getElementById(tabId).classList.add('active');

            // Scroll to top of content
            window.scrollTo({ top: document.querySelector('nav').offsetTop - 20, behavior: 'smooth' });
        }
    </script>
</body>
</html>



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
            top: 90%;
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
