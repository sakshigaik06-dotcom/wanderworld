<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>WanderWorld – Explore Beyond Horizons</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700;900&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
<style>
/* ===================== RESET & VARIABLES ===================== */
*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
:root {
  --navy:   #0a2342;
  --ocean:  #1a6b8a;
  --sky:    #38b6d8;
  --mint:   #2ec4b6;
  --foam:   #e8f7fa;
  --gold:   #f4c430;
  --white:  #ffffff;
  --gray:   #6b7280;
  --light:  #f0f8ff;
  --card-shadow: 0 8px 32px rgba(10,35,66,.12);
  --transition: .35s cubic-bezier(.4,0,.2,1);
}
html { scroll-behavior: smooth; }
body { font-family: 'DM Sans', sans-serif; color: var(--navy); background: var(--white); overflow-x: hidden; }
h1,h2,h3,h4 { font-family: 'Playfair Display', serif; }
img { display: block; width: 100%; object-fit: cover; }
a { text-decoration: none; color: inherit; }
ul { list-style: none; }

/* ===================== PAGES ===================== */
.page { display: none; }
.page.active { display: block; }

/* ===================== NAV ===================== */
nav {
  position: sticky; top: 0; z-index: 1000;
  background: rgba(10,35,66,.96);
  backdrop-filter: blur(12px);
  padding: 0 5%;
  display: flex; align-items: center; justify-content: space-between;
  height: 70px;
  box-shadow: 0 2px 24px rgba(0,0,0,.25);
}
.logo {
  font-family: 'Playfair Display', serif;
  font-size: 1.6rem; font-weight: 900;
  color: var(--white);
  letter-spacing: -0.5px;
}
.logo span { color: var(--sky); }
.nav-links { display: flex; gap: 2rem; align-items: center; }
.nav-links a {
  color: rgba(255,255,255,.82);
  font-size: .9rem; font-weight: 500;
  letter-spacing: .04em;
  transition: color var(--transition);
  cursor: pointer;
  padding: 4px 0;
  border-bottom: 2px solid transparent;
}
.nav-links a:hover, .nav-links a.active {
  color: var(--sky);
  border-bottom-color: var(--sky);
}
.nav-cta {
  background: linear-gradient(135deg, var(--sky), var(--mint));
  color: var(--white) !important;
  padding: 9px 22px !important;
  border-radius: 50px;
  border-bottom: none !important;
  font-weight: 600 !important;
  transition: transform var(--transition), box-shadow var(--transition) !important;
}
.nav-cta:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(56,182,216,.45); }
.hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; }
.hamburger span { width: 26px; height: 2px; background: var(--white); border-radius: 2px; transition: var(--transition); }

/* ===================== BUTTONS ===================== */
.btn {
  display: inline-flex; align-items: center; gap: .5rem;
  padding: 14px 34px; border-radius: 50px;
  font-family: 'DM Sans', sans-serif; font-weight: 600; font-size: .95rem;
  cursor: pointer; border: none; transition: all var(--transition);
}
.btn-primary {
  background: linear-gradient(135deg, var(--sky) 0%, var(--mint) 100%);
  color: var(--white);
  box-shadow: 0 8px 24px rgba(56,182,216,.4);
}
.btn-primary:hover { transform: translateY(-3px); box-shadow: 0 12px 32px rgba(56,182,216,.55); }
.btn-outline {
  background: transparent;
  color: var(--white);
  border: 2px solid var(--white);
}
.btn-outline:hover { background: var(--white); color: var(--navy); }
.btn-dark { background: var(--navy); color: var(--white); }
.btn-dark:hover { background: var(--ocean); transform: translateY(-2px); }

/* ===================== SECTION COMMON ===================== */
.section { padding: 90px 5%; }
.section-label {
  display: inline-flex; align-items: center; gap: .5rem;
  background: linear-gradient(135deg, rgba(56,182,216,.12), rgba(46,196,182,.12));
  color: var(--ocean);
  padding: 6px 18px; border-radius: 50px;
  font-size: .8rem; font-weight: 600; letter-spacing: .1em; text-transform: uppercase;
  margin-bottom: 1rem;
}
.section-title {
  font-size: clamp(2rem, 4vw, 3rem);
  color: var(--navy);
  line-height: 1.2;
  margin-bottom: .75rem;
}
.section-title span { color: var(--sky); }
.section-sub { color: var(--gray); font-size: 1.05rem; max-width: 560px; line-height: 1.7; margin-bottom: 3rem; }
.section-header { text-align: center; }
.section-header .section-sub { margin-left: auto; margin-right: auto; }

/* ===================== HOME – HERO ===================== */
.hero {
  height: 100vh; min-height: 600px;
  position: relative;
  display: flex; align-items: center; justify-content: center;
  overflow: hidden;
}
.hero-bg {
  position: absolute; inset: 0;
  background: url('https://images.unsplash.com/photo-1506905925346-21bda4d32df4?w=1600&q=80') center/cover no-repeat;
}
.hero-overlay {
  position: absolute; inset: 0;
  background: linear-gradient(135deg, rgba(10,35,66,.88) 0%, rgba(26,107,138,.6) 60%, rgba(46,196,182,.2) 100%);
}
.hero-content {
  position: relative; z-index: 2;
  text-align: center; color: var(--white);
  padding: 0 5%;
  animation: fadeUp .9s ease both;
}
.hero-badge {
  display: inline-flex; align-items: center; gap: .5rem;
  background: rgba(255,255,255,.12); backdrop-filter: blur(8px);
  border: 1px solid rgba(255,255,255,.2);
  color: var(--sky); font-size: .82rem; font-weight: 600; letter-spacing: .12em; text-transform: uppercase;
  padding: 7px 18px; border-radius: 50px; margin-bottom: 1.5rem;
}
.hero-title {
  font-size: clamp(2.2rem, 6vw, 4.5rem);
  font-weight: 900; line-height: 1.1;
  margin-bottom: 1.25rem;
  text-shadow: 0 4px 24px rgba(0,0,0,.3);
}
.hero-title span { color: var(--sky); }
.hero-sub { font-size: clamp(1rem, 2vw, 1.25rem); color: rgba(255,255,255,.85); max-width: 600px; margin: 0 auto 2.5rem; line-height: 1.7; }
.hero-btns { display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; }
.hero-stats {
  position: absolute; bottom: 40px; left: 50%; transform: translateX(-50%);
  display: flex; gap: 3rem;
  background: rgba(255,255,255,.1); backdrop-filter: blur(16px);
  border: 1px solid rgba(255,255,255,.2);
  padding: 20px 40px; border-radius: 20px;
  color: var(--white);
  z-index: 2;
}
.stat-item { text-align: center; }
.stat-num { font-family: 'Playfair Display', serif; font-size: 1.8rem; font-weight: 700; color: var(--sky); }
.stat-lbl { font-size: .78rem; opacity: .75; letter-spacing: .06em; text-transform: uppercase; }

/* ===================== HOME – TOP PLACES ===================== */
.places-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 1.5rem;
}
.place-card {
  border-radius: 20px; overflow: hidden;
  box-shadow: var(--card-shadow);
  cursor: pointer;
  position: relative;
  height: 340px;
  transition: transform var(--transition), box-shadow var(--transition);
}
.place-card:hover { transform: translateY(-8px); box-shadow: 0 20px 48px rgba(10,35,66,.2); }
.place-card img { height: 100%; transition: transform .5s ease; }
.place-card:hover img { transform: scale(1.08); }
.place-card-overlay {
  position: absolute; inset: 0;
  background: linear-gradient(to top, rgba(10,35,66,.9) 0%, transparent 55%);
}
.place-card-info {
  position: absolute; bottom: 0; left: 0; right: 0;
  padding: 24px;
  color: var(--white);
}
.place-rank {
  position: absolute; top: 16px; left: 16px;
  background: var(--gold);
  color: var(--navy);
  font-weight: 700; font-size: .78rem;
  padding: 4px 12px; border-radius: 50px;
}
.place-card-info h3 { font-size: 1.35rem; margin-bottom: .3rem; }
.place-card-info p { font-size: .83rem; opacity: .8; }
.place-card-info .rating { color: var(--gold); font-size: .85rem; margin-top: .4rem; }

