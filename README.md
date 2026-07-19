 <!doctype html>                                                                                                                                                                                                
  <html lang="en"><head><meta charset="utf-8">                                                                                                                                                                   
  <meta name="viewport" content="width=device-width, initial-scale=1">                                                                                                                                           
  <title>FIRE Tracker — returning to app…</title></head>                                                                                                                                                         
  <body style="font-family: system-ui, sans-serif; text-align:center; padding:3rem 1.5rem;">                                                                                                                     
    <h1>Returning to FIRE Tracker…</h1>                                                                                                                                                                          
    <p>If the app doesn't open automatically, tap the button.</p>                                                                                                                                                
    <p><a id="open" href="#" style="display:inline-block;padding:.8rem 1.4rem;border-radius:999px;background:#21D0B3;color:#14132B;text-decoration:none;font-weight:600;">Open FIRE Tracker</a></p>              
    <script>                                                                                                                                                                                                     
      var target = "firetracker://bank-callback" + window.location.search;                                                                                                                                       
      document.getElementById("open").setAttribute("href", target);                                                                                                                                              
      window.location.replace(target);                                                                                                                                                                           
    </script>                                                                                                                                                                                                    
  </body></html> 
