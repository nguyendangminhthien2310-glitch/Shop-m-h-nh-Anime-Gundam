<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="utf-8" />
  <title>Đăng nhập</title>
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <style>
    :root{ --bg:#0f172a; --panel:#0b1226; --accent:#00c6ff; --danger:#ff4b6e; --text:#e6eef7 }
    *{box-sizing:border-box}
    body{
      margin:0; min-height:100vh; display:grid; place-items:center;
      font-family:Inter, Arial, sans-serif; background:linear-gradient(180deg,#071021,#071220);
      color:var(--text);
    }
    .card{
      width:320px; padding:28px; border-radius:12px;
      background:linear-gradient(180deg, rgba(255,255,255,0.03), rgba(255,255,255,0.01));
      border:1px solid rgba(255,255,255,0.04); box-shadow:0 10px 30px rgba(2,6,23,0.6);
    }
    h2{margin:0 0 8px; font-size:20px}
    p.sub{margin:0 0 18px; color:rgba(230,238,247,0.7); font-size:13px}
    input{
      width:100%; padding:10px 12px; margin:8px 0; border-radius:8px; border:1px solid rgba(255,255,255,0.06);
      background:#07111b; color:var(--text); font-size:14px;
    }
    button{
      width:100%; padding:11px; margin-top:10px; border-radius:8px; border:none; cursor:pointer;
      background:var(--accent); color:#021627; font-weight:700; letter-spacing:.6px;
    }
    .msg{ height:20px; margin-top:10px; font-size:14px; text-align:center }
    .hint{ margin-top:12px; font-size:12px; color:rgba(230,238,247,0.65); text-align:center }
  </style>
</head>
<body>
  <div class="card" role="region" aria-label="Đăng nhập">
    <h2>Đăng nhập</h2>
    <p class="sub">Nhập tài khoản để chuyển đến <code>nguyendangminhthien.html</code></p>
    <label for="user" class="sr-only">Tên đăng nhập</label>
    <input id="user" type="text" placeholder="Tên đăng nhập" autocomplete="username">
    <label for="pass" class="sr-only">Mật khẩu</label>
    <input id="pass" type="password" placeholder="Mật khẩu" autocomplete="current-password">
    <button id="btn">Đăng nhập</button>
    <div id="msg" class="msg" aria-live="polite"></div>
    <div class="hint">Tài khoản demo: <strong>admin</strong> / <strong>123456</strong></div>
  </div>
  <script>
    // ✅ Tài khoản mặc định (chỉ demo phía client)
    const VALID_USER = "admin";
    const VALID_PASS = "123456";
    document.getElementById("btn").addEventListener("click", function(){
      const u = (document.getElementById("user").value || "").trim();
      const p = document.getElementById("pass").value || "";
      const msg = document.getElementById("msg");
      if(!u || !p){
        msg.style.color = "#ffbaba"; msg.textContent = "Vui lòng nhập đầy đủ thông tin.";
        return;
      }
      // chính xác phân biệt chữ hoa/thường
      if(u === VALID_USER && p === VALID_PASS){
        msg.style.color = "#bfffcf"; msg.textContent = "Đăng nhập thành công — chuyển trang...";
        // chuyển sang trang đích (cùng thư mục)
        setTimeout(()=> { window.location.href = "ShopmohinhAnimeGundam.html"; }, 800);
      } else {
        msg.style.color = "#ffbaba"; msg.textContent = "Sai tên đăng nhập hoặc mật khẩu.";
      }
    });
    // cho phép Enter để submit
    document.addEventListener("keydown", function(e){
      if(e.key === "Enter") document.getElementById("btn").click();
    });
  </script>
</body>
</html>