/* ===================== HOME – TRAVEL TIPS ===================== */
.tips-section { background: var(--foam); }
.tips-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 1.5rem;
}
.tip-card {
  background: var(--white);
  border-radius: 18px;
  padding: 2rem 1.75rem;
  box-shadow: var(--card-shadow);
  transition: transform var(--transition);
}
.tip-card:hover { transform: translateY(-5px); }
.tip-icon {
  width: 56px; height: 56px;
  border-radius: 16px;
  background: linear-gradient(135deg, var(--sky), var(--mint));
  display: flex; align-items: center; justify-content: center;
  font-size: 1.4rem; color: var(--white);
  margin-bottom: 1.25rem;
}
.tip-card h4 { font-size: 1.1rem; margin-bottom: .6rem; }
.tip-card p { color: var(--gray); font-size: .9rem; line-height: 1.65; }

/* ===================== HOME – TESTIMONIALS ===================== */
.testimonials-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 1.5rem;
}
.testimonial-card {
  background: var(--white);
  border-radius: 20px;
  padding: 2rem;
  box-shadow: var(--card-shadow);
  border-left: 4px solid var(--sky);
  transition: transform var(--transition);
}
.testimonial-card:hover { transform: translateY(-5px); }
.testimonial-card p { color: var(--gray); line-height: 1.7; font-size: .95rem; margin-bottom: 1.5rem; font-style: italic; }
.testimonial-author { display: flex; align-items: center; gap: 1rem; }
.author-avatar {
  width: 50px; height: 50px; border-radius: 50%; object-fit: cover;
  border: 3px solid var(--sky);
}
.author-name { font-weight: 600; font-size: .95rem; }
.author-loc { font-size: .8rem; color: var(--gray); }
.stars { color: var(--gold); font-size: .85rem; }

/* ===================== HOME – DISCOUNT BANNER ===================== */
.discount-banner {
  background: linear-gradient(135deg, var(--navy) 0%, var(--ocean) 50%, var(--sky) 100%);
  border-radius: 28px;
  margin: 0 5% 80px;
  padding: 60px 8%;
  display: flex; align-items: center; justify-content: space-between; gap: 2rem;
  flex-wrap: wrap;
  overflow: hidden;
  position: relative;
}
.discount-banner::before {
  content: '';
  position: absolute; top: -60px; right: -60px;
  width: 300px; height: 300px;
  border-radius: 50%;
  background: rgba(255,255,255,.06);
}
.discount-banner::after {
  content: '';
  position: absolute; bottom: -80px; right: 100px;
  width: 200px; height: 200px;
  border-radius: 50%;
  background: rgba(255,255,255,.04);
}
.discount-text { color: var(--white); }
.discount-badge {
  background: var(--gold); color: var(--navy);
  font-weight: 700; font-size: .78rem; letter-spacing: .1em; text-transform: uppercase;
  padding: 5px 14px; border-radius: 50px; display: inline-block; margin-bottom: 1rem;
}
.discount-text h2 { font-size: clamp(1.8rem, 4vw, 2.8rem); margin-bottom: .5rem; }
.discount-text p { opacity: .82; font-size: 1rem; }
.discount-code {
  background: rgba(255,255,255,.12); border: 2px dashed rgba(255,255,255,.4);
  color: var(--white); padding: 14px 28px; border-radius: 14px;
  font-family: 'Playfair Display', serif; font-size: 1.6rem; font-weight: 700;
  letter-spacing: .2em; text-align: center;
}
.discount-code small { display: block; font-family: 'DM Sans', sans-serif; font-size: .75rem; opacity: .7; font-weight: 400; letter-spacing: .05em; margin-top: 4px; }

/* ===================== DESTINATIONS PAGE ===================== */
.dest-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 2rem;
}
.dest-card {
  border-radius: 24px; overflow: hidden;
  box-shadow: var(--card-shadow);
  background: var(--white);
  transition: transform var(--transition), box-shadow var(--transition);
}
.dest-card:hover { transform: translateY(-10px); box-shadow: 0 24px 56px rgba(10,35,66,.18); }
.dest-img-wrap { height: 240px; overflow: hidden; position: relative; }
.dest-img-wrap img { height: 100%; transition: transform .6s ease; }
.dest-card:hover .dest-img-wrap img { transform: scale(1.12); }
.dest-badge {
  position: absolute; top: 16px; right: 16px;
  background: var(--sky); color: var(--white);
  font-size: .75rem; font-weight: 600; padding: 4px 12px; border-radius: 50px;
}
.dest-body { padding: 1.5rem; }
.dest-body h3 { font-size: 1.4rem; margin-bottom: .3rem; }
.dest-meta { display: flex; gap: 1rem; color: var(--gray); font-size: .82rem; margin-bottom: .75rem; }
.dest-meta span { display: flex; align-items: center; gap: .3rem; }
.dest-body p { color: var(--gray); font-size: .9rem; line-height: 1.65; margin-bottom: 1.2rem; }
.dest-footer { display: flex; align-items: center; justify-content: space-between; }
.dest-price { font-family: 'Playfair Display', serif; font-size: 1.5rem; font-weight: 700; color: var(--ocean); }
.dest-price span { font-family: 'DM Sans', sans-serif; font-size: .78rem; color: var(--gray); font-weight: 400; }

/* ===================== PACKAGES PAGE ===================== */
.packages-hero {
  background: linear-gradient(135deg, var(--navy), var(--ocean));
  padding: 100px 5% 80px;
  text-align: center;
  color: var(--white);
}
.packages-hero h1 { font-size: clamp(2rem, 5vw, 3.5rem); margin-bottom: .75rem; }
.packages-hero p { opacity: .82; font-size: 1.05rem; max-width: 500px; margin: 0 auto; }
.pkg-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 2rem;
}
.pkg-card {
  border-radius: 24px; overflow: hidden;
  box-shadow: var(--card-shadow);
  background: var(--white);
  transition: transform var(--transition), box-shadow var(--transition);
  position: relative;
}
.pkg-card.featured { border: 3px solid var(--sky); }
.pkg-card:hover { transform: translateY(-10px); box-shadow: 0 24px 56px rgba(10,35,66,.18); }
.pkg-tag {
  position: absolute; top: 20px; left: 20px;
  background: var(--gold); color: var(--navy);
  font-size: .72rem; font-weight: 700; padding: 4px 12px; border-radius: 50px;
  letter-spacing: .06em; text-transform: uppercase;
}
.pkg-img { height: 200px; }
.pkg-body { padding: 1.75rem; }
.pkg-body h3 { font-size: 1.35rem; margin-bottom: .75rem; }
.pkg-features { margin-bottom: 1.25rem; }
.pkg-features li {
  display: flex; align-items: center; gap: .6rem;
  font-size: .88rem; color: var(--gray); padding: .3rem 0;
}
.pkg-features li i { color: var(--mint); width: 16px; }
.pkg-footer { display: flex; align-items: center; justify-content: space-between; padding-top: 1rem; border-top: 1px solid var(--foam); }
.pkg-price { font-family: 'Playfair Display', serif; }
.pkg-price .amount { font-size: 1.8rem; font-weight: 700; color: var(--ocean); }
.pkg-price .per { font-size: .78rem; color: var(--gray); }
.pkg-duration { font-size: .82rem; color: var(--gray); display: flex; align-items: center; gap: .3rem; }

