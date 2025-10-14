<!-- Full updated HTML snippet (works in regular HTML pages) -->
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Saran — Portfolio Header</title>
  <style>
    body { font-family: system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial; margin: 24px; color: #0f172a; }
    .center { text-align: center; }
    .badges img { margin: 6px 6px; vertical-align: middle; }
    .stats { display:flex; gap:18px; justify-content:center; align-items:center; margin-top:12px; flex-wrap:wrap; }
    .stats img { height:150px; border-radius:8px; box-shadow: 0 6px 18px rgba(2,6,23,0.08); }
    .contrib { margin-top:14px; max-width:900px; }
  </style>
</head>
<body>

  <h1 class="center">Hey 👋 What's Up? I'm Saran</h1>

  <div class="center">
    <!-- Tech Stack Icons -->
    <img src="https://skillicons.dev/icons?i=js,ts,react,nodejs,express,mongodb,postgresql,mysql,laravel,nextjs,tailwind,docker,aws,py"
         height="60" alt="tech stack logos" />
  </div>

  <div class="center badges" style="margin-top:12px;">
    <!-- Social Media -->
    <a href="https://www.linkedin.com/in/kalaithasan-saran/" target="_blank" rel="noopener">
      <img src="https://img.shields.io/static/v1?message=LinkedIn&logo=linkedin&label=&color=0077B5&logoColor=white&labelColor=&style=for-the-badge"
           height="25" alt="linkedin logo" />
    </a>
    <a href="mailto:sarankalaithasan@gmail.com" target="_blank" rel="noopener">
      <img src="https://img.shields.io/static/v1?message=Gmail&logo=gmail&label=&color=D14836&logoColor=white&labelColor=&style=for-the-badge"
           height="25" alt="gmail logo" />
    </a>
    <a href="https://github.com/11saran" target="_blank" rel="noopener">
      <img src="https://img.shields.io/static/v1?message=GitHub&logo=github&label=&color=181717&logoColor=white&labelColor=&style=for-the-badge"
           height="25" alt="github logo" />
    </a>
    <a href="https://my-portfolio-ten-omega-28.vercel.app" target="_blank" rel="noopener">
      <img src="https://img.shields.io/static/v1?message=Portfolio&logo=vercel&label=&color=000000&logoColor=white&labelColor=&style=for-the-badge"
           height="25" alt="portfolio logo" />
    </a>
  </div>

  <!-- GitHub Stats (streak + trophy) with JS fallback to try multiple providers -->
  <div class="stats" aria-hidden="false" role="img" style="margin-top:16px;">
    <!-- Trophy (static) -->
    <img src="https://github-profile-trophy.vercel.app?username=11saran&theme=dracula&column=-1&row=1&margin-w=8&margin-h=8&no-bg=false&no-frame=false&order=4"
         alt="trophy graph" id="trophy" />

    <!-- Streak image: we will set this via JS to support fallbacks -->
    <img src="" alt="streak graph" id="streak" />
  </div>

  <!-- Contribution graph -->
  <div class="contrib center">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/11saran/11saran/output/pacman-contribution-graph-dark.svg">
      <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/11saran/11saran/output/pacman-contribution-graph.svg">
      <img alt="pacman contribution graph" src="https://raw.githubusercontent.com/11saran/11saran/output/pacman-contribution-graph.svg" style="max-width:100%;" />
    </picture>
  </div>

  <script>
    (function () {
      // List of candidate streak endpoints (tries in order)
      // 1) Primary common endpoint
      // 2) demolab endpoint (if available)
      // 3) simple fallback badge (not streak but better than broken)
      const username = '11saran';
      const candidates = [
        `https://github-readme-streak-stats.herokuapp.com?user=${username}&theme=dracula&hide_border=false&border_radius=5`,
        `https://streak-stats.demolab.com?user=${username}&locale=en&mode=daily&theme=dracula&hide_border=false&border_radius=5`,
        `https://img.shields.io/badge/Contributions-See%20GitHub-181717?logo=github`
      ];

      const streakImg = document.getElementById('streak');

      // Try each URL and pick the first that loads successfully
      let tried = 0;
      function tryNext() {
        if (tried >= candidates.length) {
          // last resort: show a descriptive placeholder image (data URI)
          streakImg.src = 'data:image/svg+xml;utf8,' + encodeURIComponent(
            `<svg xmlns="http://www.w3.org/2000/svg" width="400" height="150">
               <rect width="100%" height="100%" fill="#0b1220"/>
               <text x="50%" y="50%" fill="#cbd5e1" font-family="Arial,Helvetica,sans-serif" font-size="16" text-anchor="middle" dominant-baseline="middle">
                 Streak stats currently unavailable — view on GitHub
               </text>
             </svg>`
          );
          return;
        }

        const url = candidates[tried++];
        const test = new Image();
        // prevent caching issues by adding a small timestamp for testing only
        test.onload = function () {
          // if this loaded and has non-zero size, use it
          if (test.width > 0 && test.height > 0) {
            streakImg.src = url;
          } else {
            tryNext();
          }
        };
        test.onerror = function () {
          tryNext();
        };
        // Start load
        test.src = url + (url.indexOf('?') === -1 ? '?_=' + Date.now() : '&_=' + Date.now());
      }

      tryNext();
    })();
  </script>

</body>
</html>
