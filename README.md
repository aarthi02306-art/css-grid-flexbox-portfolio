/* ===== Theme variables (light is default) ===== */
:root{
  --bg:#ffffff; --surface:#f2f4f7; --card:#ffffff;
  --text:#1a1a1a; --muted:#4a4a4a;
  --accent:#0b4f9c; --on-accent:#ffffff; --border:#595959;
  --shadow:0 4px 14px rgba(0,0,0,.12);
  --radius:.75rem; --gap:1.5rem;
  --font:system-ui,-apple-system,"Segoe UI",Roboto,Arial,sans-serif;
  color-scheme:light;
}
/* Dark theme: follows OS unless the user chose light */
@media (prefers-color-scheme:dark){
  :root:not([data-theme="light"]){
    --bg:#0f172a; --surface:#1e293b; --card:#1e293b;
    --text:#f1f5f9; --muted:#cbd5e1;
    --accent:#7ab8ff; --on-accent:#0b1220; --border:#94a3b8;
    --shadow:0 4px 14px rgba(0,0,0,.5);
    color-scheme:dark;
  }
}
/* Dark theme: chosen with the toggle button */
:root[data-theme="dark"]{
  --bg:#0f172a; --surface:#1e293b; --card:#1e293b;
  --text:#f1f5f9; --muted:#cbd5e1;
  --accent:#7ab8ff; --on-accent:#0b1220; --border:#94a3b8;
  --shadow:0 4px 14px rgba(0,0,0,.5);
  color-scheme:dark;
}

/* ===== Base (mobile first) ===== */
*,*::before,*::after{box-sizing:border-box}
html{scroll-behavior:smooth}
body{
  margin:0; min-height:100vh;
  display:grid; grid-template-rows:auto 1fr auto; /* Grid: page skeleton */
  font-family:var(--font); font-size:clamp(1rem,.95rem + .3vw,1.125rem);
  line-height:1.6; color:var(--text); background:var(--bg);
  transition:background-color .3s,color .3s;
}
h1{font-size:clamp(1.8rem,1.3rem + 2.5vw,3rem);line-height:1.2;margin:0 0 1rem}
h2{font-size:clamp(1.4rem,1.1rem + 1.2vw,2rem);margin:0 0 .75rem}
h3{margin:0 0 .5rem}
a{color:var(--accent)}
img{max-width:100%;height:auto}
ul{list-style:none;margin:0;padding:0}

/* ===== Header and footer (Flexbox) ===== */
header,footer{
  display:flex; flex-direction:column; align-items:center; gap:1rem;
  padding:1rem; background:var(--surface);
}
header nav ul,footer nav ul{display:flex;flex-wrap:wrap;justify-content:center;gap:.5rem 1.25rem}
header nav a{display:inline-block;padding:.4rem .2rem;text-decoration:none;font-weight:600}
header nav a:hover{text-decoration:underline}
a[aria-current="page"]{border-bottom:3px solid var(--accent)}
.logo{font-weight:800;font-size:1.25rem;margin:0}
footer p{margin:0;color:var(--muted)}

/* ===== Buttons ===== */
.button,button{
  display:inline-flex; align-items:center; justify-content:center; gap:.5rem;
  background:var(--accent); color:var(--on-accent);
  padding:.65rem 1.25rem; border:2px solid transparent; border-radius:999px;
  font:inherit; font-weight:600; text-decoration:none; cursor:pointer;
  transition:transform .2s,box-shadow .2s;
}
.button:hover,button:hover{transform:translateY(-2px);box-shadow:var(--shadow)}
#theme-toggle{background:transparent;color:var(--text);border-color:var(--border)}

/* ===== Focus ===== */
a:focus-visible,button:focus-visible,input:focus-visible,select:focus-visible,textarea:focus-visible{
  outline:3px solid #ff8800; outline-offset:2px;
}
.skip-link{position:absolute;left:-999px;top:0;background:#000;color:#fff;padding:.5rem 1rem}
.skip-link:focus{left:0;z-index:10}

/* ===== Main layout (Grid) ===== */
main{
  width:100%; max-width:72rem; margin:0 auto; padding:1.5rem 1rem;
  display:grid; grid-template-columns:1fr; gap:var(--gap); align-content:start;
}
main > h1{margin:0}
.hero{
  padding:2.5rem 1.25rem; border-radius:var(--radius); text-align:center;
  background:linear-gradient(135deg,var(--surface),var(--card)); box-shadow:var(--shadow);
}
.hero p{max-width:40rem;margin:0 auto 1.5rem;color:var(--muted)}
.about-grid{display:grid;grid-template-columns:1fr;gap:var(--gap)}
article,aside{
  background:var(--card); border:1px solid var(--border);
  border-radius:var(--radius); padding:1.25rem; box-shadow:var(--shadow);
}
article h2,article h3{margin-top:0}
aside ul{display:flex;flex-wrap:wrap;gap:.5rem}
aside li{background:var(--surface);padding:.25rem .75rem;border-radius:999px}

/* Projects cards */
.cards{display:grid;grid-template-columns:1fr;gap:var(--gap)}
.cards section{display:flex}
.cards article{display:flex;flex-direction:column;gap:.5rem;width:100%;transition:transform .2s}
.cards article:hover{transform:translateY(-4px)}
.cards article a{margin-top:auto}

/* Contact form */
.contact-grid{display:grid;grid-template-columns:1fr;gap:var(--gap)}
fieldset{border:1px solid var(--border);border-radius:var(--radius);padding:1rem}
legend{padding:0 .5rem;font-weight:700}
label{display:block;font-weight:700;margin-bottom:.25rem}
form p{margin:0 0 1rem}
input,select,textarea{
  width:100%; padding:.65rem; font:inherit; color:var(--text);
  background:var(--bg); border:1px solid var(--border); border-radius:.5rem;
}
small{color:var(--muted)}

/* ===== Tablet: 768px and up ===== */
@media (min-width:48em){
  header,footer{flex-direction:row;justify-content:space-between;padding:1rem 2rem}
  main{padding:2rem}
  .hero{padding:4rem 2rem}
  .about-grid{grid-template-columns:2fr 1fr}
  .cards{grid-template-columns:repeat(2,1fr)}
}

/* ===== Desktop: 1024px and up ===== */
@media (min-width:64em){
  .cards{grid-template-columns:repeat(3,1fr)}
  .contact-grid{grid-template-columns:2fr 1fr;align-items:start}
  .hero{text-align:left;padding:5rem 3rem}
  .hero p{margin-left:0}
}

/* ===== Respect user motion settings ===== */
@media (prefers-reduced-motion:reduce){
  *,*::before,*::after{transition:none!important;scroll-behavior:auto!important}
  .button:hover,button:hover,.cards article:hover{transform:none}
}