/* ===================== GALLERY PAGE ===================== */
.gallery-hero {
  background: linear-gradient(135deg, var(--ocean), var(--mint));
  padding: 100px 5% 80px;
  text-align: center; color: var(--white);
}
.gallery-hero h1 { font-size: clamp(2rem, 5vw, 3.5rem); margin-bottom: .75rem; }
.gallery-hero p { opacity: .82; font-size: 1.05rem; }
.gallery-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: 220px;
  gap: 1rem;
}
.g-item {
  border-radius: 16px; overflow: hidden;
  position: relative; cursor: pointer;
}
.g-item.wide { grid-column: span 2; }
.g-item.tall { grid-row: span 2; }
.g-item img { height: 100%; transition: transform .5s ease; }
.g-item:hover img { transform: scale(1.08); }
.g-overlay {
  position: absolute; inset: 0;
  background: linear-gradient(to top, rgba(10,35,66,.8), transparent 50%);
  opacity: 0; transition: opacity var(--transition);
  display: flex; align-items: flex-end;
  padding: 1.25rem;
}
.g-item:hover .g-overlay { opacity: 1; }
.g-overlay span { color: var(--white); font-size: .9rem; font-weight: 500; }

/* ===================== ABOUT PAGE ===================== */
.about-hero {
  background: url('https://images.unsplash.com/photo-1488646953014-85cb44e25828?w=1600&q=80') center/cover no-repeat;
  position: relative;
  padding: 160px 5% 100px;
  color: var(--white);
}
.about-hero::before { content: ''; position: absolute; inset: 0; background: linear-gradient(135deg, rgba(10,35,66,.92), rgba(26,107,138,.7)); }
.about-hero-content { position: relative; z-index: 1; max-width: 620px; }
.about-hero h1 { font-size: clamp(2.2rem, 5vw, 4rem); margin-bottom: 1rem; }
.about-hero p { font-size: 1.1rem; opacity: .85; line-height: 1.75; }
.about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 5rem; align-items: center; }
.about-img-wrap { border-radius: 24px; overflow: hidden; height: 480px; box-shadow: var(--card-shadow); }
.about-text h2 { font-size: clamp(1.8rem, 3vw, 2.5rem); margin-bottom: 1rem; }
.about-text p { color: var(--gray); line-height: 1.8; margin-bottom: 1rem; }
.mission-cards { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 2rem; }
.mission-card {
  background: var(--foam); border-radius: 16px; padding: 1.25rem;
}
.mission-card h4 { font-size: 1rem; margin-bottom: .4rem; color: var(--ocean); }
.mission-card p { font-size: .85rem; color: var(--gray); line-height: 1.6; }
.why-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 1.5rem;
}
.why-card {
  text-align: center; padding: 2.5rem 1.5rem;
  border-radius: 20px; background: var(--white);
  box-shadow: var(--card-shadow);
  transition: transform var(--transition);
}
.why-card:hover { transform: translateY(-6px); }
.why-icon {
  width: 70px; height: 70px; border-radius: 50%;
  background: linear-gradient(135deg, var(--sky), var(--mint));
  display: flex; align-items: center; justify-content: center;
  font-size: 1.7rem; color: var(--white);
  margin: 0 auto 1.25rem;
}
.why-card h4 { font-size: 1.1rem; margin-bottom: .5rem; }
.why-card p { color: var(--gray); font-size: .88rem; line-height: 1.65; }

/* ===================== CONTACT PAGE ===================== */
.contact-hero {
  background: linear-gradient(135deg, var(--navy), var(--sky));
  padding: 100px 5% 80px; text-align: center; color: var(--white);
}
.contact-hero h1 { font-size: clamp(2rem, 5vw, 3.5rem); margin-bottom: .75rem; }
.contact-hero p { opacity: .82; font-size: 1.05rem; }
.contact-grid { display: grid; grid-template-columns: 1fr 1.5fr; gap: 4rem; align-items: start; }
.contact-info h3 { font-size: 1.5rem; margin-bottom: 1.25rem; }
.contact-info p { color: var(--gray); line-height: 1.75; margin-bottom: 2rem; }
.contact-items { display: flex; flex-direction: column; gap: 1.25rem; }
.contact-item { display: flex; gap: 1rem; align-items: flex-start; }
.c-icon {
  width: 48px; height: 48px; border-radius: 12px; flex-shrink: 0;
  background: linear-gradient(135deg, var(--sky), var(--mint));
  display: flex; align-items: center; justify-content: center;
  font-size: 1.1rem; color: var(--white);
}
.c-text strong { display: block; font-weight: 600; margin-bottom: .2rem; }
.c-text span { color: var(--gray); font-size: .9rem; }
.contact-form {
  background: var(--white); border-radius: 24px;
  padding: 2.5rem; box-shadow: var(--card-shadow);
}
.contact-form h3 { font-size: 1.5rem; margin-bottom: 2rem; }
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
.form-group { margin-bottom: 1.25rem; }
.form-group label { display: block; font-size: .85rem; font-weight: 600; margin-bottom: .5rem; color: var(--navy); }
.form-group input, .form-group select, .form-group textarea {
  width: 100%;
  padding: 13px 18px;
  border: 2px solid #e5e7eb;
  border-radius: 12px;
  font-family: 'DM Sans', sans-serif; font-size: .95rem;
  color: var(--navy);
  transition: border-color var(--transition), box-shadow var(--transition);
  outline: none;
}
.form-group input:focus, .form-group select:focus, .form-group textarea:focus {
  border-color: var(--sky);
  box-shadow: 0 0 0 4px rgba(56,182,216,.12);
}
.form-group textarea { resize: vertical; min-height: 130px; }
.form-success {
  display: none; text-align: center; padding: 2rem;
  color: var(--mint); font-size: 1.1rem;
}
.form-success i { font-size: 3rem; display: block; margin-bottom: 1rem; }

/* ===================== FOOTER ===================== */
footer {
  background: var(--navy);
  color: rgba(255,255,255,.75);
  padding: 70px 5% 0;
}
.footer-grid {
  display: grid;
  grid-template-columns: 1.5fr 1fr 1fr 1fr;
  gap: 3rem;
  padding-bottom: 50px;
  border-bottom: 1px solid rgba(255,255,255,.1);
}
.footer-brand .logo { font-size: 1.5rem; margin-bottom: 1rem; }
.footer-brand p { font-size: .9rem; line-height: 1.75; max-width: 260px; }
.social-links { display: flex; gap: .75rem; margin-top: 1.5rem; }
.social-link {
  width: 40px; height: 40px; border-radius: 10px;
  background: rgba(255,255,255,.08);
  display: flex; align-items: center; justify-content: center;
  font-size: .95rem; color: rgba(255,255,255,.7);
  transition: background var(--transition), color var(--transition), transform var(--transition);
  cursor: pointer;
}
.social-link:hover { background: var(--sky); color: var(--white); transform: translateY(-3px); }
.footer-col h4 { color: var(--white); font-size: 1rem; margin-bottom: 1.25rem; }
.footer-col ul li { margin-bottom: .6rem; }
.footer-col ul li a {
  font-size: .88rem; color: rgba(255,255,255,.65);
  transition: color var(--transition); cursor: pointer;
}
.footer-col ul li a:hover { color: var(--sky); }
.footer-bottom {
  padding: 20px 0;
  display: flex; align-items: center; justify-content: space-between;
  font-size: .82rem; color: rgba(255,255,255,.45);
  flex-wrap: wrap; gap: 1rem;
}

/* ===================== ANIMATIONS ===================== */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(30px); }
  to   { opacity: 1; transform: translateY(0); }
}
.fade-up { opacity: 0; transform: translateY(24px); animation: fadeUp .7s ease forwards; }

/* ===================== RESPONSIVE ===================== */
@media (max-width: 1024px) {
  .gallery-grid { grid-template-columns: repeat(3, 1fr); }
  .footer-grid { grid-template-columns: 1fr 1fr; gap: 2rem; }
  .about-grid { grid-template-columns: 1fr; gap: 3rem; }
  .contact-grid { grid-template-columns: 1fr; }
}
@media (max-width: 768px) {
  .nav-links { display: none; flex-direction: column; position: fixed; top: 70px; left: 0; right: 0; background: var(--navy); padding: 2rem; gap: 1rem; z-index: 999; }
  .nav-links.open { display: flex; }
  .nav-links a { font-size: 1rem; padding: .5rem 0; }
  .hamburger { display: flex; }
  .hero-stats { flex-wrap: wrap; justify-content: center; gap: 1.5rem; padding: 16px 24px; }
  .gallery-grid { grid-template-columns: repeat(2, 1fr); }
  .g-item.wide { grid-column: span 1; }
  .footer-grid { grid-template-columns: 1fr; }
  .form-row { grid-template-columns: 1fr; }
  .discount-banner { text-align: center; justify-content: center; }
  .mission-cards { grid-template-columns: 1fr; }
}
@media (max-width: 480px) {
  .gallery-grid { grid-template-columns: 1fr; }
  .g-item.tall { grid-row: span 1; }
}
</style>
</head>
<body>

