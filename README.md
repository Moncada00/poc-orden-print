<!doctype html>
<html>
<head>
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <style>
    body { font-family: Arial; padding: 16px; text-align: center; }
    .box { border: 1px solid #000; padding: 12px; border-radius: 10px; display:inline-block; max-width: 340px; }
    img { width: 260px; height: 260px; margin-top: 10px; }
    .desc { margin-top: 10px; font-size: 16px; white-space: pre-wrap; word-break: break-word; }
    @media print { button { display:none; } body { padding:0; } }
  </style>
</head>
<body>
  <div class="box">
    <h2 id="t"></h2>
    <div class="desc"><b>Descripción:</b><br><span id="d"></span></div>
    <img id="q" />
  </div>
  <div style="margin-top:12px">
    <button onclick="window.print()">Imprimir</button>
  </div>

  <script>
    const p = new URLSearchParams(location.search);
    const orden = p.get("orden") || "";
    const desc  = p.get("desc") || "";
    const qr    = p.get("qr")   || "";

    document.getElementById("t").textContent = "ORDEN " + orden;
    document.getElementById("d").textContent = desc;

    // Si no viene qr, lo generamos con orden
    const qrUrl = qr ? qr : ("https://api.qrserver.com/v1/create-qr-code/?size=300x300&data=" + encodeURIComponent(orden));
    document.getElementById("q").src = qrUrl;
  </script>
</body>
</html>
