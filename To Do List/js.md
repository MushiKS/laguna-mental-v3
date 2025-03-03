#### Controladores del reproductor
Considerando "*tu-cancion.mp3*" como una de las canciones que descargaste.

Esto es HTML:

    <audio id="audio" src="tu-cancion.mp3"></audio>  
    <button onclick="togglePlay()">▶️ / ⏸</button>
    <input type="range" id="progress" class="slider" value="0" min="0" step="0.1">
Esto es JavaScript:

    <script>
        const audio = document.getElementById("audio");
        const progress = document.getElementById("progress");
        function togglePlay() {
            if (audio.paused) {
                audio.play();
            } else {
                audio.pause();
            }
        }
        // Actualizar slider mientras la canción avanza
        audio.addEventListener("timeupdate", () => {
            progress.value = (audio.currentTime / audio.duration) * 100;
        });
        // Permitir al usuario adelantar o retroceder
        progress.addEventListener("input", () => {
            audio.currentTime = (progress.value / 100) * audio.duration;
        });
    </script>