<!-- ============ NAV ============ -->
<nav>
  <div class="logo">Wander<span>World</span></div>
  <div class="nav-links" id="navLinks">
    <a onclick="showPage('home')" class="active" id="nav-home">Home</a>
    <a onclick="showPage('destinations')" id="nav-destinations">Destinations</a>
    <a onclick="showPage('packages')" id="nav-packages">Packages</a>
    <a onclick="showPage('gallery')" id="nav-gallery">Gallery</a>
    <a onclick="showPage('about')" id="nav-about">About</a>
    <a onclick="showPage('contact')" id="nav-contact" class="nav-cta">Contact Us</a>
  </div>
  <div class="hamburger" id="hamburger" onclick="toggleMenu()">
    <span></span><span></span><span></span>
  </div>
</nav>

<!-- ============================================================ -->
<!-- HOME PAGE -->
<!-- ============================================================ -->
<div class="page active" id="page-home">

  <!-- Hero -->
  <section class="hero">
    <div class="hero-bg"></div>
    <div class="hero-overlay"></div>
    <div class="hero-content">
      <div class="hero-badge"><i class="fa-solid fa-compass"></i> Your Ultimate Travel Partner</div>
      <h1 class="hero-title">Explore the World<br>with <span>WanderWorld</span></h1>
      <p class="hero-sub">Discover breathtaking destinations, curated travel packages, and unforgettable experiences crafted just for you.</p>
      <div class="hero-btns">
        <button class="btn btn-primary" onclick="showPage('destinations')"><i class="fa-solid fa-map-location-dot"></i> Explore Now</button>
        <button class="btn btn-outline" onclick="showPage('packages')"><i class="fa-solid fa-suitcase-rolling"></i> View Packages</button>
      </div>
    </div>
    <div class="hero-stats">
      <div class="stat-item"><div class="stat-num">50K+</div><div class="stat-lbl">Happy Travelers</div></div>
      <div class="stat-item"><div class="stat-num">120+</div><div class="stat-lbl">Destinations</div></div>
      <div class="stat-item"><div class="stat-num">98%</div><div class="stat-lbl">Satisfaction</div></div>
      <div class="stat-item"><div class="stat-num">15+</div><div class="stat-lbl">Years Experience</div></div>
    </div>
  </section>

  <!-- Top 10 Places -->
  <section class="section">
    <div class="section-header">
      <div class="section-label"><i class="fa-solid fa-star"></i> Editor's Choice</div>
      <h2 class="section-title">Top <span>10</span> Places to Visit</h2>
      <p class="section-sub">Handpicked destinations loved by thousands of wanderers around the globe.</p>
    </div>
    <div class="places-grid">
      <div class="place-card"><div class="place-rank">#1</div><img src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=600&q=80" alt="Paris"><div class="place-card-overlay"></div><div class="place-card-info"><h3>Paris, France</h3><p>City of Light & Love</p><div class="rating">★★★★★ 4.9</div></div></div>
      <div class="place-card"><div class="place-rank">#2</div><img src="https://images.unsplash.com/photo-1537996194471-e657df975ab4?w=600&q=80" alt="Bali"><div class="place-card-overlay"></div><div class="place-card-info"><h3>Bali, Indonesia</h3><p>Island of the Gods</p><div class="rating">★★★★★ 4.8</div></div></div>
      <div class="place-card"><div class="place-rank">#3</div><img src="https://images.unsplash.com/photo-1512453979798-5ea266f8880c?w=600&q=80" alt="Dubai"><div class="place-card-overlay"></div><div class="place-card-info"><h3>Dubai, UAE</h3><p>Where Dreams Come True</p><div class="rating">★★★★★ 4.8</div></div></div>
      <div class="place-card"><div class="place-rank">#4</div><img src="https://images.unsplash.com/photo-1596178065887-1198b6148b2b?w=600&q=80" alt="Maldives"><div class="place-card-overlay"></div><div class="place-card-info"><h3>Maldives</h3><p>Tropical Paradise</p><div class="rating">★★★★★ 4.9</div></div></div>
      <div class="place-card"><div class="place-rank">#5</div><img src="https://images.unsplash.com/photo-1548013146-72479768bada?w=600&q=80" alt="Rajasthan"><div class="place-card-overlay"></div><div class="place-card-info"><h3>Rajasthan, India</h3><p>Land of Maharajas</p><div class="rating">★★★★☆ 4.7</div></div></div>
      <div class="place-card"><div class="place-rank">#6</div><img src="https://images.unsplash.com/photo-1530973428-5bf2db2e4d71?w=600&q=80" alt="Santorini"><div class="place-card-overlay"></div><div class="place-card-info"><h3>Santorini, Greece</h3><p>Aegean Sea Gem</p><div class="rating">★★★★★ 4.9</div></div></div>
      <div class="place-card"><div class="place-rank">#7</div><img src="https://images.unsplash.com/photo-1549693578-d683be217e58?w=600&q=80" alt="Swiss Alps"><div class="place-card-overlay"></div><div class="place-card-info"><h3>Swiss Alps</h3><p>Majestic Mountain Peaks</p><div class="rating">★★★★★ 4.9</div></div></div>
      <div class="place-card"><div class="place-rank">#8</div><img src="https://images.unsplash.com/photo-1506905925346-21bda4d32df4?w=600&q=80" alt="Iceland"><div class="place-card-overlay"></div><div class="place-card-info"><h3>Iceland</h3><p>Land of Fire & Ice</p><div class="rating">★★★★☆ 4.7</div></div></div>
      <div class="place-card"><div class="place-rank">#9</div><img src="https://images.unsplash.com/photo-1580655653885-65763b2597d1?w=600&q=80" alt="Tokyo"><div class="place-card-overlay"></div><div class="place-card-info"><h3>Tokyo, Japan</h3><p>Neon Lights & Cherry Blossoms</p><div class="rating">★★★★☆ 4.8</div></div></div>
      <div class="place-card"><div class="place-rank">#10</div><img src="https://images.unsplash.com/photo-1518684079-3c830dcef090?w=600&q=80" alt="Turkey"><div class="place-card-overlay"></div><div class="place-card-info"><h3>Istanbul, Turkey</h3><p>Where East Meets West</p><div class="rating">★★★★☆ 4.6</div></div></div>
    </div>
  </section>

  <!-- Travel Tips -->
  <section class="section tips-section">
    <div class="section-header">
      <div class="section-label"><i class="fa-solid fa-lightbulb"></i> Travel Smart</div>
      <h2 class="section-title">Essential <span>Travel Tips</span></h2>
      <p class="section-sub">Make every journey smooth, safe, and memorable with our expert advice.</p>
    </div>
    <div class="tips-grid">
      <div class="tip-card"><div class="tip-icon"><i class="fa-solid fa-passport"></i></div><h4>Documents First</h4><p>Always keep digital and physical copies of your passport, visa, insurance, and bookings. Store them in a secure cloud.</p></div>
      <div class="tip-card"><div class="tip-icon"><i class="fa-solid fa-shield-halved"></i></div><h4>Travel Insurance</h4><p>Never skip travel insurance. It covers medical emergencies, trip cancellations, and lost baggage — a real lifesaver.</p></div>
      <div class="tip-card"><div class="tip-icon"><i class="fa-solid fa-suitcase"></i></div><h4>Pack Light & Smart</h4><p>Use rolling clothes, packing cubes, and multi-purpose items. Leave room for souvenirs and check airline baggage rules.</p></div>
      <div class="tip-card"><div class="tip-icon"><i class="fa-solid fa-coins"></i></div><h4>Budget Wisely</h4><p>Carry local currency, inform your bank of travel dates, and use travel credit cards with no foreign transaction fees.</p></div>
      <div class="tip-card"><div class="tip-icon"><i class="fa-solid fa-wifi"></i></div><h4>Stay Connected</h4><p>Get a local SIM or international eSIM. Download offline maps, translation apps, and key travel guides before departing.</p></div>
      <div class="tip-card"><div class="tip-icon"><i class="fa-solid fa-heart-pulse"></i></div><h4>Health & Safety</h4><p>Research vaccinations needed, carry a basic first-aid kit, and save local emergency numbers as soon as you arrive.</p></div>
    </div>
  </section>

  <!-- Testimonials -->
  <section class="section">
    <div class="section-header">
      <div class="section-label"><i class="fa-solid fa-quote-left"></i> Traveler Stories</div>
      <h2 class="section-title">What Our <span>Travelers Say</span></h2>
      <p class="section-sub">Real experiences from real wanderers who chose WanderWorld for their adventures.</p>
    </div>
    <div class="testimonials-grid">
      <div class="testimonial-card"><p>"WanderWorld made our honeymoon in Maldives absolutely magical. Every detail was perfectly planned — the private beach villa, sunset cruise, and candlelight dinner. We'll remember it forever!"</p><div class="testimonial-author"><img class="author-avatar" src="https://i.pravatar.cc/100?img=47" alt="Priya"><div><div class="author-name">Priya & Rahul Sharma</div><div class="author-loc"><i class="fa-solid fa-location-dot"></i> Mumbai, India</div><div class="stars">★★★★★</div></div></div></div>
      <div class="testimonial-card"><p>"The Bali Adventure package exceeded all my expectations. The itinerary was perfectly balanced with cultural visits, beach time, and thrilling activities. The guides were incredibly knowledgeable and friendly!"</p><div class="testimonial-author"><img class="author-avatar" src="https://i.pravatar.cc/100?img=12" alt="Alex"><div><div class="author-name">Alex Thompson</div><div class="author-loc"><i class="fa-solid fa-location-dot"></i> London, UK</div><div class="stars">★★★★★</div></div></div></div>
      <div class="testimonial-card"><p>"Traveled solo to Japan with WanderWorld's Solo Explorer package. The 24/7 support was reassuring, and I met incredible fellow travelers. The cherry blossom season timing was spot on!"</p><div class="testimonial-author"><img class="author-avatar" src="https://i.pravatar.cc/100?img=25" alt="Sara"><div><div class="author-name">Sara Mendonca</div><div class="author-loc"><i class="fa-solid fa-location-dot"></i> Goa, India</div><div class="stars">★★★★★</div></div></div></div>
      <div class="testimonial-card"><p>"The family package to Rajasthan was phenomenal. Kids loved the elephant safari and puppet shows while we enjoyed the heritage hotels. WanderWorld takes care of every age group!"</p><div class="testimonial-author"><img class="author-avatar" src="https://i.pravatar.cc/100?img=33" alt="Vikram"><div><div class="author-name">Vikram Patel Family</div><div class="author-loc"><i class="fa-solid fa-location-dot"></i> Ahmedabad, India</div><div class="stars">★★★★★</div></div></div></div>
      <div class="testimonial-card"><p>"Our Paris trip was straight out of a movie. WanderWorld arranged skip-the-line access to the Louvre and Eiffel Tower, and the boutique hotel they chose had the most stunning views of the Seine."</p><div class="testimonial-author"><img class="author-avatar" src="https://i.pravatar.cc/100?img=44" alt="Emma"><div><div class="author-name">Emma & James Wilson</div><div class="author-loc"><i class="fa-solid fa-location-dot"></i> Sydney, Australia</div><div class="stars">★★★★★</div></div></div></div>
      <div class="testimonial-card"><p>"Third time booking with WanderWorld and they keep getting better! This year's Kashmir trip was breathtaking — snow-capped peaks, Dal Lake shikaras, and authentic Wazwan cuisine. Pure bliss."</p><div class="testimonial-author"><img class="author-avatar" src="https://i.pravatar.cc/100?img=60" alt="Aisha"><div><div class="author-name">Aisha Khan</div><div class="author-loc"><i class="fa-solid fa-location-dot"></i> Delhi, India</div><div class="stars">★★★★★</div></div></div></div>
    </div>
  </section>

  <!-- Discount Banner -->
  <div class="discount-banner">
    <div class="discount-text">
      <div class="discount-badge">🎉 Limited Time Offer</div>
      <h2>Get 30% Off on All<br>International Packages!</h2>
      <p>Book before 31st December 2025 and unlock exclusive savings.<br>Terms & conditions apply.</p>
      <button class="btn btn-primary" style="margin-top:1.5rem" onclick="showPage('packages')"><i class="fa-solid fa-tags"></i> Claim Offer Now</button>
    </div>
    <div class="discount-code">WANDER30<small>Use this code at checkout</small></div>
  </div>

