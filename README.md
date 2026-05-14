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
            
