<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0, user-scalable=yes">
<title>Happy 42nd Birthday Dearest Mom</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700&family=Cormorant+Garamond:ital,wght@0,300;0,500;1,400&family=Noto+Serif+TC:wght@300;400;600;700&display=swap" rel="stylesheet">
<style>
:root {
  --bg-deep: #0a0b0e;
  --bg-surface: #12141c;
  --text-pure: #ffffff;
  --text-pearl: #f1f5f9;
  --text-soft: #cbd5e1;
  --text-muted: #94a3b8;
  --pearl-border: rgba(255, 255, 255, 0.18);
  --pearl-border-glow: rgba(255, 255, 255, 0.5);
  --champagne-gold: #f3e5d8;
  --champagne-glow: rgba(243, 229, 216, 0.28);
  --glass-layer-bg: rgba(255, 255, 255, 0.035);
  --glass-shadow: rgba(0, 0, 0, 0.6);
  --transition-smooth: cubic-bezier(0.16, 1, 0.3, 1);
  --card-padding: 85px 75px;
  --title-size: 3.5rem;
  --subtitle-size: 1.35rem;
  --body-size: 1.18rem;
  --grid-columns: repeat(2, 1fr);
  --viewport-padding: 140px 20px;
}

body.is-mobile-device {
  --card-padding: 40px 24px;
  --title-size: 2.1rem;
  --subtitle-size: 1.1rem;
  --body-size: 1.02rem;
  --grid-columns: 1fr;
  --viewport-padding: 90px 14px;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  user-select: none;
  -webkit-font-smoothing: antialiased;
  -webkit-tap-highlight-color: transparent;
}

::-webkit-scrollbar {
  width: 5px;
}
::-webkit-scrollbar-track {
  background: var(--bg-deep);
}
::-webkit-scrollbar-thumb {
  background: linear-gradient(180deg, #334155, #cbd5e1, #334155);
  border-radius: 3px;
}

html, body {
  width: 100%;
  min-height: 100%;
  background-color: var(--bg-deep);
  color: var(--text-pure);
  font-family: 'Noto Serif TC', serif;
  overflow-x: hidden;
}

body {
  perspective: 1400px;
}

#bg-canvas {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: -2;
  pointer-events: none;
}

.ambient-glow {
  position: fixed;
  border-radius: 50%;
  filter: blur(140px);
  z-index: -1;
  pointer-events: none;
  opacity: 0.15;
  animation: pulseGlow 18s infinite alternate ease-in-out;
}

.glow-1 {
  top: 10%;
  left: 15%;
  width: 550px;
  height: 550px;
  background: #ffffff;
}

.glow-2 {
  bottom: 15%;
  right: 10%;
  width: 650px;
  height: 650px;
  background: #cbd5e1;
  animation-delay: -9s;
}

@keyframes pulseGlow {
  0% { transform: translate(0, 0) scale(1); }
  100% { transform: translate(40px, 60px) scale(1.12); }
}

.top-hud-bar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  padding: 24px 40px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  z-index: 1000;
  background: linear-gradient(180deg, rgba(10, 11, 14, 0.9) 0%, rgba(10, 11, 14, 0) 100%);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  transition: padding 0.4s ease;
}

body.is-mobile-device .top-hud-bar {
  padding: 16px 20px;
}

.hud-title-group {
  display: flex;
  align-items: center;
  gap: 12px;
}

.hud-logo-icon {
  width: 18px;
  height: 18px;
  stroke: var(--text-pure);
  stroke-width: 1.5;
  fill: none;
  transform: rotate(45deg);
}

.hud-brand-name {
  font-family: 'Cinzel', serif;
  font-size: 0.9rem;
  letter-spacing: 4px;
  color: var(--text-pure);
  font-weight: 600;
}

body.is-mobile-device .hud-brand-name {
  font-size: 0.75rem;
  letter-spacing: 2px;
}

.hud-right-group {
  display: flex;
  align-items: center;
  gap: 15px;
}