</div>
<!-- END HOME -->

<!-- ============================================================ -->
<!-- DESTINATIONS PAGE -->
<!-- ============================================================ -->
<div class="page" id="page-destinations">
  <div style="background:linear-gradient(135deg,var(--navy),var(--ocean));padding:100px 5% 80px;text-align:center;color:#fff">
    <div class="section-label" style="margin:0 auto 1rem"><i class="fa-solid fa-globe"></i> Explore Our World</div>
    <h1 style="font-size:clamp(2rem,5vw,3.5rem);margin-bottom:.75rem">Popular <span style="color:var(--sky)">Destinations</span></h1>
    <p style="opacity:.82;font-size:1.05rem;max-width:520px;margin:0 auto">From serene beaches to majestic mountains — find your perfect escape.</p>
  </div>
  <section class="section">
    <div class="dest-grid">

      <div class="dest-card">
        <div class="dest-img-wrap"><img src="https://images.unsplash.com/photo-1512343879784-a960bf40e7f2?w=600&q=80" alt="Goa"><div class="dest-badge">🇮🇳 India</div></div>
        <div class="dest-body">
          <h3>Goa</h3>
          <div class="dest-meta"><span><i class="fa-solid fa-sun"></i> Nov – Feb</span><span><i class="fa-solid fa-temperature-half"></i> 25–32°C</span><span><i class="fa-solid fa-star" style="color:var(--gold)"></i> 4.7</span></div>
          <p>Sun-drenched beaches, vibrant nightlife, colonial Portuguese architecture, and fresh seafood make Goa India's most beloved coastal destination.</p>
          <div class="dest-footer"><div class="dest-price">₹15,000 <span>/person</span></div><button class="btn btn-primary" style="padding:10px 22px;font-size:.85rem" onclick="showPage('packages')">Book Now</button></div>
        </div>
      </div>

      <div class="dest-card">
        <div class="dest-img-wrap"><img src="https://images.unsplash.com/photo-1626621341517-bbf3d9990a23?w=600&q=80" alt="Manali"><div class="dest-badge">🇮🇳 India</div></div>
        <div class="dest-body">
          <h3>Manali</h3>
          <div class="dest-meta"><span><i class="fa-solid fa-snowflake"></i> Dec – Jan</span><span><i class="fa-solid fa-temperature-half"></i> -2–15°C</span><span><i class="fa-solid fa-star" style="color:var(--gold)"></i> 4.8</span></div>
          <p>Snow-capped Himalayan peaks, adventure sports, ancient monasteries, and the roaring Beas River make Manali a year-round mountain paradise.</p>
          <div class="dest-footer"><div class="dest-price">₹18,000 <span>/person</span></div><button class="btn btn-primary" style="padding:10px 22px;font-size:.85rem" onclick="showPage('packages')">Book Now</button></div>
        </div>
      </div>

      <div class="dest-card">
        <div class="dest-img-wrap"><img src="https://images.unsplash.com/photo-1566737236500-c8ac43014a67?w=600&q=80" alt="Kashmir"><div class="dest-badge">🇮🇳 India</div></div>
        <div class="dest-body">
          <h3>Kashmir</h3>
          <div class="dest-meta"><span><i class="fa-solid fa-leaf"></i> Apr – Oct</span><span><i class="fa-solid fa-temperature-half"></i> 5–25°C</span><span><i class="fa-solid fa-star" style="color:var(--gold)"></i> 4.9</span></div>
          <p>Dal Lake houseboats, Mughal gardens blooming with tulips, shikara rides at dawn, and saffron fields — Kashmir truly is heaven on earth.</p>
          <div class="dest-footer"><div class="dest-price">₹22,000 <span>/person</span></div><button class="btn btn-primary" style="padding:10px 22px;font-size:.85rem" onclick="showPage('packages')">Book Now</button></div>
        </div>
      </div>

      <div class="dest-card">
        <div class="dest-img-wrap"><img src="https://images.unsplash.com/photo-1512453979798-5ea266f8880c?w=600&q=80" alt="Dubai"><div class="dest-badge">🇦🇪 UAE</div></div>
        <div class="dest-body">
          <h3>Dubai</h3>
          <div class="dest-meta"><span><i class="fa-solid fa-sun"></i> Oct – Apr</span><span><i class="fa-solid fa-temperature-half"></i> 20–35°C</span><span><i class="fa-solid fa-star" style="color:var(--gold)"></i> 4.8</span></div>
          <p>Futuristic skylines, record-breaking malls, desert safaris, and luxury beyond imagination — Dubai is where opulence meets adventure.</p>
          <div class="dest-footer"><div class="dest-price">₹65,000 <span>/person</span></div><button class="btn btn-primary" style="padding:10px 22px;font-size:.85rem" onclick="showPage('packages')">Book Now</button></div>
        </div>
      </div>

      <div class="dest-card">
        <div class="dest-img-wrap"><img src="https://images.unsplash.com/photo-1499856871958-5b9627545d1a?w=600&q=80" alt="Paris"><div class="dest-badge">🇫🇷 France</div></div>
        <div class="dest-body">
          <h3>Paris</h3>
          <div class="dest-meta"><span><i class="fa-solid fa-leaf"></i> Apr – Jun</span><span><i class="fa-solid fa-temperature-half"></i> 10–25°C</span><span><i class="fa-solid fa-star" style="color:var(--gold)"></i> 4.9</span></div>
          <p>The Eiffel Tower at twilight, world-class cuisine, iconic art museums, charming cafés, and the romantic Seine River — Paris is timeless.</p>
          <div class="dest-footer"><div class="dest-price">₹1,20,000 <span>/person</span></div><button class="btn btn-primary" style="padding:10px 22px;font-size:.85rem" onclick="showPage('packages')">Book Now</button></div>
        </div>
      </div>

      <div class="dest-card">
        <div class="dest-img-wrap"><img src="https://images.unsplash.com/photo-1537996194471-e657df975ab4?w=600&q=80" alt="Bali"><div class="dest-badge">🇮🇩 Indonesia</div></div>
        <div class="dest-body">
          <h3>Bali</h3>
          <div class="dest-meta"><span><i class="fa-solid fa-sun"></i> Apr – Sep</span><span><i class="fa-solid fa-temperature-half"></i> 26–30°C</span><span><i class="fa-solid fa-star" style="color:var(--gold)"></i> 4.8</span></div>
          <p>Terraced rice paddies, spiritual temples, world-class surf breaks, healing wellness retreats, and a vibrant arts scene define beautiful Bali.</p>
          <div class="dest-footer"><div class="dest-price">₹55,000 <span>/person</span></div><button class="btn btn-primary" style="padding:10px 22px;font-size:.85rem" onclick="showPage('packages')">Book Now</button></div>
        </div>
      </div>

    </div>
  </section>
