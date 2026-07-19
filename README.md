<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>FIRE Tracker — returning to app…</title>
  <style>
    body { font-family: system-ui, -apple-system, sans-serif; background:#14132B; color:#fff;
           text-align:center; padding:3rem 1.5rem; margin:0; }
    h1 { font-size:1.4rem; margin:0 0 .5rem; }
    p { color:#c9c8e0; line-height:1.5; }
    #count { font-size:2.6rem; font-weight:700; color:#21D0B3; margin:1.2rem 0; min-height:3rem; }
    a.btn { display:inline-block; margin-top:.5rem; padding:.95rem 1.6rem; border-radius:999px;
            background:#21D0B3; color:#14132B; text-decoration:none; font-weight:700; font-size:1.05rem; }
    a.alt { display:block; margin-top:1.4rem; color:#8f8fb5; font-size:.9rem; }
  </style>
</head>
<body>
  <h1>Returning to FIRE Tracker…</h1>
  <p>Handing your bank authorisation back to the app.</p>
  <div id="count"></div>
  <a id="open" class="btn" href="#">Return to FIRE Tracker</a>
  <a id="alt" class="alt" href="#">Didn't work? Tap here</a>

  <script>
    (function () {
      var search = window.location.search || "";           // ?code=...&state=...
      // Android intent:// URI — Chrome/Custom Tabs honour this and launch the app by package,
      // which a bare custom-scheme redirect is often blocked from doing without a user gesture.
      var intentUrl = "intent://bank-callback" + search +
        "#Intent;scheme=firetracker;package=com.example.firetracker;end";
      var schemeUrl = "firetracker://bank-callback" + search; // fallback for non-Android browsers

      document.getElementById("open").setAttribute("href", intentUrl);
      document.getElementById("alt").setAttribute("href", schemeUrl);

      function go() { window.location.href = intentUrl; }

      // Auto-attempt immediately, then again after a short delay (some tabs need the second nudge).
      go();
      var n = 3;
      var el = document.getElementById("count");
      el.textContent = n;
      var t = setInterval(function () {
        n -= 1;
        if (n <= 0) { clearInterval(t); el.textContent = ""; go(); }
        else { el.textContent = n; }
      }, 1000);
    })();
  </script>
</body>
</html>
