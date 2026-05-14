<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="description" content="Student Saver customer and business login page." />
  <title>Student Saver Login</title>
  <style>
    :root {
      color-scheme: light;
      --ink: #101820;
      --muted: #5b6870;
      --line: #dce4e4;
      --surface: rgba(255, 255, 255, 0.86);
      --surface-strong: #ffffff;
      --teal: #087d75;
      --teal-dark: #055f59;
      --mint: #dff8ef;
      --coral: #ee6654;
      --coral-dark: #c94e3f;
      --gold: #f2b94b;
      --shadow: 0 24px 70px rgba(16, 24, 32, 0.16);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    html {
      min-height: 100%;
    }

    body {
      min-height: 100svh;
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Arial, sans-serif;
      color: var(--ink);
      background:
        linear-gradient(120deg, rgba(8, 125, 117, 0.18), transparent 32%),
        linear-gradient(300deg, rgba(238, 102, 84, 0.18), transparent 34%),
        linear-gradient(180deg, #fbfdfb, #eef5f3);
      display: grid;
      place-items: center;
      padding: 28px;
    }

    body::before {
      content: "";
      position: fixed;
      inset: 0;
      pointer-events: none;
      background-image:
        linear-gradient(rgba(16, 24, 32, 0.05) 1px, transparent 1px),
        linear-gradient(90deg, rgba(16, 24, 32, 0.05) 1px, transparent 1px);
      background-size: 46px 46px;
      mask-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.45), transparent 70%);
    }

    .app-shell {
      width: min(1180px, 100%);
      min-height: min(780px, calc(100svh - 56px));
      display: grid;
      grid-template-columns: 0.9fr 1.1fr;
      overflow: hidden;
      border: 1px solid rgba(16, 24, 32, 0.1);
      border-radius: 24px;
      background: var(--surface);
      box-shadow: var(--shadow);
      backdrop-filter: blur(18px);
    }

    .brand-panel {
      position: relative;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      padding: clamp(28px, 5vw, 54px);
      background:
        linear-gradient(150deg, rgba(8, 125, 117, 0.96), rgba(5, 95, 89, 0.98)),
        #087d75;
      color: #ffffff;
      overflow: hidden;
    }

    .brand-panel::after {
      content: "";
      position: absolute;
      right: -80px;
      bottom: -120px;
      width: 340px;
      height: 340px;
      border: 44px solid rgba(255, 255, 255, 0.12);
      border-radius: 50%;
    }

    .brand-lockup,
    .metric-row,
    .brand-message {
      position: relative;
      z-index: 1;
    }

    .brand-lockup {
      display: flex;
      align-items: center;
      gap: 14px;
    }

    .logo {
      width: 64px;
      height: 64px;
      display: grid;
      place-items: center;
      border-radius: 18px;
      background: #ffffff;
      box-shadow: 0 16px 40px rgba(0, 0, 0, 0.18);
    }

    .logo svg {
      width: 46px;
      height: 46px;
    }

    .wordmark {
      font-size: 26px;
      font-weight: 850;
      letter-spacing: 0;
      line-height: 1;
    }

    .brand-kicker {
      margin-top: 7px;
      color: rgba(255, 255, 255, 0.76);
      font-size: 14px;
      font-weight: 650;
    }

    .brand-message {
      max-width: 430px;
      margin: 56px 0;
    }

    .brand-message h1 {
      font-size: clamp(36px, 5vw, 58px);
      line-height: 1.02;
      letter-spacing: 0;
    }

    .brand-message p {
      margin-top: 18px;
      color: rgba(255, 255, 255, 0.82);
      font-size: 17px;
      line-height: 1.65;
    }

    .metric-row {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 12px;
    }

    .metric {
      min-height: 86px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      border: 1px solid rgba(255, 255, 255, 0.2);
      border-radius: 16px;
      padding: 16px;
      background: rgba(255, 255, 255, 0.1);
    }

    .metric strong {
      font-size: 20px;
      line-height: 1;
    }

    .metric span {
      margin-top: 8px;
      color: rgba(255, 255, 255, 0.72);
      font-size: 12px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.08em;
    }

    .login-panel {
      padding: clamp(24px, 4vw, 46px);
      background:
        linear-gradient(180deg, rgba(255, 255, 255, 0.78), rgba(255, 255, 255, 0.96)),
        var(--surface-strong);
    }

    .panel-top {
      display: flex;
      justify-content: space-between;
      gap: 18px;
      margin-bottom: 28px;
    }

    .panel-top h2 {
      font-size: clamp(26px, 3vw, 36px);
      line-height: 1.1;
      letter-spacing: 0;
    }

    .panel-top p {
      margin-top: 8px;
      color: var(--muted);
      font-size: 15px;
      line-height: 1.5;
    }

    .secure-chip {
      align-self: flex-start;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      min-height: 38px;
      padding: 0 13px;
      border: 1px solid var(--line);
      border-radius: 999px;
      color: #38474f;
      background: #ffffff;
      font-size: 13px;
      font-weight: 750;
      white-space: nowrap;
    }

    .secure-chip svg {
      width: 16px;
      height: 16px;
      color: var(--teal);
    }

    .login-options {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 18px;
    }

    .login-card {
      display: flex;
      min-height: 570px;
      flex-direction: column;
      border: 1px solid var(--line);
      border-radius: 20px;
      padding: 24px;
      background: #ffffff;
      box-shadow: 0 16px 34px rgba(16, 24, 32, 0.08);
    }

    .card-head {
      display: flex;
      align-items: center;
      gap: 12px;
      margin-bottom: 24px;
    }

    .avatar {
      width: 48px;
      height: 48px;
      display: grid;
      place-items: center;
      border-radius: 14px;
      flex: 0 0 auto;
    }

    .customer .avatar {
      background: var(--mint);
      color: var(--teal-dark);
    }

    .business .avatar {
      background: #ffe8dd;
      color: var(--coral-dark);
    }

    .avatar svg {
      width: 24px;
      height: 24px;
    }

    .card-head h3 {
      font-size: 22px;
      line-height: 1.1;
      letter-spacing: 0;
    }

    .card-head p {
      margin-top: 5px;
      color: var(--muted);
      font-size: 13px;
      line-height: 1.4;
    }

    .field {
      margin-bottom: 17px;
    }

    label {
      display: block;
      margin-bottom: 8px;
      color: #27353d;
      font-size: 13px;
      font-weight: 780;
    }

    .input-wrap {
      position: relative;
    }

    .input-wrap svg {
      position: absolute;
      left: 14px;
      top: 50%;
      width: 18px;
      height: 18px;
      color: #7a898f;
      transform: translateY(-50%);
      pointer-events: none;
    }

    input {
      width: 100%;
      height: 50px;
      border: 1px solid #cfdada;
      border-radius: 12px;
      padding: 0 14px 0 44px;
      background: #fbfcfc;
      color: var(--ink);
      font: inherit;
      font-size: 15px;
      outline: none;
      transition: border-color 0.2s ease, box-shadow 0.2s ease, background 0.2s ease;
    }

    input::placeholder {
      color: #9aa7ac;
    }

    input:focus-visible {
      border-color: var(--teal);
      background: #ffffff;
      box-shadow: 0 0 0 4px rgba(8, 125, 117, 0.15);
    }

    .business input:focus-visible {
      border-color: var(--coral);
      box-shadow: 0 0 0 4px rgba(238, 102, 84, 0.16);
    }

    .form-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      margin: 2px 0 22px;
      font-size: 13px;
    }

    .remember {
      display: inline-flex;
      align-items: center;
      gap: 9px;
      margin: 0;
      color: var(--muted);
      font-weight: 700;
      white-space: nowrap;
    }

    .remember input {
      width: 17px;
      height: 17px;
      padding: 0;
      border-radius: 5px;
      accent-color: var(--teal);
    }

    .business .remember input {
      accent-color: var(--coral);
    }

    a {
      color: var(--teal-dark);
      font-weight: 800;
      text-decoration: none;
    }

    a:hover {
      text-decoration: underline;
      text-underline-offset: 3px;
    }

    .business a {
      color: var(--coral-dark);
    }

    button {
      width: 100%;
      min-height: 52px;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      border: 0;
      border-radius: 14px;
      color: #ffffff;
      font: inherit;
      font-size: 15px;
      font-weight: 850;
      cursor: pointer;
      transition: transform 0.2s ease, box-shadow 0.2s ease, filter 0.2s ease;
    }

    button svg {
      width: 18px;
      height: 18px;
    }

    button:hover {
      transform: translateY(-2px);
      filter: saturate(1.06);
    }

    button:focus-visible {
      outline: 4px solid rgba(16, 24, 32, 0.12);
      outline-offset: 3px;
    }

    .customer button {
      background: linear-gradient(135deg, var(--teal), var(--teal-dark));
      box-shadow: 0 16px 28px rgba(8, 125, 117, 0.22);
    }

    .business button {
      background: linear-gradient(135deg, var(--coral), var(--coral-dark));
      box-shadow: 0 16px 28px rgba(238, 102, 84, 0.22);
    }

    .signup {
      margin-top: auto;
      padding-top: 20px;
      color: var(--muted);
      text-align: center;
      font-size: 14px;
      line-height: 1.45;
    }

    .divider {
      height: 1px;
      margin: 22px 0;
      background: var(--line);
    }

    .helper-list {
      display: grid;
      gap: 9px;
      margin-bottom: 22px;
      color: var(--muted);
      font-size: 13px;
      line-height: 1.35;
    }

    .helper-list span {
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .helper-list svg {
      width: 16px;
      height: 16px;
      color: var(--gold);
      flex: 0 0 auto;
    }

    @media (max-width: 1060px) {
      .app-shell {
        grid-template-columns: 1fr;
      }

      .brand-panel {
        min-height: auto;
        gap: 30px;
      }

      .brand-message {
        margin: 22px 0 0;
      }
    }

    @media (max-width: 760px) {
      body {
        padding: 14px;
        place-items: start center;
      }

      .app-shell {
        min-height: auto;
        border-radius: 18px;
      }

      .login-options,
      .metric-row {
        grid-template-columns: 1fr;
      }

      .login-card {
        min-height: auto;
      }

      .panel-top {
        flex-direction: column;
      }
    }

    @media (max-width: 480px) {
      .brand-panel,
      .login-panel {
        padding: 22px;
      }

      .brand-lockup,
      .card-head {
        align-items: flex-start;
      }

      .logo {
        width: 56px;
        height: 56px;
        border-radius: 15px;
      }

      .form-row {
        align-items: flex-start;
        flex-direction: column;
      }

      .secure-chip {
        white-space: normal;
      }
    }
  </style>
</head>
<body>
  <main class="app-shell">
    <section class="brand-panel" aria-label="Student Saver">
      <div class="brand-lockup">
        <div class="logo" aria-hidden="true">
          <svg viewBox="0 0 64 64" role="img" aria-label="Student Saver logo">
            <rect x="7" y="7" width="50" height="50" rx="16" fill="#087d75" />
            <path d="M21 21h22a5 5 0 0 1 0 10H27a5 5 0 0 0 0 10h18" fill="none" stroke="#ffffff" stroke-width="6" stroke-linecap="round" />
            <path d="M24 15v34M38 15v34" stroke="#f2b94b" stroke-width="4.5" stroke-linecap="round" />
          </svg>
        </div>
        <div>
          <div class="wordmark">Student Saver</div>
          <div class="brand-kicker">Smart deals for student life</div>
        </div>
      </div>

      <div class="brand-message">
        <h1>Welcome back to better savings.</h1>
        <p>Students can access offers, while business partners manage discounts, promotions, and store details from one secure login.</p>
      </div>

      <div class="metric-row" aria-label="Student Saver highlights">
        <div class="metric">
          <strong>2K+</strong>
          <span>Offers</span>
        </div>
        <div class="metric">
          <strong>850+</strong>
          <span>Partners</span>
        </div>
        <div class="metric">
          <strong>24/7</strong>
          <span>Access</span>
        </div>
      </div>
    </section>

    <section class="login-panel" aria-label="Login forms">
      <div class="panel-top">
        <div>
          <h2>Select your login</h2>
          <p>Customer and business accounts are kept separate for a cleaner, safer sign-in flow.</p>
        </div>
        <div class="secure-chip">
          <svg viewBox="0 0 24 24" fill="none" aria-hidden="true">
            <path d="M7 10V8a5 5 0 0 1 10 0v2" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
            <rect x="5" y="10" width="14" height="10" rx="3" stroke="currentColor" stroke-width="2" />
          </svg>
          Secure login
        </div>
      </div>

      <div class="login-options">
        <form class="login-card customer" action="#" method="post">
          <div class="card-head">
            <div class="avatar" aria-hidden="true">
              <svg viewBox="0 0 24 24" fill="none">
                <path d="M12 13a4 4 0 1 0 0-8 4 4 0 0 0 0 8Z" stroke="currentColor" stroke-width="2" />
                <path d="M4 21a8 8 0 0 1 16 0" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
              </svg>
            </div>
            <div>
              <h3>Customer Login</h3>
              <p>For students and everyday shoppers</p>
            </div>
          </div>

          <div class="field">
            <label for="customer-email">Email address</label>
            <div class="input-wrap">
              <svg viewBox="0 0 24 24" fill="none" aria-hidden="true">
                <path d="M4 6h16v12H4V6Z" stroke="currentColor" stroke-width="2" />
                <path d="m4 7 8 6 8-6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
              <input id="customer-email" name="customer-email" type="email" placeholder="student@example.com" autocomplete="email" required />
            </div>
          </div>

          <div class="field">
            <label for="customer-password">Password</label>
            <div class="input-wrap">
              <svg viewBox="0 0 24 24" fill="none" aria-hidden="true">
                <path d="M7 11V8a5 5 0 0 1 10 0v3" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
                <rect x="5" y="11" width="14" height="9" rx="2" stroke="currentColor" stroke-width="2" />
              </svg>
              <input id="customer-password" name="customer-password" type="password" placeholder="Enter your password" autocomplete="current-password" required />
            </div>
          </div>

          <div class="form-row">
            <label class="remember" for="customer-remember">
              <input id="customer-remember" name="customer-remember" type="checkbox" />
              Remember me
            </label>
            <a href="#">Forgot password?</a>
          </div>

          <button type="submit">
            Log In as Customer
            <svg viewBox="0 0 24 24" fill="none" aria-hidden="true">
              <path d="M5 12h14m-6-6 6 6-6 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
            </svg>
          </button>

          <div class="divider"></div>
          <div class="helper-list" aria-label="Customer account benefits">
            <span>
              <svg viewBox="0 0 24 24" fill="none" aria-hidden="true">
                <path d="m5 12 4 4L19 6" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
              Student discount wallet
            </span>
            <span>
              <svg viewBox="0 0 24 24" fill="none" aria-hidden="true">
                <path d="m5 12 4 4L19 6" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
              Saved favorite offers
            </span>
          </div>

          <p class="signup">New customer? <a href="#">Create account</a></p>
        </form>

        <form class="login-card business" action="#" method="post">
          <div class="card-head">
            <div class="avatar" aria-hidden="true">
              <svg viewBox="0 0 24 24" fill="none">
                <path d="M4 21V8l8-5 8 5v13" stroke="currentColor" stroke-width="2" stroke-linejoin="round" />
                <path d="M9 21v-7h6v7M8 10h.01M16 10h.01" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
              </svg>
            </div>
            <div>
              <h3>Business Login</h3>
              <p>For partners and store owners</p>
            </div>
          </div>

          <div class="field">
            <label for="business-email">Business email</label>
            <div class="input-wrap">
              <svg viewBox="0 0 24 24" fill="none" aria-hidden="true">
                <path d="M4 6h16v12H4V6Z" stroke="currentColor" stroke-width="2" />
                <path d="m4 7 8 6 8-6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
              <input id="business-email" name="business-email" type="email" placeholder="owner@business.com" autocomplete="email" required />
            </div>
          </div>

          <div class="field">
            <label for="business-id">Business ID</label>
            <div class="input-wrap">
              <svg viewBox="0 0 24 24" fill="none" aria-hidden="true">
                <path d="M4 7h16M7 7V5h10v2M6 7l1 13h10l1-13" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
              <input id="business-id" name="business-id" type="text" placeholder="SSB-0000" autocomplete="organization" required />
            </div>
          </div>

          <div class="field">
            <label for="business-password">Password</label>
            <div class="input-wrap">
              <svg viewBox="0 0 24 24" fill="none" aria-hidden="true">
                <path d="M7 11V8a5 5 0 0 1 10 0v3" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
                <rect x="5" y="11" width="14" height="9" rx="2" stroke="currentColor" stroke-width="2" />
              </svg>
              <input id="business-password" name="business-password" type="password" placeholder="Enter your password" autocomplete="current-password" required />
            </div>
          </div>

          <div class="form-row">
            <label class="remember" for="business-remember">
              <input id="business-remember" name="business-remember" type="checkbox" />
              Remember me
            </label>
            <a href="#">Need help?</a>
          </div>

          <button type="submit">
            Log In as Business
            <svg viewBox="0 0 24 24" fill="none" aria-hidden="true">
              <path d="M5 12h14m-6-6 6 6-6 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
            </svg>
          </button>

          <div class="divider"></div>
          <div class="helper-list" aria-label="Business account benefits">
            <span>
              <svg viewBox="0 0 24 24" fill="none" aria-hidden="true">
                <path d="m5 12 4 4L19 6" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
              Manage active offers
            </span>
            <span>
            

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Student Saver Business App</title>

<style>
*{box-sizing:border-box;font-family:Arial,sans-serif}
body{margin:0;background:#000;color:#fff}
.app{max-width:430px;margin:auto;min-height:100vh;background:#121212;padding-bottom:90px}
.hero{padding:26px 18px;background:linear-gradient(180deg,#1db954,#121212)}
.hero h1{margin:0;font-size:30px}.hero p{color:#eaffef;margin:6px 0 0}
section{display:none}section.active{display:block}
.card,.promo-card,.tool-tile{background:#181818;border:1px solid #282828;border-radius:22px;margin:14px 18px;padding:16px}
.card p,.promo-card p,.tool-tile p{color:#b3b3b3;font-size:14px}
.card h2,.card h3{margin:0 0 8px}
.small{font-size:12px;color:#aaa;text-transform:uppercase;letter-spacing:1px}
.badge{display:inline-block;background:#1db954;color:#000;font-weight:bold;border-radius:20px;padding:6px 12px;font-size:12px}
input,select,textarea{width:100%;background:#282828;color:white;border:0;border-radius:14px;padding:14px;margin:7px 0 12px;font-size:15px}
textarea{height:78px;resize:none}
button{width:100%;border:0;border-radius:25px;background:#1db954;color:#000;font-weight:bold;padding:14px;margin-top:6px}
button.dark{background:#282828;color:white}button.red{background:#ff5c5c;color:white}
.grid,.creative-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:14px 18px}
.stat{background:#181818;border:1px solid #282828;border-radius:18px;padding:16px}
.stat h2{margin:0;color:#1db954;font-size:26px}.stat p{margin:4px 0 0;color:#b3b3b3;font-size:13px}
.home-hero,.promo-studio,.growth-hero,.account-cover,.more-hero{margin:14px 18px;padding:22px;border-radius:28px;background:radial-gradient(circle at top right,#1db954,transparent 45%),linear-gradient(135deg,#191414,#181818);border:1px solid #282828}
.home-hero h2,.promo-studio h2,.growth-hero h2,.more-hero h2{font-size:27px;margin:6px 0}
.home-hero p,.promo-studio p,.growth-hero p,.more-hero p{color:#d8f5df}
.glow{box-shadow:0 0 24px rgba(29,185,84,.25)}
.mini-chart{height:90px;display:flex;gap:8px;align-items:end;margin-top:15px}
.mini-chart span{flex:1;background:#1db954;border-radius:12px 12px 0 0}
.quick-actions,.date-row{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:14px 18px}
.progress{height:8px;background:#282828;border-radius:20px;overflow:hidden;margin-top:10px}
.progress span{display:block;height:100%;background:#1db954;width:88%}
.store-avatar{width:76px;height:76px;border-radius:24px;background:#1db954;color:#000;display:flex;align-items:center;justify-content:center;font-size:28px;font-weight:bold;margin-bottom:12px}
.promo-card{overflow:hidden;padding:0}.promo-card img{width:100%;height:170px;object-fit:cover;display:block}
.promo-content{padding:16px}.promo-content h3{margin:10px 0 6px;font-size:20px}
.promo-details{display:grid;gap:6px;margin:12px 0;color:#d6d6d6;font-size:13px}
.row{display:grid;grid-template-columns:1fr 1fr 1fr;gap:8px}.row button{font-size:12px;padding:11px}
.tool-icon{display:inline-flex;width:42px;height:42px;border-radius:14px;background:#1db954;color:#000;align-items:center;justify-content:center;font-weight:bold}
.more-hero{display:flex;justify-content:space-between;gap:16px;align-items:center}
.studio-ring{width:68px;height:68px;border-radius:50%;border:3px solid #1db954;display:flex;align-items:center;justify-content:center;color:#1db954;font-weight:bold}
.suki-pass{margin:14px 18px;padding:18px;border-radius:24px;background:linear-gradient(145deg,#1db954,#0d3d24);color:#000}
.suki-pass p{color:#102016}
.stamp-row{display:flex;gap:10px;margin:12px 0}
.stamp{width:34px;height:34px;border-radius:50%;border:2px solid #000}
.stamp.active{background:#000}
.nav{position:fixed;bottom:0;left:50%;transform:translateX(-50%);width:100%;max-width:430px;background:#000;border-top:1px solid #282828;display:grid;grid-template-columns:repeat(5,1fr);padding:8px 0}
.nav button{background:transparent;color:#aaa;border-radius:0;font-size:12px;padding:8px 2px}.nav button.active{color:#1db954}
.success{color:#1db954;font-size:14px}

.subscription-studio{margin:14px 18px;padding:20px;border-radius:28px;background:linear-gradient(145deg,#181818,#101010);border:1px solid #282828}
.subscription-studio h2{margin:6px 0;font-size:27px}
.subscription-studio p{color:#b3b3b3;font-size:14px}
.billing-toggle{display:grid;grid-template-columns:1fr 1fr;background:#282828;border-radius:24px;padding:4px;margin:16px 0}
.billing-toggle button{margin:0;background:transparent;color:#aaa;padding:11px}
.billing-toggle button.active{background:#1db954;color:#000}
.pricing-card{position:relative;background:#202020;border:1px solid #303030;border-radius:24px;padding:16px;margin-top:12px}
.pro-plan{border-color:#1db954;box-shadow:0 0 24px rgba(29,185,84,.18)}
.pricing-card h3{margin:6px 0;font-size:22px}
.pricing-card strong{display:block;color:#1db954;font-size:20px;margin:10px 0}
.plan-tag{display:inline-block;color:#1db954;font-size:12px;text-transform:uppercase;letter-spacing:1px}
.recommended{position:absolute;top:14px;right:14px;background:#1db954;color:#000;border-radius:20px;padding:5px 10px;font-size:11px;font-weight:bold}
.pricing-card ul{padding-left:18px;color:#d6d6d6;font-size:14px;line-height:1.7}
</style>
</head>

<body>
<div class="app">
<div class="hero"><h1>Student Saver</h1><p>Business app for student promos, ads, loyalty, and growth</p></div>

<div class="card">
  <div class="small">Business Profile</div>
  <h2 id="businessDisplay">Campus Cafe</h2>
  <p id="businessInfo">Food and drinks near university area</p>
  <span class="badge" id="planBadge">Monthly Pro</span>
</div>

<section id="home" class="active">
  <div class="home-hero">
    <p class="small">Today's Business Pulse</p>
    <h2>Campus Cafe is trending near students</h2>
    <p>Your lunch deals are getting strong claim activity this week.</p>
    <button onclick="simulateActivity()">Refresh Live Stats</button>
  </div>

  <div class="grid">
    <div class="stat glow"><h2 id="promoCount">3</h2><p>Active Promos</p></div>
    <div class="stat"><h2 id="views">850</h2><p>Views</p></div>
    <div class="stat"><h2 id="claims">215</h2><p>Claims</p></div>
    <div class="stat"><h2 id="visibility">88%</h2><p>Visibility</p></div>
  </div>

  <div class="card">
    <h3>Smart Business Insight</h3>
    <p id="smartTip">Best posting window: 10 AM - 1 PM. Students claim food promos faster before lunch.</p>
    <div class="mini-chart">
      <span style="height:45%"></span><span style="height:70%"></span><span style="height:55%"></span>
      <span style="height:90%"></span><span style="height:66%"></span><span style="height:78%"></span>
    </div>
  </div>

  <div class="quick-actions">
    <button onclick="openTab('promos',document.querySelectorAll('.nav button')[2])">Post Promo</button>
    <button onclick="openTab('growth',document.querySelectorAll('.nav button')[3])">Boost Store</button>
  </div>
</section>

<section id="account">
  <div class="account-cover">
    <div class="store-avatar" id="storeAvatar">CC</div>
    <h2 id="accountBusinessDisplay">Campus Cafe</h2>
    <p id="accountBusinessInfo">Food and drinks near university area</p>
    <span class="badge">Verified Business</span>
  </div>

  <div class="card">
    <h2>Business Profile Setup</h2>
    <input id="businessName" placeholder="Business name">
    <input id="ownerName" placeholder="Owner name">
    <input id="email" type="email" placeholder="Business email">
    <select id="category">
      <option>Food and Drinks</option><option>School Supplies</option><option>Printing Services</option>
      <option>Retail</option><option>Transport</option>
    </select>
    <input id="nearestCampus" placeholder="Nearest campus">
    <input id="storeHours" placeholder="Opening hours, example: 8 AM - 8 PM">
    <textarea id="storeInfo" placeholder="Short business description"></textarea>
    <button onclick="saveBusiness()">Save Business Account</button>
    <p class="success" id="businessMsg"></p>
  </div>
</section>

<section id="promos">
  <div class="promo-studio">
    <p class="small">Promo Studio</p>
    <h2>Create student offers that stand out</h2>
    <p>Build claimable discounts with images, codes, limits, terms, and campus targeting.</p>
  </div>

  <div class="card">
    <input id="promoTitle" placeholder="Promo title">
    <select id="promoCategory">
      <option>Food and Drinks</option><option>School Supplies</option><option>Printing Services</option>
      <option>Transport</option><option>Fitness and Wellness</option><option>Retail</option>
    </select>
    <select id="discountType">
      <option>Percentage Discount</option><option>Fixed Amount Discount</option>
      <option>Buy 1 Take 1</option><option>Free Item Reward</option><option>Bundle Deal</option>
    </select>
    <input id="promoDiscount" placeholder="Discount value, example: 20% off">
    <select id="promoCampus">
      <option>All Campuses</option><option>National University</option><option>City College</option>
      <option>State University</option><option>Polytechnic East</option>
    </select>
    <div class="date-row"><input id="startDate" type="date"><input id="endDate" type="date"></div>
    <input id="promoCode" placeholder="Promo code, example: STUDENT20">
    <input id="claimLimit" type="number" placeholder="Claim limit, example: 100">
    <input id="promoImage" placeholder="Image URL, example: https://placehold.co/600x400">
    <textarea id="promoDesc" placeholder="Promo description"></textarea>
    <textarea id="promoTerms" placeholder="Terms and conditions"></textarea>
    <button onclick="addDetailedPromo()">Publish Promo</button>
  </div>

  <div id="promoList"></div>
</section>

<section id="growth">
  <div class="growth-hero">
    <p class="small">Growth Engine</p>
    <h2>Boost your store around campus</h2>
    <p>Use ads, recommendations, and location targeting to reach nearby students.</p>
  </div>

  <div class="creative-grid">
    <div class="tool-tile"><span class="tool-icon">TOP</span><h3>Top Search</h3><p>Place promos above regular results.</p></div>
    <div class="tool-tile"><span class="tool-icon">MAP</span><h3>Campus Radius</h3><p>Reach students near selected schools.</p></div>
  </div>

  <div class="card">
    <h3>Campaign Builder</h3>
    <select id="adPlacement"><option>Top Search Placement</option><option>Campus Recommendation</option><option>Category Spotlight</option></select>
    <input id="budget" type="number" placeholder="Daily ad budget">
    <select id="campus"><option>National University</option><option>City College</option><option>State University</option></select>
    <input id="radius" type="number" placeholder="Radius in km">
    <textarea id="targetMsg" placeholder="Message for nearby students"></textarea>
    <button onclick="activateAd()">Activate Growth Campaign</button>
    <p class="success" id="adMsg"></p>
  </div>
</section>

<section id="more">
  <div class="more-hero">
    <div><div class="small">Business Control Room</div><h2>Growth Studio</h2><p>Manage loyalty, subscriptions, live promo tools, and visibility.</p></div>
    <span class="studio-ring">PRO</span>
  </div>

  <div class="suki-pass">
    <div class="small">Suki Loyalty Pass</div>
    <h3>Student Rewards Card</h3>
    <p>Reward repeat student customers with stamps and exclusive perks.</p>
    <input id="rewardName" placeholder="Reward name, example: Free Iced Coffee">
    <input id="requiredVisits" type="number" placeholder="Required visits, example: 5">
    <input id="reward" placeholder="Reward details">
    <div class="stamp-row"><span class="stamp active"></span><span class="stamp active"></span><span class="stamp active"></span><span class="stamp"></span><span class="stamp"></span></div>
    <button onclick="saveLoyalty()">Activate Suki Program</button>
    <p class="success" id="loyaltyMsg"></p>
  </div>

  <div class="creative-grid">
    <div class="tool-tile"><span class="tool-icon">AD</span><h3>Boost Mode</h3><p>Push promos higher in search results.</p><button class="dark" onclick="activateAd()">Boost</button></div>
    <div class="tool-tile"><span class="tool-icon">RT</span><h3>Live Updates</h3><p>Refresh views, claims, visits, and repeat customers.</p><button class="dark" onclick="simulateActivity()">Refresh</button></div>
  </div>

  <div class="subscription-studio">
    <div class="small">Subscription Studio</div>
    <h2>Choose your growth plan</h2>
    <p>Unlock better promotion tools, student targeting, ads, and business insights.</p>

    <div class="billing-toggle">
      <button class="active" onclick="setBilling('monthly', this)">Monthly</button>
      <button onclick="setBilling('yearly', this)">Yearly</button>
    </div>

    <div class="pricing-card free-plan">
      <span class="plan-tag">Starter</span>
      <h3>Free Plan</h3>
      <p>For new stores testing Student Saver.</p>
      <strong>PHP 0</strong>
      <ul>
        <li>Basic business profile</li>
        <li>Post up to 2 active promos</li>
        <li>Basic visibility score</li>
      </ul>
      <button class="dark" onclick="selectPlan('Free Plan')">Use Free</button>
    </div>

    <div class="pricing-card pro-plan">
      <div class="recommended">Recommended</div>
      <span class="plan-tag">Growth</span>
      <h3>Pro Plan</h3>
      <p>For stores that want more student reach.</p>
      <strong id="proPrice">PHP 699 / month</strong>
      <ul>
        <li>Unlimited promo posting</li>
        <li>Featured advertisement boost</li>
        <li>Campus radius targeting</li>
        <li>Engagement analytics</li>
      </ul>
      <button onclick="selectPlan('Monthly Pro')">Choose Pro</button>
    </div>

    <div class="pricing-card yearly-plan">
      <span class="plan-tag">Scale</span>
      <h3>Business Plus</h3>
      <p>For growing brands with multiple campaigns.</p>
      <strong id="plusPrice">PHP 1,199 / month</strong>
      <ul>
        <li>Everything in Pro</li>
        <li>Priority search placement</li>
        <li>Loyalty campaign tools</li>
        <li>Advanced customer reports</li>
      </ul>
      <button class="dark" onclick="selectPlan('Business Plus')">Choose Plus</button>
    </div>

    <p class="success" id="planMsg"></p>
  </div>
</section>

<div class="nav">
  <button class="active" onclick="openTab('home',this)">Home</button>
  <button onclick="openTab('account',this)">Account</button>
  <button onclick="openTab('promos',this)">Promos</button>
  <button onclick="openTab('growth',this)">Growth</button>
  <button onclick="openTab('more',this)">More</button>
</div>
</div>

<script>
let promoCount=3,views=850,claims=215,visits=120,repeat=48,visibility=88,billingMode="monthly";

let promos=[
 {title:"Student Lunch Combo",category:"Food",desc:"15% off rice meals and drinks with valid school ID.",code:"LUNCH15",campus:"National University",claims:"85 / 150",img:"https://placehold.co/600x380/1db954/000000?text=Lunch+Combo",active:true},
 {title:"Milk Tea Study Deal",category:"Drinks",desc:"Buy 1 take 1 every Friday from 2 PM to 6 PM.",code:"STUDYTEA",campus:"All Campuses",claims:"120 / 200",img:"https://placehold.co/600x380/191414/1db954?text=Study+Milk+Tea",active:true},
 {title:"Printing Discount",category:"Printing",desc:"Get PHP 30 off printing services for school projects and reviewers.",code:"PRINT30",campus:"City College",claims:"42 / 100",img:"https://placehold.co/600x380/282828/ffffff?text=Printing+Discount",active:true}
];

function openTab(id,btn){
 document.querySelectorAll("section").forEach(s=>s.classList.remove("active"));
 document.getElementById(id).classList.add("active");
 document.querySelectorAll(".nav button").forEach(b=>b.classList.remove("active"));
 btn.classList.add("active");
}

function updateStats(){
 document.getElementById("promoCount").innerText=promos.filter(p=>p.active).length;
 document.getElementById("views").innerText=views;
 document.getElementById("claims").innerText=claims;
 document.getElementById("visibility").innerText=visibility+"%";
}

function renderPromos(){
 document.getElementById("promoList").innerHTML=promos.map((p,i)=>`
 <div class="promo-card">
   <img src="${p.img}" alt="${p.title}">
   <div class="promo-content">
     <span class="badge">${p.active ? "Active" : "Paused"}</span>
     <h3>${p.title}</h3>
     <p>${p.desc}</p>
     <div class="promo-details">
       <span>Category: ${p.category}</span>
       <span>Code: ${p.code}</span>
       <span>Campus: ${p.campus}</span>
       <span>Claims: ${p.claims}</span>
     </div>
     <div class="row">
       <button class="dark" onclick="editPromo(${i})">Edit</button>
       <button class="dark" onclick="togglePromo(${i})">${p.active ? "Pause" : "Activate"}</button>
       <button class="red" onclick="removePromo(${i})">Remove</button>
     </div>
   </div>
 </div>`).join("");
 updateStats();
}

function saveBusiness(){
 let name=document.getElementById("businessName").value||"Campus Cafe";
 let category=document.getElementById("category").value;
 let info=document.getElementById("storeInfo").value||"Profile updated";
 let initials=name.split(" ").map(w=>w[0]).join("").substring(0,2).toUpperCase();

 document.getElementById("businessDisplay").innerText=name;
 document.getElementById("businessInfo").innerText=category+" • "+info;
 document.getElementById("accountBusinessDisplay").innerText=name;
 document.getElementById("accountBusinessInfo").innerText=category+" • "+info;
 document.getElementById("storeAvatar").innerText=initials;
 document.getElementById("businessMsg").innerText="Business account saved successfully.";
 visibility=Math.min(100,visibility+4);
 updateStats();
}

function addDetailedPromo(){
 let title=document.getElementById("promoTitle").value;
 let category=document.getElementById("promoCategory").value;
 let discount=document.getElementById("promoDiscount").value;
 let campus=document.getElementById("promoCampus").value;
 let code=document.getElementById("promoCode").value||"No code required";
 let limit=document.getElementById("claimLimit").value||"Unlimited";
 let image=document.getElementById("promoImage").value||"https://placehold.co/600x380/1db954/000000?text=Student+Saver+Promo";
 let desc=document.getElementById("promoDesc").value;

 if(!title||!discount||!desc){alert("Please enter promo title, discount, and description.");return;}

 promos.unshift({title,category,desc:discount+" - "+desc,code,campus,claims:"0 / "+limit,img:image,active:true});
 views+=80;claims+=20;visibility=Math.min(100,visibility+5);
 renderPromos();
}

function editPromo(i){
 document.getElementById("promoTitle").value=promos[i].title;
 document.getElementById("promoDesc").value=promos[i].desc;
 openTab("promos",document.querySelectorAll(".nav button")[2]);
 window.scrollTo({top:0,behavior:"smooth"});
}

function togglePromo(i){promos[i].active=!promos[i].active;renderPromos();}
function removePromo(i){promos.splice(i,1);renderPromos();}

function activateAd(){
 visibility=100;views+=100;
 if(document.getElementById("adMsg")) document.getElementById("adMsg").innerText="Growth campaign activated successfully.";
 updateStats();
}

function saveLoyalty(){
 document.getElementById("loyaltyMsg").innerText="Suki loyalty program activated.";
 repeat+=12;visibility=Math.min(100,visibility+3);updateStats();
}

function setBilling(mode,btn){
 billingMode=mode;
 document.querySelectorAll(".billing-toggle button").forEach(b=>b.classList.remove("active"));
 btn.classList.add("active");
 if(mode==="monthly"){
   document.getElementById("proPrice").innerText="PHP 699 / month";
   document.getElementById("plusPrice").innerText="PHP 1,199 / month";
 }else{
   document.getElementById("proPrice").innerText="PHP 6,990 / year";
   document.getElementById("plusPrice").innerText="PHP 11,990 / year";
 }
}

function selectPlan(plan){
 document.getElementById("planBadge").innerText=plan;
 documen