</div>
<!-- END DESTINATIONS -->

<!-- ============================================================ -->
<!-- PACKAGES PAGE -->
<!-- ============================================================ -->
<div class="page" id="page-packages">
  <div class="packages-hero">
    <div class="section-label" style="margin:0 auto 1rem;color:rgba(255,255,255,.85)"><i class="fa-solid fa-tag"></i> Our Offers</div>
    <h1>Travel <span style="color:var(--sky)">Packages</span></h1>
    <p>Thoughtfully designed packages for every kind of traveler. All-inclusive, hassle-free adventures await.</p>
  </div>
  <section class="section">
    <div class="pkg-grid">

      <div class="pkg-card">
        <div class="pkg-tag">🎒 Solo</div>
        <div class="pkg-img"><img src="https://images.unsplash.com/photo-1501555088652-021faa106b9b?w=600&q=80" alt="Solo Trip"></div>
        <div class="pkg-body">
          <h3>Solo Explorer</h3>
          <ul class="pkg-features">
            <li><i class="fa-solid fa-check"></i> 3-Star Accommodation (7 Nights)</li>
            <li><i class="fa-solid fa-check"></i> Daily Breakfast Included</li>
            <li><i class="fa-solid fa-check"></i> Airport Transfers</li>
            <li><i class="fa-solid fa-check"></i> City Guided Tours</li>
            <li><i class="fa-solid fa-check"></i> 24/7 Travel Support</li>
            <li><i class="fa-solid fa-check"></i> Travel Insurance</li>
          </ul>
          <div class="pkg-footer">
            <div>
              <div class="pkg-price"><span class="amount">₹25,000</span></div>
              <div class="pkg-price"><span class="per">per person</span></div>
            </div>
            <div style="text-align:right">
              <div class="pkg-duration"><i class="fa-solid fa-clock"></i> 7 Nights / 8 Days</div>
              <button class="btn btn-primary" style="margin-top:.6rem;padding:10px 20px;font-size:.85rem" onclick="showPage('contact')">Book Now</button>
            </div>
          </div>
        </div>
      </div>

      <div class="pkg-card featured">
        <div class="pkg-tag">👨‍👩‍👧‍👦 Popular</div>
        <div class="pkg-img"><img src="https://images.unsplash.com/photo-1476514525535-07fb3b4ae5f1?w=600&q=80" alt="Family Trip"></div>
        <div class="pkg-body">
          <h3>Family Bliss</h3>
          <ul class="pkg-features">
            <li><i class="fa-solid fa-check"></i> 4-Star Family Suites (6 Nights)</li>
            <li><i class="fa-solid fa-check"></i> Breakfast & Dinner Buffet</li>
            <li><i class="fa-solid fa-check"></i> Kids' Activities & Club</li>
            <li><i class="fa-solid fa-check"></i> Private Family Transfers</li>
            <li><i class="fa-solid fa-check"></i> Theme Park Tickets</li>
            <li><i class="fa-solid fa-check"></i> Travel Insurance (Family)</li>
          </ul>
          <div class="pkg-footer">
            <div>
              <div class="pkg-price"><span class="amount">₹85,000</span></div>
              <div class="pkg-price"><span class="per">for 4 members</span></div>
            </div>
            <div style="text-align:right">
              <div class="pkg-duration"><i class="fa-solid fa-clock"></i> 6 Nights / 7 Days</div>
              <button class="btn btn-primary" style="margin-top:.6rem;padding:10px 20px;font-size:.85rem" onclick="showPage('contact')">Book Now</button>
            </div>
          </div>
        </div>
      </div>

      <div class="pkg-card">
        <div class="pkg-tag" style="background:var(--mint)">💑 Romance</div>
        <div class="pkg-img"><img src="https://images.unsplash.com/photo-1436491865332-7a61a109cc05?w=600&q=80" alt="Honeymoon"></div>
        <div class="pkg-body">
          <h3>Honeymoon Escape</h3>
          <ul class="pkg-features">
            <li><i class="fa-solid fa-check"></i> 5-Star Luxury Resort (5 Nights)</li>
            <li><i class="fa-solid fa-check"></i> Candlelight Dinner on Beach</li>
            <li><i class="fa-solid fa-check"></i> Couples Spa & Massage</li>
            <li><i class="fa-solid fa-check"></i> Sunrise Boat Cruise</li>
            <li><i class="fa-solid fa-check"></i> Complimentary Room Décor</li>
            <li><i class="fa-solid fa-check"></i> Dedicated Personal Butler</li>
          </ul>
          <div class="pkg-footer">
            <div>
              <div class="pkg-price"><span class="amount">₹1,10,000</span></div>
              <div class="pkg-price"><span class="per">per couple</span></div>
            </div>
            <div style="text-align:right">
              <div class="pkg-duration"><i class="fa-solid fa-clock"></i> 5 Nights / 6 Days</div>
              <button class="btn btn-primary" style="margin-top:.6rem;padding:10px 20px;font-size:.85rem" onclick="showPage('contact')">Book Now</button>
            </div>
          </div>
        </div>
      </div>

      <div class="pkg-card">
        <div class="pkg-tag" style="background:#e05c2a">🏔️ Adventure</div>
        <div class="pkg-img"><img src="https://images.unsplash.com/photo-1551632811-561732d1e306?w=600&q=80" alt="Adventure"></div>
        <div class="pkg-body">
          <h3>Adventure Tour</h3>
          <ul class="pkg-features">
            <li><i class="fa-solid fa-check"></i> Camping & Glamping (8 Nights)</li>
            <li><i class="fa-solid fa-check"></i> Trekking & Mountaineering</li>
            <li><i class="fa-solid fa-check"></i> White-Water Rafting</li>
            <li><i class="fa-solid fa-check"></i> Paragliding & Zip-lining</li>
            <li><i class="fa-solid fa-check"></i> Expert Adventure Guides</li>
            <li><i class="fa-solid fa-check"></i> All Safety Gear Provided</li>
          </ul>
          <div class="pkg-footer">
            <div>
              <div class="pkg-price"><span class="amount">₹45,000</span></div>
              <div class="pkg-price"><span class="per">per person</span></div>
            </div>
            <div style="text-align:right">
              <div class="pkg-duration"><i class="fa-solid fa-clock"></i> 8 Nights / 9 Days</div>
              <button class="btn btn-primary" style="margin-top:.6rem;padding:10px 20px;font-size:.85rem" onclick="showPage('contact')">Book Now</button>
            </div>
          </div>
        </div>
      </div>

    </div>
  </section>