.hud-date-badge {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.05rem;
  letter-spacing: 3px;
  color: var(--text-muted);
}

body.is-mobile-device .hud-date-badge {
  font-size: 0.85rem;
  letter-spacing: 1px;
}

.device-indicator-tag {
  font-family: 'Cinzel', serif;
  font-size: 0.65rem;
  letter-spacing: 2px;
  color: var(--champagne-gold);
  padding: 3px 10px;
  border: 1px solid rgba(243, 229, 216, 0.3);
  border-radius: 12px;
  background: rgba(243, 229, 216, 0.05);
}

.scroll-progress-line {
  position: fixed;
  top: 0;
  left: 0;
  height: 2px;
  background: linear-gradient(90deg, #334155, var(--text-pure), var(--champagne-gold));
  z-index: 1001;
  width: 0%;
  transition: width 0.1s linear;
}

.scroll-guide-hint {
  position: fixed;
  bottom: 25px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  z-index: 900;
  pointer-events: none;
  transition: opacity 0.6s ease;
}

.scroll-guide-line {
  width: 1px;
  height: 35px;
  background: linear-gradient(180deg, var(--text-pure), transparent);
  animation: guideLinePulse 2s infinite ease-in-out;
}

@keyframes guideLinePulse {
  0%, 100% { transform: scaleY(0.6); opacity: 0.3; }
  50% { transform: scaleY(1); opacity: 1; }
}

.scroll-guide-text {
  font-family: 'Cinzel', serif;
  font-size: 0.65rem;
  letter-spacing: 3px;
  color: var(--text-muted);
}

.main-viewport-wrapper {
  width: 100%;
  position: relative;
}

.viewport-section {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: var(--viewport-padding);
  position: relative;
  transform-style: preserve-3d;
}

.pearl-glass-card {
  width: 100%;
  max-width: 980px;
  background: var(--glass-layer-bg);
  backdrop-filter: blur(35px);
  -webkit-backdrop-filter: blur(35px);
  border: 1px solid var(--pearl-border);
  border-radius: 10px;
  padding: var(--card-padding);
  box-shadow: 0 30px 90px var(--glass-shadow), inset 0 0 35px rgba(255, 255, 255, 0.03);
  transition: transform 1s var(--transition-smooth), opacity 1s ease, border-color 0.5s ease, box-shadow 0.5s ease;
  transform-style: preserve-3d;
  position: relative;
  overflow: hidden;
}

.pearl-glass-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle at var(--mouse-x, 50%) var(--mouse-y, 50%), rgba(255, 255, 255, 0.08) 0%, transparent 65%);
  pointer-events: none;
}

body.is-desktop-device .pearl-glass-card:hover {
  border-color: var(--pearl-border-glow);
  box-shadow: 0 45px 110px rgba(0, 0, 0, 0.85), inset 0 0 45px rgba(255, 255, 255, 0.06);
}

body.is-mobile-device .pearl-glass-card {
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  box-shadow: 0 15px 45px rgba(0,0,0,0.5);
}

.background-watermark {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-family: 'Cinzel', serif;
  font-size: 12rem;
  font-weight: 700;
  color: rgba(255, 255, 255, 0.015);
  letter-spacing: 12px;
  pointer-events: none;
  white-space: nowrap;
  z-index: 0;
}

body.is-mobile-device .background-watermark {
  font-size: 5.5rem;
  letter-spacing: 4px;
}

.card-inner-body {
  position: relative;
  z-index: 1;
}

.card-origami-hidden-top {
  transform: translateY(100px) rotateX(-25deg) translateZ(-100px) scale(0.9);
  opacity: 0;
  filter: blur(10px);
}

.card-origami-hidden-bottom {
  transform: translateY(-100px) rotateX(25deg) translateZ(-100px) scale(0.9);
  opacity: 0;
  filter: blur(10px);
}

body.is-mobile-device .card-origami-hidden-top,
body.is-mobile-device .card-origami-hidden-bottom {
  transform: translateY(50px) scale(0.95);
  filter: blur(5px);
}

