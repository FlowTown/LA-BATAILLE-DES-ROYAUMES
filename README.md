[<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>La Bataille des Royaumes — La Nuit Magique</title>
  <style>
    :root{
      --bg-1:#05060a;
      --bg-2:#0b0d14;
      --panel:rgba(255,255,255,0.06);
      --panel-strong:rgba(255,255,255,0.09);
      --line:rgba(255,255,255,0.12);
      --text:#f5efe2;
      --muted:#b8b1a4;
      --gold:#d7b56d;
      --shadow:0 20px 50px rgba(0,0,0,.35);
    }

    *{box-sizing:border-box}

    html{
      scroll-behavior:smooth;
    }

    body{
      margin:0;
      font-family:Georgia, "Times New Roman", serif;
      color:var(--text);
      background:
        radial-gradient(circle at top, rgba(215,181,109,0.10), transparent 30%),
        radial-gradient(circle at 15% 20%, rgba(59,130,246,0.08), transparent 20%),
        radial-gradient(circle at 80% 25%, rgba(168,85,247,0.08), transparent 20%),
        linear-gradient(180deg, var(--bg-2), var(--bg-1));
      min-height:100vh;
      overflow-x:hidden;
    }

    body::before{
      content:"";
      position:fixed;
      inset:0;
      pointer-events:none;
      opacity:.28;
      background-image:
        radial-gradient(2px 2px at 20% 30%, #ffffffcc 45%, transparent 46%),
        radial-gradient(1px 1px at 70% 22%, #ffffff99 45%, transparent 46%),
        radial-gradient(1.5px 1.5px at 82% 66%, #ffffffaa 45%, transparent 46%),
        radial-gradient(1px 1px at 12% 72%, #ffffff88 45%, transparent 46%),
        radial-gradient(1.5px 1.5px at 48% 84%, #ffffff77 45%, transparent 46%);
    }

    a{
      color:inherit;
      text-decoration:none;
    }

    .container{
      width:min(1220px, calc(100% - 32px));
      margin:0 auto;
      position:relative;
      z-index:1;
    }

    header{
      position:sticky;
      top:0;
      z-index:20;
      backdrop-filter:blur(10px);
      background:rgba(5,6,10,.72);
      border-bottom:1px solid var(--line);
    }

    .topbar{
      min-height:84px;
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:20px;
      padding:14px 0;
      flex-wrap:wrap;
    }

    .brand{
      display:flex;
      align-items:center;
      gap:16px;
    }

    .brand img{
      width:68px;
      height:68px;
      object-fit:contain;
      filter:drop-shadow(0 8px 20px rgba(0,0,0,.35));
    }

    .brand-text h1{
      margin:0;
      font-size:clamp(1.35rem, 2.6vw, 2.2rem);
      letter-spacing:.03em;
    }

    .brand-text p{
      margin:6px 0 0;
      color:var(--muted);
      font-size:.95rem;
    }

    .nav-actions{
      display:flex;
      gap:12px;
      flex-wrap:wrap;
    }

    .btn{
      display:inline-flex;
      align-items:center;
      justify-content:center;
      gap:8px;
      padding:13px 18px;
      border-radius:14px;
      border:1px solid rgba(215,181,109,.28);
      background:rgba(255,255,255,.04);
      color:var(--text);
      font-weight:700;
      box-shadow:var(--shadow);
      transition:.2s ease;
    }

    .btn:hover{
      transform:translateY(-1px);
      background:rgba(255,255,255,.08);
    }

    .btn-primary{
      background:linear-gradient(180deg, rgba(215,181,109,.23), rgba(215,181,109,.08));
    }

    .hero{
      padding:72px 0 46px;
      text-align:center;
    }

    .eyebrow{
      display:inline-block;
      padding:8px 14px;
      border:1px solid rgba(215,181,109,.35);
      border-radius:999px;
      color:var(--gold);
      background:rgba(215,181,109,.08);
      font-size:.8rem;
      text-transform:uppercase;
      letter-spacing:.12em;
      margin-bottom:20px;
    }

    .hero h2{
      margin:0 auto 18px;
      max-width:960px;
      font-size:clamp(2.5rem, 6vw, 5.5rem);
      line-height:.96;
      text-wrap:balance;
    }

    .hero p{
      max-width:800px;
      margin:0 auto;
      color:var(--muted);
      font-size:1.04rem;
      line-height:1.75;
    }

    .hero-actions{
      margin-top:30px;
      display:flex;
      justify-content:center;
      gap:14px;
      flex-wrap:wrap;
    }

    .section{
      padding:28px 0;
    }

    .section-head{
      margin-bottom:20px;
      display:flex;
      align-items:end;
      justify-content:space-between;
      gap:18px;
      flex-wrap:wrap;
    }

    .section-head h3{
      margin:0 0 6px;
      font-size:clamp(1.6rem, 3vw, 2.2rem);
    }

    .section-head p{
      margin:0;
      color:var(--muted);
    }

    .panel{
      background:linear-gradient(180deg, rgba(255,255,255,.08), rgba(255,255,255,.035));
      border:1px solid var(--line);
      border-radius:24px;
      box-shadow:var(--shadow);
      backdrop-filter:blur(12px);
    }

    .podium{
      display:grid;
      grid-template-columns:repeat(3,1fr);
      gap:18px;
      margin-bottom:22px;
    }

    .podium-card{
      padding:22px;
      position:relative;
      overflow:hidden;
    }

    .podium-card::after{
      content:"";
      position:absolute;
      inset:auto -20% -30% auto;
      width:180px;
      height:180px;
      border-radius:50%;
      background:radial-gradient(circle, rgba(255,255,255,.12), transparent 65%);
      pointer-events:none;
    }

    .rank{
      display:inline-flex;
      align-items:center;
      justify-content:center;
      width:38px;
      height:38px;
      border-radius:999px;
      border:1px solid rgba(255,255,255,.18);
      margin-bottom:14px;
      color:var(--gold);
      font-weight:700;
    }

    .podium-card h4,
    .kingdom-card h4,
    .form-panel h4,
    .info-panel h4{
      margin:0 0 10px;
      font-size:1.2rem;
    }

    .score{
      margin:0;
      font-size:clamp(2rem, 4vw, 3rem);
      font-weight:700;
      line-height:1;
    }

    .sub{
      margin:8px 0 0;
      color:var(--muted);
      font-size:.95rem;
      line-height:1.55;
    }

    .kingdom-grid{
      display:grid;
      grid-template-columns:repeat(4,1fr);
      gap:18px;
    }

    .kingdom-card{
      padding:20px;
      position:relative;
      overflow:hidden;
    }

    .kingdom-card::before{
      content:"";
      position:absolute;
      inset:0;
      background:linear-gradient(180deg, rgba(255,255,255,.03), transparent 45%);
      pointer-events:none;
    }

    .kingdom-logo{
      width:96px;
      height:96px;
      border-radius:20px;
      display:grid;
      place-items:center;
      margin-bottom:16px;
      background:rgba(255,255,255,.035);
      border:1px solid rgba(255,255,255,.10);
      overflow:hidden;
    }

    .kingdom-logo img{
      width:78px;
      height:78px;
      object-fit:contain;
      filter:drop-shadow(0 10px 18px rgba(0,0,0,.35));
    }

    .kingdom-meta{
      display:flex;
      justify-content:space-between;
      gap:12px;
      margin-top:16px;
      color:var(--muted);
      font-size:.92rem;
    }

    .form-layout{
      display:grid;
      grid-template-columns:1.2fr .8fr;
      gap:18px;
      align-items:start;
    }

    .form-panel,
    .info-panel{
      padding:22px;
    }

    .field{
      display:grid;
      gap:8px;
      margin-bottom:14px;
    }

    label{
      font-size:.95rem;
      color:#efe2c3;
    }

    input,
    select,
    textarea{
      width:100%;
      border:none;
      outline:none;
      border-radius:14px;
      padding:14px;
      background:rgba(0,0,0,.28);
      color:var(--text);
      border:1px solid rgba(255,255,255,.12);
      font:inherit;
    }

    textarea{
      min-height:120px;
      resize:vertical;
    }

    .helper{
      color:var(--muted);
      line-height:1.65;
      font-size:.95rem;
    }

    .point-list{
      display:grid;
      gap:12px;
      margin-top:18px;
    }

    .point-item{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:12px;
      padding:13px 14px;
      border-radius:14px;
      border:1px solid rgba(255,255,255,.10);
      background:rgba(255,255,255,.035);
    }

    .point-value{
      color:var(--gold);
      font-weight:700;
      white-space:nowrap;
    }

    .next-step{
      padding:22px;
    }

    footer{
      padding:36px 0 60px;
      text-align:center;
      color:var(--muted);
    }

    .green{ box-shadow: inset 0 0 0 1px rgba(40,190,115,.35), var(--shadow); }
    .gold{ box-shadow: inset 0 0 0 1px rgba(215,181,109,.35), var(--shadow); }
    .red{ box-shadow: inset 0 0 0 1px rgba(205,66,66,.35), var(--shadow); }
    .black{ box-shadow: inset 0 0 0 1px rgba(180,180,180,.18), var(--shadow); }
    .bordeaux{ box-shadow: inset 0 0 0 1px rgba(123,36,72,.45), var(--shadow); }
    .blue{ box-shadow: inset 0 0 0 1px rgba(72,165,255,.35), var(--shadow); }
    .violet{ box-shadow: inset 0 0 0 1px rgba(145,96,255,.35), var(--shadow); }
    .orange{ box-shadow: inset 0 0 0 1px rgba(255,149,53,.35), var(--shadow); }

    @media (max-width:1100px){
      .kingdom-grid{
        grid-template-columns:repeat(2,1fr);
      }

      .form-layout{
        grid-template-columns:1fr;
      }
    }

    @media (max-width:760px){
      .container{
        width:min(100% - 20px, 1220px);
      }

      .podium{
        grid-template-columns:1fr;
      }

      .kingdom-grid{
        grid-template-columns:1fr;
      }

      .hero{
        padding-top:48px;
      }

      .brand img{
        width:56px;
        height:56px;
      }
    }
  </style>
</head>
<body>

  <header>
    <div class="container topbar">
      <div class="brand">
        <img src="Asset%201.svg" alt="Logo La Nuit Magique">
        <div class="brand-text">
          <h1>La Bataille des Royaumes</h1>
          <p>La Nuit Magique — Classement et demandes de points</p>
        </div>
      </div>

      <div class="nav-actions">
        <a href="#classement" class="btn">Classement</a>
        <a href="#demande" class="btn btn-primary">Demander des points</a>
      </div>
    </div>
  </header>

  <main class="container">
    <section class="hero">
      <span class="eyebrow">Fantasy • compétition • légende</span>
      <h2>Huit Royaumes s'affrontent pour écrire l'histoire de la Nuit Magique.</h2>
      <p>
        Suivez l'évolution des points de chaque Royaume, envoyez des demandes de points
        selon les actions accomplies, et faites progresser votre camp dans la grande
        bataille des Royaumes.
      </p>

      <div class="hero-actions">
        <a href="#classement" class="btn btn-primary">Voir le classement</a>
        <a href="#demande" class="btn">Envoyer une demande</a>
      </div>
    </section>

    <section class="section" id="classement">
      <div class="section-head">
        <div>
          <h3>Classement actuel</h3>
          <p>Tous les Royaumes commencent à 0 point pour le lancement.</p>
        </div>
      </div>

      <div class="podium">
        <article class="panel podium-card gold">
          <div class="rank">1</div>
          <h4>Augustus Nubium Mundus</h4>
          <p class="score">0</p>
          <p class="sub">Royaume d'or — à égalité au départ</p>
        </article>

        <article class="panel podium-card green">
          <div class="rank">2</div>
          <h4>Alcarah</h4>
          <p class="score">0</p>
          <p class="sub">Royaume vert — prêt à s'élever</p>
        </article>

        <article class="panel podium-card red">
          <div class="rank">3</div>
          <h4>Baldezor</h4>
          <p class="score">0</p>
          <p class="sub">Royaume rouge — prêt à conquérir</p>
        </article>
      </div>

      <div class="kingdom-grid">
        <article class="panel kingdom-card green">
          <div class="kingdom-logo">
            <img src="Alcarah.png" alt="Logo Alcarah">
          </div>
          <h4>Alcarah</h4>
          <p class="score">0</p>
          <div class="kingdom-meta">
            <span>Couleur</span>
            <strong>Vert</strong>
          </div>
        </article>

        <article class="panel kingdom-card gold">
          <div class="kingdom-logo">
            <img src="Augustus%20Nubium%20Mundus.png" alt="Logo Augustus Nubium Mundus">
          </div>
          <h4>Augustus Nubium Mundus</h4>
          <p class="score">0</p>
          <div class="kingdom-meta">
            <span>Couleur</span>
            <strong>Or</strong>
          </div>
        </article>

        <article class="panel kingdom-card red">
          <div class="kingdom-logo">
            <img src="Baldezor.png" alt="Logo Baldezor">
          </div>
          <h4>Baldezor</h4>
          <p class="score">0</p>
          <div class="kingdom-meta">
            <span>Couleur</span>
            <strong>Rouge</strong>
          </div>
        </article>

        <article class="panel kingdom-card black">
          <div class="kingdom-logo">
            <img src="Grimelfe%20NV.png" alt="Logo Les Ombres de Grimelfe">
          </div>
          <h4>Les Ombres de Grimelfe</h4>
          <p class="score">0</p>
          <div class="kingdom-meta">
            <span>Couleur</span>
            <strong>Noir</strong>
          </div>
        </article>

        <article class="panel kingdom-card bordeaux">
          <div class="kingdom-logo">
            <img src="Lunerei.png" alt="Logo Lunerei">
          </div>
          <h4>Lunerei</h4>
          <p class="score">0</p>
          <div class="kingdom-meta">
            <span>Couleur</span>
            <strong>Bordeaux</strong>
          </div>
        </article>

        <article class="panel kingdom-card blue">
          <div class="kingdom-logo">
            <img src="Sappheiros.png" alt="Logo Sappheiros">
          </div>
          <h4>Sappheiros</h4>
          <p class="score">0</p>
          <div class="kingdom-meta">
            <span>Couleur</span>
            <strong>Bleu clair</strong>
          </div>
        </article>

        <article class="panel kingdom-card violet">
          <div class="kingdom-logo">
            <img src="TDS%20NV.png" alt="Logo Les Terres de Sang">
          </div>
          <h4>Les Terres de Sang</h4>
          <p class="score">0</p>
          <div class="kingdom-meta">
            <span>Couleur</span>
            <strong>Violet</strong>
          </div>
        </article>

        <article class="panel kingdom-card orange">
          <div class="kingdom-logo">
            <img src="Temeriah.png" alt="Logo Témeriah">
          </div>
          <h4>Témeriah</h4>
          <p class="score">0</p>
          <div class="kingdom-meta">
            <span>Couleur</span>
            <strong>Orange</strong>
          </div>
        </article>
      </div>
    </section>

    <section class="section" id="demande">
      <div class="section-head">
        <div>
          <h3>Demander des points</h3>
          <p>Chaque demande sera vérifiée avant validation par l’administration.</p>
        </div>
      </div>

      <div class="form-layout">
        <article class="panel form-panel">
          <h4>Formulaire public</h4>

          <div class="field">
            <label for="nom">Nom / pseudo</label>
            <input id="nom" type="text" placeholder="Ex. Florian">
          </div>

          <div class="field">
            <label for="email">Email</label>
            <input id="email" type="email" placeholder="exemple@mail.com">
          </div>

          <div class="field">
            <label for="royaume">Royaume</label>
            <select id="royaume">
              <option>Alcarah</option>
              <option>Augustus Nubium Mundus</option>
              <option>Baldezor</option>
              <option>Les Ombres de Grimelfe</option>
              <option>Lunerei</option>
              <option>Sappheiros</option>
              <option>Les Terres de Sang</option>
              <option>Témeriah</option>
            </select>
          </div>

          <div class="field">
            <label for="action">Action réalisée</label>
            <select id="action">
              <option>Venir aider au bureau — 100 points</option>
              <option>Distribution de flyers — 500 points</option>
              <option>Amener un nouveau bénévole — 1000 points</option>
            </select>
          </div>

          <div class="field">
            <label for="preuve">Commentaire / preuve</label>
            <textarea id="preuve" placeholder="Ajoute une date, un détail, une précision, ou un lien vers une preuve."></textarea>
          </div>

          <a href="#" class="btn btn-primary">Envoyer la demande</a>
        </article>

        <aside class="panel info-panel">
          <h4>Actions disponibles</h4>
          <p class="helper">
            Cette première version affiche déjà l’univers, les Royaumes, les points
            et le formulaire. Ensuite, on branchera la vraie logique pour enregistrer
            les demandes, les approuver et mettre à jour les scores automatiquement.
          </p>

          <div class="point-list">
            <div class="point-item">
              <span>Venir aider au bureau</span>
              <span class="point-value">+100</span>
            </div>
            <div class="point-item">
              <span>Distribution de flyers</span>
              <span class="point-value">+500</span>
            </div>
            <div class="point-item">
              <span>Amener un nouveau bénévole</span>
              <span class="point-value">+1000</span>
            </div>
          </div>
        </aside>
      </div>
    </section>

    <section class="section">
      <div class="panel next-step">
        <h4>Prochaine étape</h4>
        <p class="helper">
          On ajoute ensuite un vrai système avec envoi des demandes, espace admin de validation,
          et mise à jour automatique du score de chaque Royaume.
        </p>
      </div>
    </section>
  </main>

  <footer class="container">
    La Nuit Magique — La Bataille des Royaumes
  </footer>

</body>
</html>
](https://flowtown.github.io/LA-BATAILLE-DES-ROYAUMES/)