</div>
<!-- END PACKAGES -->

<!-- ============================================================ -->
<!-- GALLERY PAGE -->
<!-- ============================================================ -->
<div class="page" id="page-gallery">
  <div class="gallery-hero">
    <div class="section-label" style="margin:0 auto 1rem;color:rgba(255,255,255,.85)"><i class="fa-solid fa-images"></i> Visual Stories</div>
    <h1>Travel <span style="color:var(--gold)">Gallery</span></h1>
    <p>A window into the world's most breathtaking moments, captured through the lens of our wanderers.</p>
  </div>
  <section class="section">
    <div class="gallery-grid">
      <div class="g-item wide"><img src="https://images.unsplash.com/photo-1506905925346-21bda4d32df4?w=800&q=80" alt="Mountains"><div class="g-overlay"><span><i class="fa-solid fa-mountain"></i> Swiss Alps</span></div></div>
      <div class="g-item tall"><img src="https://images.unsplash.com/photo-1537996194471-e657df975ab4?w=600&q=80" alt="Bali Rice"><div class="g-overlay"><span><i class="fa-solid fa-leaf"></i> Bali, Indonesia</span></div></div>
      <div class="g-item"><img src="https://images.unsplash.com/photo-1499856871958-5b9627545d1a?w=600&q=80" alt="Paris"><div class="g-overlay"><span><i class="fa-solid fa-tower-observation"></i> Paris, France</span></div></div>
      <div class="g-item"><img src="https://images.unsplash.com/photo-1512453979798-5ea266f8880c?w=600&q=80" alt="Dubai"><div class="g-overlay"><span><i class="fa-solid fa-city"></i> Dubai, UAE</span></div></div>
      <div class="g-item wide"><img src="https://images.unsplash.com/photo-1596178065887-1198b6148b2b?w=800&q=80" alt="Maldives"><div class="g-overlay"><span><i class="fa-solid fa-water"></i> Maldives</span></div></div>
      <div class="g-item"><img src="https://images.unsplash.com/photo-1548013146-72479768bada?w=600&q=80" alt="Rajasthan"><div class="g-overlay"><span><i class="fa-solid fa-fort-awesome"></i> Rajasthan, India</span></div></div>
      <div class="g-item"><img src="https://images.unsplash.com/photo-1530973428-5bf2db2e4d71?w=600&q=80" alt="Santorini"><div class="g-overlay"><span><i class="fa-solid fa-umbrella-beach"></i> Santorini, Greece</span></div></div>
      <div class="g-item wide tall"><img src="https://images.unsplash.com/photo-1566737236500-c8ac43014a67?w=800&q=80" alt="Kashmir"><div class="g-overlay"><span><i class="fa-solid fa-snowflake"></i> Kashmir, India</span></div></div>
      <div class="g-item"><img src="https://images.unsplash.com/photo-1580655653885-65763b2597d1?w=600&q=80" alt="Tokyo"><div class="g-overlay"><span><i class="fa-solid fa-torii-gate"></i> Tokyo, Japan</span></div></div>
      <div class="g-item"><img src="https://images.unsplash.com/photo-1512343879784-a960bf40e7f2?w=600&q=80" alt="Goa"><div class="g-overlay"><span><i class="fa-solid fa-umbrella-beach"></i> Goa, India</span></div></div>
      <div class="g-item"><img src="https://images.unsplash.com/photo-1626621341517-bbf3d9990a23?w=600&q=80" alt="Manali"><div class="g-overlay"><span><i class="fa-solid fa-mountain-sun"></i> Manali, India</span></div></div>
      <div class="g-item"><img src="https://images.unsplash.com/photo-1551632811-561732d1e306?w=600&q=80" alt="Trek"><div class="g-overlay"><span><i class="fa-solid fa-person-hiking"></i> Adventure Trek</span></div></div>
    </div>
  </section>
</div>
<!-- END GALLERY -->

<!-- ============================================================ -->
<!-- ABOUT PAGE -->
<!-- ============================================================ -->
<div class="page" id="page-about">
  <div class="about-hero">
    <div class="about-hero-content">
      <div class="section-label" style="color:rgba(255,255,255,.85)"><i class="fa-solid fa-earth-asia"></i> Our Story</div>
      <h1>Turning Journeys<br>into <span style="color:var(--sky)">Memories</span></h1>
      <p>Founded in 2009, WanderWorld has been helping millions of travelers discover the world's most extraordinary destinations with passion, expertise, and care.</p>
    </div>
  </div>

  <section class="section">
    <div class="about-grid">
      <div class="about-img-wrap"><img src="https://images.unsplash.com/photo-1488646953014-85cb44e25828?w=800&q=80" alt="About WanderWorld"></div>
      <div class="about-text">
        <div class="section-label"><i class="fa-solid fa-building"></i> About Us</div>
        <h2>Who We <span style="color:var(--sky)">Are</span></h2>
        <p>WanderWorld is India's most trusted travel company, with offices across 12 cities and partnerships with over 500 hotels and airlines worldwide. We specialize in creating personalized travel experiences that go beyond the ordinary.</p>
        <p>Our team of 200+ passionate travel experts works tirelessly to ensure every journey is seamless, safe, and extraordinary — from the moment you dream it to the moment you live it.</p>
        <div class="mission-cards">
          <div class="mission-card"><h4><i class="fa-solid fa-bullseye" style="color:var(--sky)"></i> Our Mission</h4><p>To make world travel accessible, joyful, and transformative for every traveler.</p></div>
          <div class="mission-card"><h4><i class="fa-solid fa-eye" style="color:var(--sky)"></i> Our Vision</h4><p>A world where every person experiences the beauty of global cultures and destinations.</p></div>
          <div class="mission-card"><h4><i class="fa-solid fa-gem" style="color:var(--sky)"></i> Our Values</h4><p>Integrity, excellence, sustainability, and genuine care for every traveler.</p></div>
          <div class="mission-card"><h4><i class="fa-solid fa-leaf" style="color:var(--sky)"></i> Eco Travel</h4><p>Committed to responsible tourism that protects cultures and natural wonders.</p></div>
        </div>
      </div>
    </div>
  </section>

  <section class="section tips-section">
    <div class="section-header">
      <div class="section-label"><i class="fa-solid fa-trophy"></i> Our Advantage</div>
      <h2 class="section-title">Why Choose <span>WanderWorld?</span></h2>
      <p class="section-sub">Thousands of travelers trust us. Here's why we're different from the rest.</p>
    </div>
    <div class="why-grid">
      <div class="why-card"><div class="why-icon"><i class="fa-solid fa-medal"></i></div><h4>15+ Years Experience</h4><p>Over a decade of crafting perfect travel experiences across 120+ countries worldwide.</p></div>
      <div class="why-card"><div class="why-icon"><i class="fa-solid fa-headset"></i></div><h4>24/7 Support</h4><p>Round-the-clock assistance in 15 languages — we're always here when you need us most.</p></div>
      <div class="why-card"><div class="why-icon"><i class="fa-solid fa-lock"></i></div><h4>Secure Booking</h4><p>100% secure payment gateway with instant confirmation and transparent pricing policy.</p></div>
      <div class="why-card"><div class="why-icon"><i class="fa-solid fa-users"></i></div><h4>Expert Guides</h4><p>Certified, multilingual local guides who bring destinations alive with authentic stories.</p></div>
      <div class="why-card"><div class="why-icon"><i class="fa-solid fa-tags"></i></div><h4>Best Price Guarantee</h4><p>We match any lower price you find — your ideal trip at the most competitive rates.</p></div>
      <div class="why-card"><div class="why-icon"><i class="fa-solid fa-recycle"></i></div><h4>Sustainable Travel</h4><p>Eco-certified practices ensuring your adventures help preserve the planet's treasures.</p></div>
    </div>
  </section>