.card-origami-visible {
  transform: translateY(0) rotateX(0deg) translateZ(0px) scale(1) !important;
  opacity: 1 !important;
  filter: blur(0px) !important;
}

.card-header-badge-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
  padding-bottom: 20px;
  margin-bottom: 35px;
}

body.is-mobile-device .card-header-badge-row {
  padding-bottom: 15px;
  margin-bottom: 25px;
}

.badge-tag {
  font-family: 'Cinzel', serif;
  font-size: 0.75rem;
  letter-spacing: 3px;
  color: var(--champagne-gold);
  padding: 5px 15px;
  border: 1px solid rgba(243, 229, 216, 0.3);
  border-radius: 20px;
  background: rgba(243, 229, 216, 0.04);
}

body.is-mobile-device .badge-tag {
  font-size: 0.65rem;
  letter-spacing: 1.5px;
  padding: 4px 10px;
}

.badge-number {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.15rem;
  letter-spacing: 3px;
  color: var(--text-muted);
}

body.is-mobile-device .badge-number {
  font-size: 0.95rem;
}

.hero-main-title {
  font-size: var(--title-size);
  font-weight: 500;
  letter-spacing: 6px;
  color: var(--text-pure);
  text-align: center;
  line-height: 1.3;
  margin-bottom: 15px;
  text-shadow: 0 0 35px rgba(255, 255, 255, 0.25);
}

.hero-sub-title {
  font-family: 'Cormorant Garamond', serif;
  font-size: var(--subtitle-size);
  letter-spacing: 4px;
  color: var(--text-muted);
  text-align: center;
  margin-bottom: 30px;
  font-style: italic;
}

.accent-gold-divider {
  width: 70px;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--champagne-gold), transparent);
  margin: 0 auto 35px auto;
}

.prose-paragraph {
  font-size: var(--body-size);
  line-height: 2.2;
  color: var(--text-soft);
  text-align: justify;
  font-weight: 300;
  margin-bottom: 20px;
}

.moments-grid {
  display: grid;
  grid-template-columns: var(--grid-columns);
  gap: 25px;
  margin-top: 35px;
}

.moment-card-box {
  background: rgba(255, 255, 255, 0.018);
  border: 1px solid var(--pearl-border);
  border-radius: 8px;
  padding: 32px 28px;
  transition: all 0.4s var(--transition-smooth);
}

body.is-desktop-device .moment-card-box:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: var(--pearl-border-glow);
  transform: translateY(-5px);
}

body.is-mobile-device .moment-card-box {
  padding: 24px 20px;
}

body.is-mobile-device .moment-card-box:active {
  background: rgba(255, 255, 255, 0.06);
}

.moment-icon-svg {
  width: 40px;
  height: 40px;
  margin-bottom: 18px;
  stroke: var(--champagne-gold);
  stroke-width: 1.2;
  fill: none;
}

.moment-title {
  font-size: 1.2rem;
  font-weight: 600;
  color: var(--text-pure);
  margin-bottom: 10px;
  letter-spacing: 2px;
}

.moment-desc {
  font-size: 0.95rem;
  line-height: 1.9;
  color: var(--text-muted);
  font-weight: 300;
}

.blessings-wall-grid {
  display: grid;
  grid-template-columns: var(--grid-columns);
  gap: 20px;
  margin-top: 35px;
}

.blessing-card-item {
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--pearl-border);
  border-radius: 8px;
  padding: 26px 24px;
  transition: all 0.4s ease;
}

body.is-desktop-device .blessing-card-item:hover {
  background: rgba(255, 255, 255, 0.055);
  border-color: var(--pearl-border-glow);
  transform: translateY(-4px);
}

body.is-mobile-device .blessing-card-item {
  padding: 20px 18px;
}

.blessing-tag-title {
  font-family: 'Cinzel', serif;
  font-size: 0.8rem;
  letter-spacing: 2.5px;
  color: var(--champagne-gold);
  margin-bottom: 8px;
}

.blessing-content-text {
  font-size: 1.02rem;
  line-height: 1.95;
  color: var(--text-pearl);
  font-weight: 300;
}

