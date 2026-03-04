
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
  top: 50%;
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
