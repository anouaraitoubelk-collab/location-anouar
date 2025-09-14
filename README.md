<!doctype html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Location de Voitures — VotreAgence</title>
  <style>
    :root{
      --accent:#1e90ff;
      --dark:#0f1724;
      --muted:#64748b;
      --card:#ffffff;
      --bg:#f1f5f9;
      --radius:12px;
      --shadow: 0 6px 18px rgba(16,24,40,0.08);
      font-family: 'Segoe UI', Tahoma, Helvetica, Arial, sans-serif;
    }
    *{box-sizing:border-box}
    body{margin:0;background:var(--bg);color:var(blue dark);line-height:1.4}
    header{background:linear-gradient(90deg,var(--accent),#10b981);color:white;padding:20px 16px}
    .container{max-width:1100px;margin:20px auto;padding:0 16px}
    header .top{display:flex;align-items:center;justify-content:space-between;gap:12px}
    header h1{margin:0;font-size:20px}
    nav a{color:rgba(255,255,255,0.95);text-decoration:none;margin-left:12px;font-weight:600}

    .hero{background:linear-gradient(0deg, rgba(0,0,0,0.15), rgba(0,0,0,0.05)), url('https://images.unsplash.com/photo-1549921296-3d1a8b9f6a3a?auto=format&fit=crop&w=1400&q=60') center/cover;padding:48px;border-radius:14px;color:white}
    .hero h2{margin:0 0 8px 0;font-size:28px}
    .hero p{margin:0 0 18px 0;opacity:0.95}

    .search-bar{display:flex;gap:8px;flex-wrap:wrap}
    .search-bar input,.search-bar select{padding:10px 12px;border-radius:8px;border:1px solid rgba(15,23,36,0.08);min-width:150px}
    .btn{background:var(--dark);color:white;padding:10px 14px;border-radius:10px;border:none;cursor:pointer}
    .btn.secondary{background:transparent;color:white;border:1px solid rgba(255,255,255,0.2)}

    .grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:18px;margin-top:20px}
    .card{background:var(--card);border-radius:var(--radius);box-shadow:var(--shadow);overflow:hidden}
    .card img{width:100%;height:160px;object-fit:cover;display:block}
    .card .body{padding:12px}
    .card h3{margin:0 0 6px 0;font-size:18px}
    .meta{display:flex;justify-content:space-between;align-items:center;color:var(--muted);font-size:14px;margin-bottom:8px}
    .price{font-weight:700;color:var(--accent)}
    .card .actions{display:flex;gap:8px}

    footer{margin-top:30px;padding:20px;text-align:center;color:var(--muted)}

    /* modal */
    .modal-backdrop{position:fixed;inset:0;background:rgba(2,6,23,0.6);display:none;align-items:center;justify-content:center;padding:16px}
    .modal{background:white;border-radius:12px;max-width:520px;width:100%;padding:18px;box-shadow:0 12px 30px rgba(2,6,23,0.4)}
    .modal h4{margin:0 0 12px 0}
    .form-row{display:flex;gap:8px;margin-bottom:8px}
    .form-row input, .form-row select{flex:1;padding:8px;border-radius:8px;border:1px solid #e6edf3}
    .close-btn{background:#ef4444;color:white;border:none;padding:8px 10px;border-radius:8px;cursor:pointer}

    /* responsive tweaks */
    @media (max-width:600px){
      header .top{flex-direction:column;align-items:flex-start}
      .hero{padding:28px}
    }
  </style>
</head>
<body>
  <header>
    <div class="container top">
      <div style="display:flex;align-items:center;gap:12px">
        <img src="https://images.unsplash.com/photo-1511919884226-fd3cad34687c?auto=format&fit=crop&w=80&q=60" alt="logo" style="width:48px;height:48px;border-radius:8px;object-fit:cover">
        <div>
          <h1>VotreAgence — Anouar's car'S</h1>
          <div style="font-size:13px;opacity:0.9">Confort • Fiabilité • Prix compétitifs</div>
        </div>
      </div>
      <nav>
        <a href="#">Accueil</a>
        <a href="#">Véhicules</a>
        <a href="#">Services</a>
        <a href="#">Contact</a>
      </nav>
    </div>
  </header>

  <main class="container">
    <section class="hero">
      <h2>Louez la voiture idéale pour votre trajet</h2>
      <p>Flotte moderne, tarifs clairs, service client réactif.</p>

      <div class="search-bar" style="margin-top:18px">
        <input type="text" id="TIZNIT" placeholder="TIZNIT
         (ex: Casablanca)">
        <input type="date" id="date-debut">
        <input type="date" id="date-fin">
        <button class="btn" onclick="rechercher()">Rechercher</button>
        <button class="btn secondary" onclick="ouvrirModal()">Réserver</button>
      </div>
    </section>

    <section style="margin-top:20px">
      <h3>Nos véhicules populaires</h3>
      <div class="grid" id="cars">
        <!-- cartes véhicules (exemples) -->
        <div class="card">
          <img src="https://images.unsplash.com/photo-1502877338535-766e1452684a?auto=format&fit=crop&w=800&q=60" alt="compact">
          <div class="body">
            <h3>Compact - Renault Clio</h3>
            <div class="meta"><span>Manuelle • 5 places</span><span class="price">2500 MAD / jour</span></div>
            <div class="actions"><button class="btn" onclick="ouvrirModal('BMW COMPETITION SERIE')">Réserver</button></div>
          </div>
        </div>

        <div class="card">
          <img src="https://images.unsplash.com/photo-1549921296-3d1a8b9f6a3a?auto=format&fit=crop&w=800&q=60" alt="sedan">
          <div class="body">
            <h3>Berline - Toyota Corolla</h3>
            <div class="meta"><span>Automatique • 5 places</span><span class="price">1000 MAD / jour</span></div>
            <div class="actions"><button class="btn" onclick="ouvrirModal('Toyota Corolla')">Réserver</button></div>
          </div>
        </div>

        <div class="card">
          <img src="https://images.unsplash.com/photo-1503376780353-7e6692767b70?auto=format&fit=crop&w=800&q=60" alt="suv">
          <div class="body">
            <h3>SUV - Nissan X-Trail</h3>
            <div class="meta"><span>Automatique • 7 places</span><span class="price">7000 MAD / jour</span></div>
            <div class="actions"><button class="btn" onclick="ouvrirModal('PORCHE 911')">Réserver</button></div>
          </div>
        </div>

      </div>
    </section>

    <footer>
      <p>© 2025 VotreAgence — Tous droits réservés</p>
      <p style="font-size:13px;color:var(--muted)">Contact: +212 684964452 • anouaraitoubelk@gmail.com</p>
    </footer>
  </main>

  <!-- Modal de réservation -->
  <div class="modal-backdrop" id="modal">
    <div class="modal">
      <h4>Réserver un véhicule</h4>
      <div style="margin-bottom:8px;color:var(--muted)">Complétez le formulaire ci-dessous, nous vous contacterons pour confirmer.</div>
      <div class="form-row"><input id="car" placeholder="Véhicule"></div>
      <div class="form-row"><input id="nom" placeholder="Votre nom"><input id="tel" placeholder="Téléphone"></div>
      <div class="form-row"><input id="email" placeholder="Email"><select id="pay"><option value="cash">Paiement sur place</option><option value="card">Carte</option></select></div>
      <div style="display:flex;gap:8px;justify-content:flex-end;margin-top:10px">
        <button class="close-btn" onclick="fermerModal()">Annuler</button>
        <button class="btn" onclick="envoyerReservation()">Envoyer</button>
      </div>
    </div>
  </div>

  <script>
    function ouvrirModal(car=''){
      document.getElementById('modal').style.display='flex';
      if(car) document.getElementById('car').value = car;
    }
    function fermerModal(){
      document.getElementById('modal').style.display='none';
    }
    function envoyerReservation(){
      const data = {
        voiture: document.getElementById('car').value,
        nom: document.getElementById('nom').value,
        tel: document.getElementById('tel').value,
        email: document.getElementById('email').value,
        paiement: document.getElementById('pay').value
      };
      console.log('Réservation envoyée:', data);
      alert('Merci ! Votre demande a été envoyée. Nous vous contacterons bientôt.');
      fermerModal();
    }
    function re