.letter-unfold-container {
  margin-top: 35px;
  text-align: center;
}

.unfold-action-button {
  background: transparent;
  border: 1px solid var(--text-pure);
  color: var(--text-pure);
  padding: 16px 45px;
  font-family: 'Noto Serif TC', serif;
  font-size: 1rem;
  letter-spacing: 4px;
  cursor: pointer;
  transition: all 0.4s ease;
  position: relative;
  overflow: hidden;
  border-radius: 4px;
  min-height: 50px;
}

body.is-mobile-device .unfold-action-button {
  width: 100%;
  padding: 15px 20px;
  font-size: 0.92rem;
  letter-spacing: 2px;
}

.unfold-action-button::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.25), transparent);
  transition: left 0.7s ease;
}

.unfold-action-button:hover::before {
  left: 100%;
}

.unfold-action-button:hover, .unfold-action-button:active {
  background: var(--text-pure);
  color: var(--bg-deep);
  box-shadow: 0 0 30px rgba(255, 255, 255, 0.3);
}

.letter-content-vault {
  max-height: 0;
  overflow: hidden;
  transition: max-height 1.2s var(--transition-smooth), opacity 1s ease;
  opacity: 0;
  text-align: left;
  margin-top: 35px;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  padding-top: 35px;
}

.letter-content-vault.expanded {
  max-height: 1400px;
  opacity: 1;
}

.letter-salutation-title {
  font-size: 1.3rem;
  color: var(--champagne-gold);
  margin-bottom: 20px;
  font-weight: 600;
  letter-spacing: 2px;
}

.letter-prose-block {
  font-size: var(--body-size);
  line-height: 2.2;
  color: var(--text-soft);
  font-weight: 300;
  margin-bottom: 20px;
  text-align: justify;
}

.letter-signature-foot {
  text-align: right;
  margin-top: 40px;
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.25rem;
  color: var(--text-pure);
  letter-spacing: 3px;
  font-style: italic;
}

.footer-credits-bar {
  text-align: center;
  padding: 60px 20px;
  background: rgba(10, 11, 14, 0.95);
  border-top: 1px solid rgba(255, 255, 255, 0.05);
  font-family: 'Cinzel', serif;
  font-size: 0.75rem;
  letter-spacing: 4px;
  color: var(--text-muted);
}

body.is-mobile-device .footer-credits-bar {
  padding: 40px 15px;
  font-size: 0.65rem;
  letter-spacing: 2px;
}
</style>
</head>
<body>

<canvas id="bg-canvas"></canvas>
<div class="ambient-glow glow-1"></div>
<div class="ambient-glow glow-2"></div>
<div class="scroll-progress-line" id="scrollProgressLine"></div>

<div class="top-hud-bar">
  <div class="hud-title-group">
    <svg class="hud-logo-icon" viewBox="0 0 24 24">
      <rect x="4" y="4" width="16" height="16"/>
    </svg>
    <span class="hud-brand-name">CELEBRATING MOM</span>
  </div>
  <div class="hud-right-group">
    <span class="device-indicator-tag" id="deviceTag">DETECTING...</span>
    <div class="hud-date-badge">JULY 28 · 42ND</div>
  </div>
</div>

<div class="scroll-guide-hint" id="scrollGuideHint">
  <div class="scroll-guide-line"></div>
  <span class="scroll-guide-text">SCROLL</span>
</div>

