# Photos
Simpen aja
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Frame — Penyimpanan Foto</title>
  <style>
    :root {
      --ink: #171717;
      --muted: #8a8a8a;
      --line: #e8e8e8;
      --paper: #fafafa;
      --white: #fff;
      --black: #111;
    }
    * { box-sizing: border-box; }
    body { margin: 0; background: var(--paper); color: var(--ink); font: 14px/1.5 Inter, ui-sans-serif, system-ui, sans-serif; }
    button, input { font: inherit; }
    button { cursor: pointer; border: 0; }
    .layout { min-height: 100vh; display: grid; grid-template-columns: 235px 1fr; }
    aside { padding: 28px 18px; border-right: 1px solid var(--line); background: var(--white); }
    .logo { display: flex; align-items: center; gap: 10px; padding: 0 12px 40px; font-size: 22px; font-weight: 850; letter-spacing: -1px; }
    .logo-mark { width: 30px; height: 30px; display: grid; place-items: center; border-radius: 9px; background: var(--black); color: white; font-size: 15px; }
    .nav-label { padding: 0 12px 9px; color: #aaa; font-size: 10px; font-weight: 750; letter-spacing: 1.4px; text-transform: uppercase; }
    .nav { display: grid; gap: 4px; }
    .nav button { width: 100%; padding: 11px 12px; border-radius: 9px; background: transparent; color: #777; text-align: left; }
    .nav button:hover, .nav button.active { background: #f0f0f0; color: var(--black); font-weight: 700; }
    .nav button span { display: inline-block; width: 25px; color: #999; }
    .storage { margin: 45px 10px 0; padding: 16px; border: 1px solid var(--line); border-radius: 13px; }
    .storage-top { display: flex; justify-content: space-between; margin-bottom: 10px; font-size: 12px; font-weight: 700; }
    .storage-top span { color: var(--muted); font-weight: 500; }
    .bar { height: 7px; overflow: hidden; border-radius: 9px; background: #ededed; }
    .bar div { width: 42%; height: 100%; border-radius: inherit; background: var(--black); }
    .storage small { display: block; margin-top: 9px; color: var(--muted); font-size: 11px; }
    main { min-width: 0; }
    header { height: 83px; display: flex; justify-content: space-between; align-items: center; padding: 0 42px; border-bottom: 1px solid var(--line); background: var(--white); }
    .search { width: min(390px, 42vw); position: relative; }
    .search input { width: 100%; padding: 11px 16px 11px 38px; border: 1px solid var(--line); border-radius: 9px; outline: 0; background: #fafafa; }
    .search input:focus { border-color: #999; }
    .search span { position: absolute; left: 13px; top: 9px; color: #888; font-size: 17px; }
    .account { display: flex; align-items: center; gap: 12px; }
    .account button { padding: 10px 16px; border-radius: 8px; background: var(--black); color: white; font-size: 12px; font-weight: 700; }
    .avatar { width: 34px; height: 34px; display: grid; place-items: center; border-radius: 50%; background: #dedede; font-size: 12px; font-weight: 800; }
    .content { max-width: 1320px; margin: auto; padding: 36px 42px 60px; }
    .welcome { display: flex; justify-content: space-between; align-items: end; margin-bottom: 30px; }
    h1 { margin: 0 0 5px; font-size: 32px; letter-spacing: -1.5px; }
    .welcome p { margin: 0; color: var(--muted); }
    .upload { padding: 12px 18px; border-radius: 8px; background: var(--black); color: white; font-weight: 700; }
    .upload:hover { background: #333; }
    .stats { display: grid; grid-template-columns: repeat(3, 1fr); gap: 14px; margin-bottom: 35px; }
    .stat { display: flex; align-items: center; justify-content: space-between; padding: 19px; border: 1px solid var(--line); border-radius: 13px; background: white; }
    .stat-label { color: var(--muted); font-size: 12px; }
    .stat-number { margin-top: 3px; font-size: 22px; font-weight: 800; }
    .stat-icon { width: 40px; height: 40px; display: grid; place-items: center; border-radius: 10px; background: #f0f0f0; font-size: 19px; }
    .section-head { display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px; }
    h2 { margin: 0; font-size: 20px; letter-spacing: -.5px; }
    .view-actions { display: flex; gap: 8px; }
    .view-actions button { padding: 6px 9px; border-radius: 6px; background: transparent; color: #999; }
    .view-actions button.active, .view-actions button:hover { background: #e9e9e9; color: #111; }
    .albums { display: grid; grid-template-columns: repeat(4, 1fr); gap: 14px; margin-bottom: 38px; }
    .album { overflow: hidden; border: 1px solid var(--line); border-radius: 12px; background: white; transition: .2s; }
    .album:hover { transform: translateY(-3px); box-shadow: 0 12px 25px #0000000d; }
    .album-cover { height: 120px; background-size: cover; background-position: center; filter: grayscale(1); }
    .cover-1 { background-image: url("https://images.unsplash.com/photo-1500534623283-312aade485b7?w=500&q=80"); }
    .cover-2 { background-image: url("https://images.unsplash.com/photo-1493246507139-91e8fad9978e?w=500&q=80"); }
    .cover-3 { background-image: url("https://images.unsplash.com/photo-1497366754035-f200968a6e72?w=500&q=80"); }
    .cover-4 { background-image: url("https://images.unsplash.com/photo-1506744038136-46273834b3fb?w=500&q=80"); }
    .album-info { padding: 11px 13px; }
    .album-name { font-weight: 750; }
    .album-count { color: var(--muted); font-size: 11px; }
    .photos { display: grid; grid-template-columns: repeat(4, 1fr); gap: 14px; }
    .photo { overflow: hidden; position: relative; height: 205px; border-radius: 12px; background: #ddd; }
    .photo img { width: 100%; height: 100%; object-fit: cover; filter: grayscale(1); transition: transform .35s; }
    .photo:hover img { transform: scale(1.05); }
    .photo-info { position: absolute; right: 0; bottom: 0; left: 0; padding: 28px 12px 11px; background: linear-gradient(transparent, #000b); color: white; opacity: 0; transition: opacity .2s; }
    .photo:hover .photo-info { opacity: 1; }
    .photo-info small { color: #ddd; }
    .empty { grid-column: 1 / -1; padding: 35px; border: 1px dashed #ccc; border-radius: 12px; text-align: center; color: var(--muted); }
    .toast { position: fixed; right: 25px; bottom: 25px; z-index: 4; padding: 12px 16px; border-radius: 9px; background: #111; color: white; box-shadow: 0 10px 30px #0003; transform: translateY(80px); opacity: 0; transition: .25s; }
    .toast.show { transform: translateY(0); opacity: 1; }
    @media (max-width: 900px) { .layout { grid-template-columns: 75px 1fr; } aside { padding: 22px 10px; } .logo { padding: 0 12px 38px; } .logo span:last-child, .nav-label, .nav button b, .storage { display: none; } .nav button { text-align: center; } .nav button span { width: auto; font-size: 18px; } header, .content { padding-left: 25px; padding-right: 25px; } .albums, .photos { grid-template-columns: repeat(2, 1fr); } }
    @media (max-width: 560px) { .layout { display: block; } aside { display: none; } header { height: auto; padding: 15px; gap: 13px; flex-wrap: wrap; } .search { order: 3; width: 100%; } .content { padding: 25px 15px 40px; } .welcome { align-items: start; gap: 17px; flex-direction: column; } h1 { font-size: 28px; } .stats { grid-template-columns: 1fr; gap: 9px; } .albums, .photos { grid-template-columns: repeat(2, 1fr); gap: 9px; } .album-cover { height: 95px; } .photo { height: 145px; } }
  </style>
</head>
<body>
  <div class="layout">
    <aside>
      <div class="logo"><span class="logo-mark">F</span><span>frame</span></div>
      <div class="nav-label">Menu utama</div>
      <nav class="nav">
        <button class="active" data-page="Semua foto"><span>▦</span><b>Semua foto</b></button>
        <button data-page="Favorit"><span>♡</span><b>Favorit</b></button>
        <button data-page="Dibagikan"><span>↗</span><b>Dibagikan</b></button>
        <button data-page="Sampah"><span>⌫</span><b>Sampah</b></button>
      </nav>
      <div class="nav-label" style="margin-top:30px">Koleksi</div>
      <nav class="nav">
        <button data-page="Liburan 2024"><span>▣</span><b>Liburan 2024</b></button>
        <button data-page="Keluarga"><span>▣</span><b>Keluarga</b></button>
        <button data-page="Pekerjaan"><span>▣</span><b>Pekerjaan</b></button>
      </nav>
      <div class="storage"><div class="storage-top">Penyimpanan <span>4.2 / 10 GB</span></div><div class="bar"><div></div></div><small>5.8 GB masih tersedia</small></div>
    </aside>
    <main>
      <header>
        <div class="search"><span>⌕</span><input id="search" type="search" placeholder="Cari foto atau album..." aria-label="Cari foto atau album"></div>
        <div class="account"><button id="uploadTop">＋ Unggah</button><div class="avatar">AR</div></div>
      </header>
      <div class="content">
        <div class="welcome"><div><h1 id="pageTitle">Selamat datang, Aira</h1><p>Semua kenanganmu tersimpan rapi di satu tempat.</p></div><button class="upload" id="upload">＋ Unggah foto</button></div>
        <div class="stats">
          <div class="stat"><div><div class="stat-label">Total foto</div><div class="stat-number">1.248</div></div><div class="stat-icon">▧</div></div>
          <div class="stat"><div><div class="stat-label">Album dibuat</div><div class="stat-number">12</div></div><div class="stat-icon">▤</div></div>
          <div class="stat"><div><div class="stat-label">Dibagikan ke kamu</div><div class="stat-number">24</div></div><div class="stat-icon">↗</div></div>
        </div>
        <section>
          <div class="section-head"><h2>Album kamu</h2><div class="view-actions"><button class="active">▦</button><button>☷</button></div></div>
          <div class="albums">
            <article class="album"><div class="album-cover cover-1"></div><div class="album-info"><div class="album-name">Liburan 2024</div><div class="album-count">248 foto</div></div></article>
            <article class="album"><div class="album-cover cover-2"></div><div class="album-info"><div class="album-name">Keluarga</div><div class="album-count">186 foto</div></div></article>
            <article class="album"><div class="album-cover cover-3"></div><div class="album-info"><div class="album-name">Pekerjaan</div><div class="album-count">92 foto</div></div></article>
            <article class="album"><div class="album-cover cover-4"></div><div class="album-info"><div class="album-name">Inspirasi</div><div class="album-count">76 foto</div></div></article>
          </div>
        </section>
        <section>
          <div class="section-head"><h2>Foto terbaru</h2><div class="view-actions"><button id="sort">Terbaru ▾</button></div></div>
          <div class="photos" id="photos">
            <article class="photo" data-name="pantai sore"><img src="https://images.unsplash.com/photo-1507525428034-b723cf961d3e?w=700&q=80" alt="Pantai saat sore"><div class="photo-info">Pantai sore<br><small>Hari ini, 16:42</small></div></article>
            <article class="photo" data-name="kopi pagi"><img src="https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=700&q=80" alt="Kopi pagi"><div class="photo-info">Kopi pagi<br><small>Kemarin, 08:15</small></div></article>
            <article class="photo" data-name="pegunungan"><img src="https://images.unsplash.com/photo-1464822759023-fed622ff2c3b?w=700&q=80" alt="Pegunungan"><div class="photo-info">Pegunungan<br><small>12 Mei 2024</small></div></article>
            <article class="photo" data-name="arsitektur kota"><img src="https://images.unsplash.com/photo-1449824913935-59a10b8d2000?w=700&q=80" alt="Arsitektur kota"><div class="photo-info">Arsitektur kota<br><small>10 Mei 2024</small></div></article>
          </div>
        </section>
      </div>
    </main>
  </div>
  <div class="toast" id="toast"></div>
  <input id="fileInput" type="file" accept="image/*" multiple hidden>
  <script>
    const toast = document.getElementById("toast");
    const fileInput = document.getElementById("fileInput");
    const photos = document.getElementById("photos");
    let timer;
    function showToast(message) { toast.textContent = message; toast.classList.add("show"); clearTimeout(timer); timer = setTimeout(() => toast.classList.remove("show"), 2200); }
    document.getElementById("upload").onclick = () => fileInput.click();
    document.getElementById("uploadTop").onclick = () => document.getElementById("upload").click();
    fileInput.addEventListener("change", event => {
      const selectedFiles = [...event.target.files].filter(file => file.type.startsWith("image/"));
      selectedFiles.forEach(file => {
        const photo = document.createElement("article");
        const image = document.createElement("img");
        const info = document.createElement("div");
        const name = document.createElement("span");
        const time = document.createElement("small");
        photo.className = "photo";
        photo.dataset.name = file.name.toLowerCase();
        image.src = URL.createObjectURL(file);
        image.alt = file.name;
        info.className = "photo-info";
        name.textContent = file.name;
        time.textContent = "Baru saja";
        info.append(name, document.createElement("br"), time);
        photo.append(image, info);
        photos.prepend(photo);
      });
      if (selectedFiles.length) showToast(selectedFiles.length + " foto berhasil ditambahkan");
      if (event.target.files.length !== selectedFiles.length) showToast("Hanya file gambar yang dapat diunggah");
      event.target.value = "";
    });
    document.querySelectorAll(".nav button").forEach(button => button.onclick = () => {
      document.querySelector(".nav button.active").classList.remove("active");
      button.classList.add("active");
      document.getElementById("pageTitle").textContent = button.dataset.page;
      showToast("Membuka " + button.dataset.page);
    });
    document.getElementById("search").addEventListener("input", event => {
      const query = event.target.value.toLowerCase();
      document.querySelectorAll(".photo").forEach(photo => photo.style.display = photo.dataset.name.includes(query) ? "" : "none");
    });
    document.getElementById("sort").onclick = () => showToast("Foto sedang ditampilkan dari yang terbaru");
    document.querySelectorAll(".view-actions button").forEach(button => button.onclick = () => {
      button.parentElement.querySelector(".active")?.classList.remove("active");
      button.classList.add("active");
      if (button.textContent.includes("☷")) document.getElementById("photos").style.gridTemplateColumns = "1fr";
      else document.getElementById("photos").style.gridTemplateColumns = "";
    });
  </script>
</body>
</html>