</div>
<!-- END ABOUT -->

<!-- ============================================================ -->
<!-- CONTACT PAGE -->
<!-- ============================================================ -->
<div class="page" id="page-contact">
  <div class="contact-hero">
    <div class="section-label" style="margin:0 auto 1rem;color:rgba(255,255,255,.85)"><i class="fa-solid fa-paper-plane"></i> Get in Touch</div>
    <h1>Contact <span style="color:var(--gold)">Us</span></h1>
    <p>Have questions about a destination or package? We'd love to hear from you!</p>
  </div>
  <section class="section">
    <div class="contact-grid">
      <div class="contact-info">
        <h3>Let's Plan Your<br><span style="color:var(--sky)">Dream Trip</span></h3>
        <p>Our travel experts are ready to help you discover your perfect destination and craft a journey tailored just for you.</p>
        <div class="contact-items">
          <div class="contact-item"><div class="c-icon"><i class="fa-solid fa-location-dot"></i></div><div class="c-text"><strong>Headquarters</strong><span>WanderWorld Tower, BKC, Mumbai – 400051, Maharashtra, India</span></div></div>
          <div class="contact-item"><div class="c-icon"><i class="fa-solid fa-phone"></i></div><div class="c-text"><strong>Phone</strong><span>+91 98765 43210 | +91 22 6123 4567</span></div></div>
          <div class="contact-item"><div class="c-icon"><i class="fa-solid fa-envelope"></i></div><div class="c-text"><strong>Email</strong><span>hello@wanderworld.in | support@wanderworld.in</span></div></div>
          <div class="contact-item"><div class="c-icon"><i class="fa-solid fa-clock"></i></div><div class="c-text"><strong>Working Hours</strong><span>Mon – Sat: 9:00 AM – 8:00 PM IST</span></div></div>
        </div>
      </div>
      <div class="contact-form">
        <h3>Send Us a Message</h3>
        <div class="form-row">
          <div class="form-group"><label>First Name</label><input type="text" placeholder="e.g. Priya"></div>
          <div class="form-group"><label>Last Name</label><input type="text" placeholder="e.g. Sharma"></div>
        </div>
        <div class="form-group"><label>Email Address</label><input type="email" placeholder="priya@example.com"></div>
        <div class="form-group"><label>Phone Number</label><input type="tel" placeholder="+91 98765 43210"></div>
        <div class="form-group">
          <label>Interested In</label>
          <select>
            <option value="">Select a package type...</option>
            <option>Solo Trip</option>
            <option>Family Package</option>
            <option>Honeymoon Escape</option>
            <option>Adventure Tour</option>
            <option>Custom Itinerary</option>
            <option>General Enquiry</option>
          </select>
        </div>
        <div class="form-group"><label>Your Message</label><textarea placeholder="Tell us your travel dreams, preferred dates, budget range, or any special requests..."></textarea></div>
        <button class="btn btn-primary" style="width:100%;justify-content:center" onclick="submitForm()"><i class="fa-solid fa-paper-plane"></i> Send Message</button>
        <div class="form-success" id="formSuccess"><i class="fa-solid fa-circle-check"></i>Thank you! Your message has been sent. Our travel expert will get back to you within 24 hours. ✈️</div>
      </div>
    </div>
  </section>
</div>
<!-- END CONTACT -->

<!-- ============== FOOTER ============== -->
<footer>
  <div class="footer-grid">
    <div class="footer-brand">
      <div class="logo">Wander<span>World</span></div>
      <p>Your trusted travel partner for over 15 years, crafting unforgettable journeys across 120+ countries. Where every trip becomes a treasured story.</p>
      <div class="social-links">
        <div class="social-link"><i class="fa-brands fa-facebook-f"></i></div>
        <div class="social-link"><i class="fa-brands fa-instagram"></i></div>
        <div class="social-link"><i class="fa-brands fa-twitter"></i></div>
        <div class="social-link"><i class="fa-brands fa-youtube"></i></div>
        <div class="social-link"><i class="fa-brands fa-whatsapp"></i></div>
      </div>
    </div>
    <div class="footer-col">
      <h4>Quick Links</h4>
      <ul>
        <li><a onclick="showPage('home')">Home</a></li>
        <li><a onclick="showPage('destinations')">Destinations</a></li>
        <li><a onclick="showPage('packages')">Packages</a></li>
        <li><a onclick="showPage('gallery')">Gallery</a></li>
        <li><a onclick="showPage('about')">About Us</a></li>
        <li><a onclick="showPage('contact')">Contact</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Top Destinations</h4>
      <ul>
        <li><a>Goa, India</a></li>
        <li><a>Manali, India</a></li>
        <li><a>Kashmir, India</a></li>
        <li><a>Dubai, UAE</a></li>
        <li><a>Paris, France</a></li>
        <li><a>Bali, Indonesia</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Support</h4>
      <ul>
        <li><a>FAQs</a></li>
        <li><a>Cancellation Policy</a></li>
        <li><a>Privacy Policy</a></li>
        <li><a>Terms of Service</a></li>
        <li><a>Travel Insurance</a></li>
        <li><a>Visa Assistance</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <span>© 2025 WanderWorld Travel Pvt. Ltd. All rights reserved.</span>
    <span>Made with <i class="fa-solid fa-heart" style="color:var(--sky)"></i> for every traveler</span>
  </div>
</footer>

<script>
function showPage(id) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.nav-links a').forEach(a => a.classList.remove('active'));
  document.getElementById('page-' + id).classList.add('active');
  const navEl = document.getElementById('nav-' + id);
  if (navEl) navEl.classList.add('active');
  document.getElementById('navLinks').classList.remove('open');
  window.scrollTo({ top: 0, behavior: 'smooth' });
}
function toggleMenu() {
  document.getElementById('navLinks').classList.toggle('open');
}
function submitForm() {
  const inputs = document.querySelectorAll('#page-contact input, #page-contact textarea, #page-contact select');
  let valid = true;
  inputs.forEach(i => { if (!i.value.trim() && i.type !== 'tel') valid = false; });
  if (!valid) { alert('Please fill in all required fields.'); return; }
  inputs.forEach(i => i.value = '');
  document.getElementById('formSuccess').style.display = 'block';
  setTimeout(() => document.getElementById('formSuccess').style.display = 'none', 5000);
}
</script>
</body>
</html>
# wanderworld