<div class="main-viewport-wrapper">

  <section class="viewport-section">
    <div class="pearl-glass-card card-origami-hidden-top card-origami-visible" id="sectionCard1">
      <div class="background-watermark">AGE 42</div>
      <div class="card-inner-body">
        <div class="card-header-badge-row">
          <span class="badge-tag">HAPPY 42ND BIRTHDAY</span>
          <span class="badge-number">07.28</span>
        </div>
        <h1 class="hero-main-title">媽媽 42歲生日快樂</h1>
        <div class="hero-sub-title">To My Dearest Mom, With All My Love</div>
        <div class="accent-gold-divider"></div>
        <p class="prose-paragraph">
          祝最美麗的媽媽 42 歲生日快樂！雖然我今年才 12 歲，還不太會說很深奧的大道理，但我知道您每天為了我們這個家付出了好多好多。在這個特別的日子裡，我想把最真心、最溫暖的祝福通通送給您。
        </p>
      </div>
    </div>
  </section>

  <section class="viewport-section">
    <div class="pearl-glass-card card-origami-hidden-bottom" id="sectionCard2">
      <div class="background-watermark">THANKS</div>
      <div class="card-inner-body">
        <div class="card-header-badge-row">
          <span class="badge-tag">GRATITUDE // 感謝點點滴滴</span>
          <span class="badge-number">PART 01</span>
        </div>
        <h2 style="font-size: clamp(1.6rem, 4vw, 2.3rem); text-align: center; color: #fff; letter-spacing: 4px; font-weight: 500; margin-bottom: 12px;">謝謝媽媽每天的照顧</h2>
        <div class="accent-gold-divider"></div>

        <div class="moments-grid">
          <div class="moment-card-box">
            <svg class="moment-icon-svg" viewBox="0 0 24 24">
              <path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/>
            </svg>
            <div class="moment-title">溫暖又美味的飯菜</div>
            <div class="moment-desc">
              不管是每天放學回家的熱湯，還是特別為我準備的好吃料理，每一口都能吃到媽媽滿滿的愛。
            </div>
          </div>

          <div class="moment-card-box">
            <svg class="moment-icon-svg" viewBox="0 0 24 24">
              <polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/>
            </svg>
            <div class="moment-title">耐心的陪伴與教導</div>
            <div class="moment-desc">
              當我有不懂的事或心情不好的時候，媽媽總是很有耐心地聽我說，給我最溫暖的鼓勵與支持。
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <section class="viewport-section">
    <div class="pearl-glass-card card-origami-hidden-top" id="sectionCard3">
      <div class="background-watermark">BLESS</div>
      <div class="card-inner-body">
        <div class="card-header-badge-row">
          <span class="badge-tag">WISHES // 給媽媽的真心祝願</span>
          <span class="badge-number">PART 02</span>
        </div>
        <h2 style="font-size: clamp(1.6rem, 4vw, 2.3rem); text-align: center; color: #fff; letter-spacing: 4px; font-weight: 500; margin-bottom: 12px;">給 42 歲媽媽的祝福牆</h2>
        <div class="accent-gold-divider"></div>

        <div class="blessings-wall-grid">
          <div class="blessing-card-item">
            <div class="blessing-tag-title">WISH 01 // 健康第一</div>
            <div class="blessing-content-text">
              希望媽媽每天都健健康康、體力滿滿，不要太累，記得要多休息！
            </div>
          </div>

          <div class="blessing-card-item">
            <div class="blessing-tag-title">WISH 02 // 永遠漂亮</div>
            <div class="blessing-content-text">
              在我的心裡媽媽永遠是最漂亮的！希望您每一天都笑口常開、心情好！
            </div>
          </div>

          <div class="blessing-card-item">
            <div class="blessing-tag-title">WISH 03 // 平安順心</div>
            <div class="blessing-content-text">
              祝媽媽 42 歲這一年的每一天，事情都很順利，沒有煩惱、只有開心！
            </div>
          </div>

          <div class="blessing-card-item">
            <div class="blessing-tag-title">WISH 04 // 幸福滿滿</div>
            <div class="blessing-content-text">
              謝謝媽媽為我們做的一切，換我們好好愛您，讓您每天都覺得很幸福！
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <section class="viewport-section">
    <div class="pearl-glass-card card-origami-hidden-bottom" id="sectionCard4">
      <div class="background-watermark">LETTER</div>
      <div class="card-inner-body">
        <div class="card-header-badge-row">
          <span class="badge-tag">HEARTFELT // 孩子的手寫信</span>
          <span class="badge-number">FINAL</span>
        </div>
        <h2 style="font-size: clamp(1.6rem, 4vw, 2.3rem); text-align: center; color: #fff; letter-spacing: 4px; font-weight: 500; margin-bottom: 12px;">給媽媽的一封信</h2>
        <div class="accent-gold-divider"></div>

        <div class="letter-unfold-container">
          <button class="unfold-action-button" onclick="toggleLetterView()">點擊打開專屬信箋</button>

          <div class="letter-content-vault" id="letterVaultBlock">
            <div class="letter-salutation-title">親愛的媽媽：</div>
            <div class="letter-prose-block">
              祝您 42 歲生日快樂！
            </div>
            <div class="letter-prose-block">
              平常我可能不太好意思直接當面說這些話，所以用這個網站寫下來給您看。
            </div>
            <div class="letter-prose-block">
              謝謝您每天照顧我的生活，煮好吃的飯菜給我吃，還教了我很多做人做事的道理。雖然有時候我也會讓您操心或惹您生氣，但我真的非常感謝您對我的包容與愛護。
            </div>
            <div class="letter-prose-block">
              42 歲的媽媽依然超級有活力又漂亮！新的一年，希望您可以少辛苦一點，多享受自己的生活。祝您身體健康、平平安安、天天都有好心情！
            </div>
            <div class="letter-signature-foot">
              —— 愛您的孩子 敬上<br>
              2026 年 7 月 28 日
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

