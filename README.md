<!doctype html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Boutique - Produits Digitaux & Beauté</title>
  <meta name="description" content="Boutique en ligne simple pour vendre des produits digitaux et des produits de beauté. HTML + CSS uniquement, prêt à personnaliser." />

  <style>
    /* ---------- Reset simple ---------- */
    * { box-sizing: border-box; margin: 0; padding: 0; }
    html,body { height: 100%; }
    html,body{ background-color: #d1d2d2;
      background-image: -moz-radial-gradient(html);
         }
    body { font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial; line-height: 1.4; color: #222; background: #f6f7fb; }
    a { color: inherit; text-decoration: none; }
    /* ---------- Layout ---------- */n
    .container { max-width: 1100px; margin: 28px auto; padding: 0 18px; }

    /* ---------- Header ---------- */
    header.site-header { border-radius: 10px; box-shadow: 0 6px 18px rgba(16,24,40,0.06); padding: 18px; margin-bottom: 18px; }
    .brand { display:flex; align-items:center; gap:12px; }
    .logo { width:46px; height:46px; border-radius:8px; background: linear-gradient(135deg,#236ace 0%, #183087 100%); display:flex; align-items:center; justify-content:center; color:#1b1818; font-weight:700; }
    .brand h1 { font-size:18px; }
    nav { margin-left:auto; }
    .nav-list { display:flex; gap:14px; align-items:center; }
    .nav-list a { padding:8px 12px; border-radius:8px; font-weight:600; color:#374151; }
    .nav-list a.cta { background:#0f4be2; color:#000000; } 

    /* ---------- Hero ---------- */
    .hero { display:grid; grid-template-columns: 1fr 420px; gap:18px; align-items:center; margin: 18px 0; }
    .hero-left h2 { font-size:26px; margin-bottom:8px; }
    .hero-left p { color:#000000; margin-bottom:12px; }
    .hero-actions { display:flex; gap:10px; }
    .btn { display:inline-block; padding:10px 14px; border-radius:8px; font-weight:700; }
    .btn-primary { background:#0f4be2; color:rgb(0, 0, 0); }
    .btn-outline { border:2px solid #0f4be2; color:#000000; background:transparent; }
    .hero-right { background:linear-gradient(180deg,#0f3cb7,#0b5bab); border-radius:10px; padding:14px; box-shadow: 0 8px 24px rgba(16,24,40,0.04); }
    .search { display:flex; gap:8px; }
    .search input { flex:1; padding:10px 12px; border-radius:8px; border:1px solid #e6e9ef; }

    /* ---------- Filters / Categories ---------- */
    .categories { display:flex; gap:8px; margin: 12px 0 18px; flex-wrap:wrap; }
    .cat { background:#fff; padding:8px 12px; border-radius:999px; border:1px solid #e6e9ef; font-weight:600; }
    .cat.active { background:#0f4be2; color:#000000; border-color:transparent; }

    /* ---------- Products grid ---------- */
    .products-grid { display:grid; grid-template-columns: repeat(3, 1fr); gap:18px; }
    .product { background:#0f4be2; border-radius:12px; overflow:hidden; box-shadow: 0 6px 18px rgba(16,24,40,0.04); display:flex; flex-direction:column; }
    .product .media { height:180px; background-size:cover; background-position:center; }
    .product .body { padding:12px 14px; display:flex; flex-direction:column; gap:8px; flex:1; }
    .product .title { font-weight:700; font-size:1rem; }
    .product .desc { color:#000000; font-size:0.92rem; flex:1; }
    .price-row { display:flex; align-items:center; justify-content:space-between; gap:10px; }
    .price { font-weight:800; color:#111; }
    .small { font-size:0.85rem; color:#000000; }
    .buy { padding:8px 10px; border-radius:8px; font-weight:700; text-align:center; }
    .buy-mail { background:linear-gradient(90deg,#0f4be2,#101f92); color:rgb(3, 2, 2); }
    .badge { display:inline-block; padding:6px 8px; border-radius:8px; background:#ffedd5; color:#000000; font-weight:700; font-size:0.82rem; }
s
    /* ---------- Section titles ---------- */
    .section-title { display:flex; align-items:center; justify-content:space-between; margin: 18px 0 8px; }
    .section-title h3 { font-size:18px; }
    .see-all { color:#fafafa; font-weight:700; }

    /* ---------- Footer ---------- */
    footer { margin-top:22px; padding:18px; border-radius:10px; background:#fff; box-shadow: 0 6px 18px rgba(16,24,40,0.04); }
    .footer-grid { display:flex; gap:20px; flex-wrap:wrap; }
    .footer-grid div { min-width:180px; }

    /* ---------- Responsive ---------- */
    @media (max-width:1000px) {
      .hero { grid-template-columns: 1fr; }
      .products-grid { grid-template-columns: repeat(2, 1fr); }
    }
    @media (max-width:640px) {
      .nav-list { display:none; }
      .container { padding: 0 12px; }
      .products-grid { grid-template-columns: 1fr; }
      .hero-right { order: -1; }
    }

    /* ---------- Small helpers ---------- */
    .muted { color:#667085; }
    .center { text-align:center; }
    /* ---------- Animations ---------- */

/* Apparition en fondu + glissement */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Zoom léger au survol */
@keyframes zoomIn {
  from { transform: scale(0.95); opacity:0.7; }
  to   { transform: scale(1); opacity:1; }
}

/* Effet pulse pour attirer l’attention */
@keyframes pulse {
  0% { transform: scale(1); }
  50% { transform: scale(1.05); }
  100% { transform: scale(1); }
}

/* ---------- Application ---------- */
header.site-header {
  animation: fadeInUp 0.8s ease-in-out;
}

.hero-left h2, .hero-left p, .hero-actions {
  animation: fadeInUp 1s ease forwards;
}

.product {
  animation: zoomIn 0.6s ease;
  transition: transform 0.3s ease;
}
.product:hover {
  transform: translateY(-6px) scale(1.02);
  box-shadow: 0 10px 28px rgba(16,24,40,0.1);
}

.btn-primary, .btn-outline, .buy-mail {
  transition: all 2s ease;
}
.btn-primary:hover, .btn-outline:hover, .buy-mail:hover {
  animation: pulse 0.6s ease;
}

.footer-grid div {
  animation: fadeInUp 1s ease;
}

  </style>
</head>
<body>
<style>
   header.site-header {
     border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.08);
      overflow: hidden;
      display: flex;
      flex-direction: column;
      transition: transform 0.2s ease;
      transform: translateY(-6px);
   }
</style>
<style>
 
   
</style>
  <div class="container">

    <!-- Header -->
    <header class="site-header" role="banner">
      <div style="display:flex;align-items:center;gap:12px;">
        <div class="brand">
          <div class="logo">KF</div>
          <div>
            <h1>KHABA DIGITAUX</h1>
            <div class="small muted">Produits digitaux</div>
          </div>
        </div>

        <nav aria-label="Navigation principale">
          <div class="nav-list">
            <a href="#digital">Digitaux</a>
            
            <a class="cta" href="https://wa.me/224611755368?text=Bonjour%2C%20je%20souhaite%20acheter%20KF%20KF-SHOP%20%281%20unit%C3%A9%29.%20Nom%3A%20__.%20Adresse%3A%20__.%20Merci.">Contact / Acheter</a>
          </div>
        </nav>
      </div>
    </header>

    <!-- Hero -->
    <section class="hero" aria-label="Intro">
      <div class="hero-left">
        <h2>Bienvenue dans notre boutique</h2>
        <p>Vendez et achetez des produits digitaux (e-books, templates, formations) et des produits de beauté locaux. Simple, propre et prêt à personnaliser.</p>
        <div class="hero-actions">
          <a class="btn btn-primary" href="#products">Voir les produits</a>
          <a class="btn btn-outline" href="#contact">Nous contacter</a>
         
        </div>  
      </div>

      <aside class="hero-right">
        <div style="margin-bottom:8px;font-weight:800;">Recherche rapide</div>
        <form class="search" onsubmit="return false;"> 
          <input type="search" placeholder="Rechercher un produit..." aria-label="Rechercher" />
          <button class="btn btn-primary" type="submit">OK</button>
        </form>

        <div style="margin-top:12px;display:flex;gap:8px;flex-wrap:wrap;">
          <div class="badge">Livraison: numérique & locale</div>
          <div class="badge">Paiement: Mobile Money / Espèces</div>
        </div>
      </aside>
    </section>

    <!-- Categories -->
    <div class="categories" role="navigation" aria-label="Catégories">
      <a class="cat active" href="#products">Tous</a>
      <a class="cat" href="#digital">Produits digitaux</a>

    </div>

    <!-- Products - Digital -->
    <section id="digital">
      <div class="section-title">
        <h3>Produits digitaux</h3>
        <a class="see-all" href="#products">Voir tout</a>
      </div>

      <div class="products-grid" aria-live="polite">
        <!-- Produit 1 -->
        <article class="product">
          <div class="media" style="background-image: url('image\ du\ cour/EBOOK.PNG.jpg');"></div>
          <div class="body">
            <div class="title">E-book: Guide Marketing Digital</div>
            <div class="desc">Un guide complet pour apprendre à vendre en ligne en Guinée — stratégie, canaux, publicité.</div>
            <div class="price-row">
              <div>
                <div class="price">25 000 GNF</div>
                <div class="small">Livraison: lien instantané</div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: PDF</span>
              </div>
            </div>
          </div>
        </article>


        <!-- Produit 2 -->
        <article class="product">
          <div class="media" style="background-image: url('image\ du\ cour/');"></div>
          <div class="body">
            <div class="title">cour de trading</div>
            <div class="desc">Connaitre et comprendre les stratégies du trading.</div>
            <div class="price-row">
              <div>
                <div class="price">25 000 GNF</div>
                <div class="small">Licence: usage commercial</div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: PDF</span>
              </div>
            </div>
          </div>
        </article>

        <!-- Produit 3 -->
        <article class="product">
          <div class="media" style="background-image: url('word.png.webp');"></div>
          <div class="body">
            <div class="title">Cour de word pdf & video></div>
            <div class="desc">modules pdf & vidéo pour metriser le logiciel word.</div>
            <div class="price-row">
              <div>
                <div class="price">50 000 GNF</div>
                <div class="small">Accès: 30 jours</div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: Vidéo & PDF</span>
              </div>
            </div>
          </div>
          
        </article>

      </div>
    </section>
    <hr>

    <!-- Products - Beauté -->
    <section id="beaute" style="margin-top:22px;">
      <div class="section-title">
      
       
      </div>

      <div class="products-grid">
        <!-- Produit beauté 1 -->
        <article class="product">
          <div class="media" style="background-image: url('excel.png.png');"></div>
          <div class="body">
            <div class="title">Cour de Excel pdf & video</div>
            <div class="desc">modules pdf & vidéo pour metriser le logiciel word.</div>
            <div class="price-row">
              <div>
                <div class="price">60 000 GNF</div>
                <div class="small"></div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video & PDF</span>
              </div>
            </div>
          </div>
        </article>

        <!-- Produit beauté 2 -->
        <article class="product">
          <div class="media" style="background-image: url('POWER.PNG.webp');"></div>
          <div class="body">
            <div class="title">Cour de Power point pdf & video</div>
            <div class="desc">modules pdf & vidéo pour metriser le logiciel word.</div>
            <div class="price-row">
              <div>
                <div class="price">45 000 GNF</div>
                <div class="small"></div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video & PDF</span>
              </div>
            </div>
          </div>
        </article>

        <!-- Produit beauté 3 -->
        <article class="product">
          <div class="media" style="background-image: url('ACCESS.PNG.webp');"></div>
          <div class="body">
            <div class="title">Cour d'Access pdf & video</div>
            <div class="desc">modules pdf & vidéo pour metriser le logiciel word.</div>
            <div class="price-row">
              <div>
                <div class="price">95 000 GNF</div>
                <div class="small"></div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video & PDF</span>
              </div>
            </div>
          </div>
        </article>

     </div>
              </div>
            </div>
          </div>
        </article>
        <br>


    <!-- Products - Digital -->
    <section id="digital">
      <div class="section-title">
      
      </div>

      <div class="products-grid" aria-live="polite">
        <!-- Produit 1 -->
        <article class="product">
          <div class="media" style="background-image: url('HTML.PNG.webp');"></div>
          <div class="body">
            <div class="title">Cour HTML pdf & video</div>
            <div class="desc">modules pdf & vidéo pour metriser le logiciel.</div>
            <div class="price-row">
              <div>
                <div class="price">50 000 GNF</div>
                <div class="small">Livraison: lien instantané</div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video & PDF</span>
              </div>
            </div>
          </div>
        </article>

        <!-- Produit 2 -->
        <article class="product">
          <div class="media" style="background-image: url('CSS.PNG.png');"></div>
          <div class="body">
            <div class="title">Cour de CSS</div>
            <div class="desc">modules pdf & vidéo pour metriser cette langage de programation.</div>
            <div class="price-row">
              <div>
                <div class="price">55 000 GNF</div>
                
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video & PDF</span>
              </div>
            </div>
          </div>
        </article>

        <!-- Produit 3 -->
        <article class="product">
          <div class="media" style="background-image: url(sage.png);"></div>
          <div class="body">
            <div class="title">Formation en sage comptabilité</div>
            <div class="desc">Gérez efficacement vos finances et votre comptabilité grâce à Sage.</div>
            <div class="price-row">
              <div>
                <div class="price">85 000 GNF</div>
                <div class="small"></div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video & PDF</span>
              </div>
            </div>
          </div>
          
        </article>

      </div>
    </section>

    <!-- Products - Beauté -->
    <section id="beaute" style="margin-top:22px;">
      <div class="section-title">
       
        
      </div>

      <div class="products-grid">
        <!-- Produit beauté 1 -->
        <article class="product">
          <div class="media" style="background-image: url(py.PNG);"></div>
          <div class="body">
            <div class="title">PYTHON programation</div>
            <div class="desc">Développemtent Mobile pour plus de comprehention.</div>
            <div class="price-row">
              <div>
                <div class="Money">108 000 GNF</div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video & PDF</span>
              </div>
            </div>
          </div>
        </article>

        <!-- Produit beauté 2 -->
        <article class="product">
          <div class="media" style="background-image: url(JAVA.PNG);"></div>
          <div class="body">
            <div class="title">JAVA Scrip</div>
            <div class="desc">Apprenez JavaScript dès aujourd’hui et transformez vos idées en sites et applications modernes !.</div>
            <div class="price-row">
              <div>
                <div class="price">55 000 GNF</div>
                
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video & PDF</span>
              </div>
            </div>
          </div>
        </article>

        <!-- Produit beauté 3 -->
        <article class="product">
          <div class="media" style="background-image: url(GESTION.PNG);"></div>
          <div class="body">
            <div class="title">GESTION DU PROJET</div>
            <div class="desc">Développez vos compétences en gestion de projet pour diriger avec méthode et efficacité.</div>
            <div class="price-row">
              <div>
                <div class="price">125 000 GNF</div>
                
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: PDF</span>
              </div>
            </div>
          </div>
        </article>

     </div>
              </div>
            </div>
          </div>
<br>
           

    <!-- Products - Digital -->
    <section id="digital">
      <div class="section-title">
        
        
      </div>

      <div class="products-grid" aria-live="polite">
        <!-- Produit 1 -->
        <article class="product">
          <div class="media" style="background-image: url(RESSOURCE.PNG);"></div>
          <div class="body">
            <div class="title">RESSOURCE HUMAINES</div>
            <div class="desc">"Maîtrisez les bases des ressources humaines pour mieux gérer et motiver vos équipes.".</div>
            <div class="price-row">
              <div>
                <div class="price">25 000 GNF</div>
                
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: PDF</span>
              </div>
            </div>
          </div>
        </article>

        <!-- Produit 2 -->
        <article class="product">
          <div class="media" style="background-image: url(PS.PNG);"></div>
          <div class="body">
            <div class="title">PHOTOSHOP</div>
            <div class="desc">Pack de templates modifiables pour boutiques et flyers — prêt à l'emploi.</div>
            <div class="price-row">
              <div>
                <div class="price">80 000 GNF</div>
                <div class="small">Libérez votre créativité et transformez vos images avec Photoshop.</div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video & PDF</span>
              </div>
            </div>
          </div>
        </article>

        <!-- Produit 3 -->
        <article class="product">
          <div class="media" style="background-image: url(AI.PNG);" ></div>
          <div class="body">
            <div class="title">ILLUSTRATOR</div>
            <div class="desc">Créez des designs professionnels et uniques grâce à Illustrator</div>
            <div class="price-row">
              <div>
                <div class="price">85 000 GNF</div>
                
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: Vidéo & PDF</span>
              </div>
            </div>
          </div>
          
        </article>
   
      

      </div>
    </section>
    
      <!-- Products - Digital -->
    <section id="digital">
      <div class="section-title">
        
        
      </div>
      <br>

      <div class="products-grid" aria-live="polite">
        <!-- Produit 1 -->
        <article class="product">
          <div class="media" style="background-image: url(wordepress.png);"></div>
          <div class="body">
            <div class="title">Word Press</div>
            <div class="desc">"Maîtrisez et Creer votre site de vente avec cette formation .".</div>
            <div class="price-row">
              <div>
                <div class="price">125 000 GNF</div>
                
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: VIDEO</span>
              </div>
            </div>
          </div>
        </article>
      

        <!-- Produit 2 -->
        <article class="product">
          <div class="media" style="background-image: url(CYBER.PNG.jpg);"></div>
          <div class="body">
            <div class="title">Cyber Sécurité</div>
            <div class="desc">formation pratique et efficacité pour les debutant.</div>
            <div class="price-row">
              <div>
                <div class="price">150 000 GNF</div>
                <div class="small">Formation en Cyber securité .</div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video </span>
              </div>
            </div>
          </div>
        </article>

        <!-- Produit 3 -->
        <article class="product">
          <div class="media" style="background-image: url(canva.png.jpg);" ></div>
          <div class="body">
            <div class="title">Canva</div>
            <div class="desc">Formeation Création des designs professionnels et uniques grâce à canva avec syplicité et suivis des formations bonus</div>
            <div class="price-row">
              <div>
                <div class="price">105 000 GNF</div>
                
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: Vidéo</span>
              </div>
            </div>
          </div>
          
        </article> 
         <article class="product">
          <div class="media" style="background-image: url(cisco.png);"></div>
          <div class="body">
            <div class="title">CISCO.CCNA.CCNP</div>
            <div class="desc">formation pratique et efficacité pour les debutant EN CISCO .</div>
            <div class="price-row">
              <div>
                <div class="price">120 000 GNF</div>
                <div class="small">Formation en CISCO .</div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video </span>
              </div>
            </div>
          </div>
        </article>
         <article class="product">
          <div class="media" style="background-image: url(BIG\ DATA.PNG);"></div>
          <div class="body">
            <div class="title">BIG DATA</div>
            <div class="desc">formation pratique et efficacité pour les debutant.</div>
            <div class="price-row">
              <div>
                <div class="price">130 000 GNF</div>
                <div class="small">Formation en BIG DATA POUR BOUSTER VOTRE COMPETENCE .</div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video </span>
              </div>
            </div>
          </div>
        </article>
         <article class="product">
          <div class="media" style="background-image: url(DJANGO.PNG);"></div>
          <div class="body">
            <div class="title">CERTIFICATION EN DJANGO</div>
            <div class="desc">formation pratique et efficacité pour les debutant.</div>
            <div class="price-row">
              <div>
                <div class="price">90 000 GNF</div>
                <div class="small">Formation en DJANGO .</div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video </span>
              </div>
            </div>
          </div>
        </article>
         <article class="product">
          <div class="media" style="background-image: url(hacking.PNG);"></div>
          <div class="body">
            <div class="title">HACKING </div>
            <div class="desc">formation pratique et efficacité pour les debutant EN HACKING.</div>
            <div class="price-row">
              <div>
                <div class="price">160 000 GNF</div>
                <div class="small">Formation en HACKING.</div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video </span>
              </div>
            </div>
          </div>
        </article>
         <article class="product">
          <div class="media" style="background-image: url(CAPCUT.PNG);"></div>
          <div class="body">
            <div class="title">CAPCUT</div>
            <div class="desc">formation pratique et efficacité SUR CAPCUT.</div>
            <div class="price-row">
              <div>
                <div class="price">110 000 GNF</div>
                <div class="small">Formation en CAPCUT pour vos montage video .</div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video </span>
              </div>
            </div>
          </div>
        </article>
         <article class="product">
          <div class="media" style="background-image: url(LINKEDIN.PNG);"></div>
          <div class="body">
            <div class="title">LINKEDIN</div>
            <div class="desc">formation pratique et efficacité pour les debutantS en LINKEDIN</div>
            <div class="price-row">
              <div>
                <div class="price">100 000 GNF</div>
                <div class="small">Formation en LINKEDIN .</div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video </span>
              </div>
            </div>
         
          </div>
        </article>
         <article class="product">
          <div class="media" style="background-image: url(id.PNG.jpg);"></div>
          <div class="body">
            <div class="title">INDISIGN</div>
            <div class="desc">formation pratique et efficacité pour les debutant en disign.</div>
            <div class="price-row">
              <div>
                <div class="price">90 000 GNF</div>
                <div class="small">Formation en ABDODE InDisign .</div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video </span>
              </div>
            </div>
          </div>
        </article>
    <article class="product">
          <div class="media" style="background-image: url(auto.png);"></div>
          <div class="body">
            <div class="title">AUTO-ENTREPRENEUR</div>
            <div class="desc">Savoir L'entreprenarient.</div>
            <div class="price-row">
              <div>
                <div class="price">100 000 GNF</div>
                <div class="small">Formation AUTO.</div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video </span>
              </div>
            </div>
          </div>
        </article>
          <article class="product">
          <div class="media" style="background-image: url(cad.PNG);"></div>
          <div class="body">
            <div class="title">AUTO-CAD</div>
            <div class="desc">INGENIEUR ARCHITECTE EN ACTION.</div>
            <div class="price-row">
              <div>
                <div class="price">200 000 GNF</div>
                <div class="small">Formation en AUTO-CAD.</div>
              </div>
              <div style="display:flex;flex-direction:column;gap:8px;min-width:120px;">
                <a class="buy buy-mail" href="+224.html">Acheter</a>
                <span class="small muted center">Format: video </span>
              </div>
            </div>
          </div>
        </article>
      </div>
      </div>
          
        <div class="container">
          
          <div class="text" style="text-align: center;justify-content: center;">
            <h2 style="text-align: center;">INSTATION DES LOGICIELS CONFORMENT A VOS SERVIR ET A VOS FORMATIONS</h2>
            <P>Vous voyer pas vos logiciel prierre d'envoyer un email pour une revervations</P>
        </div>
         <img src="pack.png.jpg">
     <style>
       
      img {
         width: 1900px; /* taille agrandie */
      height: 700px;
      border-radius: 5%;
    margin: 0 auto;
     display: block;

     
     }
      .btn {
      display: inline-block;
      background: #1657c0;
      color: white;
      padding: 10px 18px;
      border-radius: 8px;
      text-decoration: none;
      transition: background 0.3s ease;}
      .btn:hover {
      background: #218838;
    }
     .texte p {
      margin-bottom: 15px;
    }
     .texte {
      font-size: 18px;
      line-height: 1.6;
      color: #333; }
     </style>
    

     <div class="container">
   <br>
    <div class="texte" style="text-align: center;">
      <h2 style="text-align: center;">Vous Attender toujour pour vos logiciel</h2>
      <p>Reserver votre logiciel en cliquant sur le bouton <p> <em> " Reserver votre logiciel "</em> </p> et renplire les formulaires de reservation</p>
      <a href="RESERVATION.html" class="btn"> Reserver votre logiciel</a>

        <section id="contact" style="margin-top:28px;">
      <div class="section-title">
        <h3>Contact & Commande</h3>
        <span class="muted">Commandez par mail ou via Mobile Money</span>
      </div>
      

      <div style="display:grid;grid-template-columns:1fr 320px;gap:18px;margin-bottom:22px;">
        <div style="background:#fff;padding:14px;border-radius:10px;box-shadow:0 6px 18px rgba(16,24,40,0.04);">
          <p class="small">Pour finaliser un achat, envoyez un email à <strong>kabamaman624@gmail.com</strong> en précisant : nom, produit, quantité, adresse ou numéro Mobile Money. Vous recevrez ensuite les instructions de paiement.</p>

          <ul style="margin-top:10px;list-style:none;display:grid;gap:8px;">
            <li class="small">• Paiement Mobile Money (Orange Money, MTN Mobile Money)</li>
            <li class="small">• Paiement en espèces (retrait en point de vente)</li>
            <li class="small">• Produits digitaux : lien d'accès après paiement</li>
          </ul>
        </div>

        <aside style="background:#53a5c1;padding:14px;border-radius:10px;box-shadow:0 6px 18px rgba(16,24,40,0.04);">
          <h4 style="margin-bottom:8px;">Support rapide</h4>
          <p class="small muted">WhatsApp : <strong>+224 611 75 53 68</strong></p>
          <p class="small muted">Email : <strong>kabamaman624@gmail.com</strong></p>
          <p class="small muted">Horaires : Lun - Sam, 08:00 - 18:00</p>
          <div style="margin-top:8px;"><a class="btn btn-primary" href="https://wa.me/224611755368?text=Bonjour%2C%20je%20souhaite%20acheter%20KF-PRODUIT DIGITAUX.%20Nom%3A%20__.LAISSEZ UN MESSAGE POUR TOUS SOUCIS %3A%20__.%20Merci.">Appel WhatsApp</a></div>
        </aside>
      </div>

    </section>

    <!-- Footer -->
    <footer>
      <div style="display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:12px;">
        <div>
          <strong>KHABA Digital</strong>
          <div class="small muted">© "KF Digital" - Tous droits réservés</div>
        </div>
        <div class="small muted">Conception & mise en page : vous</div>
      </div>
    </footer>

  </div>

</body>
</html>