</div>

<footer class="footer-credits-bar">
  PEARL GLASS BIRTHDAY EDITION // DUAL-ENGINE ADAPTIVE SYSTEM FOR MOM
</footer>

<script>
let isMobile = false;

function detectDeviceEnvironment() {
  const userAgent = navigator.userAgent || navigator.vendor || window.opera;
  const isTouchDevice = ('ontouchstart' in window) || (navigator.maxTouchPoints > 0);
  const isSmallScreen = window.innerWidth <= 768;

  if (/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(userAgent) || (isTouchDevice && isSmallScreen)) {
    isMobile = true;
    document.body.classList.add('is-mobile-device');
    document.body.classList.remove('is-desktop-device');
    document.getElementById('deviceTag').innerText = 'MOBILE MODE';
  } else {
    isMobile = false;
    document.body.classList.add('is-desktop-device');
    document.body.classList.remove('is-mobile-device');
    document.getElementById('deviceTag').innerText = 'DESKTOP MODE';
  }
}

detectDeviceEnvironment();
window.addEventListener('resize', detectDeviceEnvironment);

const bgCanvas = document.getElementById('bg-canvas');
const ctx = bgCanvas.getContext('2d');

let width = bgCanvas.width = window.innerWidth;
let height = bgCanvas.height = window.innerHeight;

let mouseX = width / 2;
let mouseY = height / 2;

window.addEventListener('resize', () => {
  width = bgCanvas.width = window.innerWidth;
  height = bgCanvas.height = window.innerHeight;
});

window.addEventListener('mousemove', (e) => {
  if (!isMobile) {
    mouseX = e.clientX;
    mouseY = e.clientY;
  }
});

window.addEventListener('touchmove', (e) => {
  if (e.touches.length > 0) {
    mouseX = e.touches[0].clientX;
    mouseY = e.touches[0].clientY;
  }
}, { passive: true });

class FloatingDust {
  constructor() {
    this.x = Math.random() * width;
    this.y = Math.random() * height;
    this.vx = (Math.random() - 0.5) * 0.35;
    this.vy = (Math.random() - 0.5) * 0.35;
    this.radius = Math.random() * 1.5 + 0.4;
  }
  update() {
    this.x += this.vx;
    this.y += this.vy;

    if (this.x < 0 || this.x > width) this.vx *= -1;
    if (this.y < 0 || this.y > height) this.vy *= -1;

    const dx = mouseX - this.x;
    const dy = mouseY - this.y;
    const dist = Math.sqrt(dx * dx + dy * dy);
    if (dist < 120) {
      const angle = Math.atan2(dy, dx);
      const force = (120 - dist) / 120;
      this.x -= Math.cos(angle) * force * 2;
      this.y -= Math.sin(angle) * force * 2;
    }
  }
  draw() {
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
    ctx.fillStyle = 'rgba(255, 255, 255, 0.25)';
    ctx.fill();
  }
}

const particleCount = isMobile ? 35 : 75;
const dustParticles = Array.from({ length: particleCount }, () => new FloatingDust());

function renderCanvasAnimation() {
  ctx.clearRect(0, 0, width, height);

  const maxDist = isMobile ? 90 : 120;
  for (let i = 0; i < dustParticles.length; i++) {
    for (let j = i + 1; j < dustParticles.length; j++) {
      const dx = dustParticles[i].x - dustParticles[j].x;
      const dy = dustParticles[i].y - dustParticles[j].y;
      const dist = Math.sqrt(dx * dx + dy * dy);

      if (dist < maxDist) {
        ctx.beginPath();
        ctx.moveTo(dustParticles[i].x, dustParticles[i].y);
        ctx.lineTo(dustParticles[j].x, dustParticles[j].y);
        ctx.strokeStyle = `rgba(255, 255, 255, ${0.07 * (1 - dist / maxDist)})`;
        ctx.lineWidth = 0.5;
        ctx.stroke();
      }
    }
  }

  dustParticles.forEach(particle => {
    particle.update();
    particle.draw();
  });

  requestAnimationFrame(renderCanvasAnimation);
}
renderCanvasAnimation();

const cardElements = [
  document.getElementById('sectionCard1'),
  document.getElementById('sectionCard2'),
  document.getElementById('sectionCard3'),
  document.getElementById('sectionCard4')
];

function handleScrollObserver() {
  const scrollY = window.scrollY;
  const maxScroll = document.documentElement.scrollHeight - window.innerHeight;
  const progress = maxScroll > 0 ? (scrollY / maxScroll) * 100 : 0;

  document.getElementById('scrollProgressLine').style.width = `${progress}%`;

  if (scrollY > 60) {
    document.getElementById('scrollGuideHint').style.opacity = '0';
  } else {
    document.getElementById('scrollGuideHint').style.opacity = '1';
  }

  const viewHeight = window.innerHeight;
  const thresholdRatio = isMobile ? 0.6 : 0.45;

  cardElements.forEach(card => {
    const rect = card.getBoundingClientRect();
    const cardCenter = rect.top + rect.height / 2;
    const screenCenter = viewHeight / 2;

    if (Math.abs(cardCenter - screenCenter) < viewHeight * thresholdRatio) {
      card.classList.add('card-origami-visible');
    } else {
      card.classList.remove('card-origami-visible');
    }
  });
}

window.addEventListener('scroll', handleScrollObserver, { passive: true });
handleScrollObserver();

cardElements.forEach(card => {
  card.addEventListener('mousemove', (e) => {
    if (isMobile) return;
    const rect = card.getBoundingClientRect();
    const x = e.clientX - rect.left;
    const y = e.clientY - rect.top;

    const centerX = rect.width / 2;
    const centerY = rect.height / 2;

    const rotateX = ((y - centerY) / centerY) * -5;
    const rotateY = ((x - centerX) / centerX) * 5;

    card.style.setProperty('--mouse-x', `${(x / rect.width) * 100}%`);
    card.style.setProperty('--mouse-y', `${(y / rect.height) * 100}%`);
    card.style.transform = `perspective(1000px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) translateZ(8px)`;
  });

  card.addEventListener('mouseleave', () => {
    if (isMobile) return;
    card.style.transform = '';
  });
});

function toggleLetterView() {
  const vault = document.getElementById('letterVaultBlock');
  const btn = document.querySelector('.unfold-action-button');

  if (vault.classList.contains('expanded')) {
    vault.classList.remove('expanded');
    btn.innerText = '點擊打開專屬信箋';
  } else {
    vault.classList.add('expanded');
    btn.innerText = '收合信箋';
  }
}
</script>
</body>
</html>
