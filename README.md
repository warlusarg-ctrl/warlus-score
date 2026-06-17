
  [athlete-score (2).html](https://github.com/user-attachments/files/29068894/athlete-score.2.html)

<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>WARLUS — Athlete Score</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@700;900&family=Barlow:wght@400;500;600&display=swap');

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --navy:        #0F1B3C;
    --navy-mid:    #1A2B52;
    --navy-deep:   #0A1228;
    --blue-accent: #2E5BFF;
    --blue-light:  #4A8CFF;
    --gold:        #C8A84B;
    --gold-light:  #E8C96A;
    --white:       #FFFFFF;
    --gray:        #8A94A6;
    --danger:      #FF3B30;
    --warning:     #FF9500;
    --ok:          #34C759;
  }

  html, body {
    min-height: 100%;
    background: var(--navy-deep);
    font-family: 'Barlow', sans-serif;
    color: var(--white);
    -webkit-font-smoothing: antialiased;
  }

  /* ── SCREENS ── */
  .screen {
    display: none;
    min-height: 100vh;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 32px 24px;
    animation: fadeIn 0.4s ease;
  }
  .screen.active { display: flex; }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(10px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* ── LOGO ── */
  .logo {
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 900;
    font-size: 26px;
    letter-spacing: 4px;
    color: var(--white);
    text-align: center;
    margin-bottom: 6px;
  }
  .logo-mark {
    width: 28px;
    height: 36px;
    margin: 0 auto 6px;
    display: block;
  }
  .tagline {
    font-size: 10px;
    letter-spacing: 3px;
    color: var(--gold);
    text-transform: uppercase;
    text-align: center;
    margin-bottom: 40px;
  }

  /* ── INTRO ── */
  .badge {
    display: inline-block;
    border: 1px solid var(--gold);
    color: var(--gold);
    font-size: 10px;
    letter-spacing: 3px;
    text-transform: uppercase;
    padding: 5px 14px;
    border-radius: 2px;
    margin-bottom: 24px;
  }
  .intro-headline {
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 900;
    font-size: clamp(36px, 9vw, 58px);
    line-height: 0.95;
    text-align: center;
    text-transform: uppercase;
    margin-bottom: 20px;
    max-width: 420px;
  }
  .intro-headline em {
    color: var(--gold);
    font-style: normal;
  }
  .intro-sub {
    font-size: 14px;
    color: var(--gray);
    text-align: center;
    margin-bottom: 36px;
    max-width: 300px;
    line-height: 1.6;
  }

  /* dimensiones */
  .dims {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 8px;
    width: 100%;
    max-width: 360px;
    margin-bottom: 40px;
  }
  .dim-pill {
    background: rgba(200,168,75,0.08);
    border: 1px solid rgba(200,168,75,0.25);
    border-radius: 4px;
    padding: 10px 12px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .dim-pill span { font-size: 16px; }
  .dim-pill p {
    font-size: 11px;
    color: var(--gold-light);
    letter-spacing: 0.5px;
    text-transform: uppercase;
    font-weight: 600;
  }

  /* ── BUTTONS ── */
  .btn-primary {
    background: var(--gold);
    color: var(--navy-deep);
    border: none;
    border-radius: 4px;
    padding: 18px 48px;
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 900;
    font-size: 17px;
    letter-spacing: 3px;
    text-transform: uppercase;
    cursor: pointer;
    width: 100%;
    max-width: 340px;
    transition: background 0.2s, transform 0.1s;
  }
  .btn-primary:hover  { background: var(--gold-light); }
  .btn-primary:active { transform: scale(0.98); }

  .btn-secondary {
    background: transparent;
    color: var(--gray);
    border: 1px solid rgba(255,255,255,0.12);
    border-radius: 4px;
    padding: 14px 48px;
    font-family: 'Barlow', sans-serif;
    font-weight: 500;
    font-size: 14px;
    cursor: pointer;
    width: 100%;
    max-width: 340px;
    margin-top: 12px;
    transition: border-color 0.2s;
  }
  .btn-secondary:hover { border-color: rgba(255,255,255,0.3); color: var(--white); }

  /* ── QUESTION ── */
  .progress-bar-wrap {
    width: 100%;
    max-width: 440px;
    height: 2px;
    background: rgba(255,255,255,0.08);
    margin-bottom: 36px;
  }
  .progress-bar-fill {
    height: 100%;
    background: var(--gold);
    transition: width 0.5s ease;
  }

  .q-meta {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    max-width: 440px;
    margin-bottom: 8px;
  }
  .q-counter {
    font-size: 10px;
    color: var(--gray);
    letter-spacing: 2px;
    text-transform: uppercase;
  }
  .q-dimension {
    font-size: 10px;
    color: var(--gold);
    letter-spacing: 2px;
    text-transform: uppercase;
  }

  .q-text {
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 900;
    font-size: clamp(24px, 6vw, 34px);
    text-align: center;
    line-height: 1.1;
    margin-bottom: 36px;
    max-width: 400px;
    text-transform: uppercase;
  }

  .options {
    display: flex;
    flex-direction: column;
    gap: 10px;
    width: 100%;
    max-width: 440px;
  }
  .option-btn {
    background: rgba(255,255,255,0.03);
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: 6px;
    padding: 15px 18px;
    color: var(--white);
    font-family: 'Barlow', sans-serif;
    font-size: 14px;
    font-weight: 500;
    cursor: pointer;
    text-align: left;
    transition: border-color 0.15s, background 0.15s;
    display: flex;
    align-items: center;
    gap: 14px;
  }
  .option-btn:hover {
    border-color: var(--gold);
    background: rgba(200,168,75,0.07);
  }
  .option-btn.selected {
    border-color: var(--gold);
    background: rgba(200,168,75,0.13);
  }
  .option-letter {
    width: 26px;
    height: 26px;
    border-radius: 50%;
    border: 1px solid rgba(255,255,255,0.18);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 11px;
    font-weight: 700;
    flex-shrink: 0;
    transition: background 0.15s, border-color 0.15s;
  }
  .option-btn.selected .option-letter {
    background: var(--gold);
    border-color: var(--gold);
    color: var(--navy-deep);
  }

  /* ── EMAIL ── */
  .email-headline {
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 900;
    font-size: clamp(30px, 7vw, 44px);
    text-align: center;
    text-transform: uppercase;
    line-height: 1.05;
    margin-bottom: 12px;
  }
  .email-headline em { color: var(--gold); font-style: normal; }
  .email-sub {
    color: var(--gray);
    font-size: 14px;
    text-align: center;
    margin-bottom: 32px;
    max-width: 300px;
    line-height: 1.6;
  }
  .input-wrap { width: 100%; max-width: 420px; margin-bottom: 12px; }
  .input-wrap input {
    width: 100%;
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.12);
    border-radius: 6px;
    padding: 16px 18px;
    color: var(--white);
    font-family: 'Barlow', sans-serif;
    font-size: 15px;
    outline: none;
    transition: border-color 0.2s;
  }
  .input-wrap input::placeholder { color: var(--gray); }
  .input-wrap input:focus { border-color: var(--gold); }
  .privacy-note {
    font-size: 11px;
    color: var(--gray);
    text-align: center;
    margin-bottom: 28px;
    opacity: 0.7;
  }

  /* ── RESULT ── */
  .score-ring-wrap {
    position: relative;
    width: 170px;
    height: 170px;
    margin: 0 auto 20px;
  }
  .score-ring-svg {
    width: 170px;
    height: 170px;
    transform: rotate(-90deg);
  }
  .score-ring-bg   { fill: none; stroke: rgba(255,255,255,0.06); stroke-width: 7; }
  .score-ring-fill {
    fill: none;
    stroke-width: 7;
    stroke-linecap: round;
    transition: stroke-dashoffset 1.4s cubic-bezier(0.4,0,0.2,1), stroke 0.5s;
  }
  .score-number {
    position: absolute; inset: 0;
    display: flex; flex-direction: column;
    align-items: center; justify-content: center;
  }
  .score-digit {
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 900;
    font-size: 54px;
    line-height: 1;
  }
  .score-max { font-size: 12px; color: var(--gray); letter-spacing: 1px; }

  .score-label {
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 900;
    font-size: 20px;
    letter-spacing: 4px;
    text-transform: uppercase;
    text-align: center;
    margin-bottom: 8px;
  }
  .score-desc {
    font-size: 14px;
    color: var(--gray);
    text-align: center;
    max-width: 320px;
    line-height: 1.65;
    margin-bottom: 28px;
  }

  /* barras por dimensión */
  .dim-bars {
    width: 100%;
    max-width: 440px;
    display: flex;
    flex-direction: column;
    gap: 14px;
    margin-bottom: 28px;
  }
  .dim-bar-row { display: flex; flex-direction: column; gap: 5px; }
  .dim-bar-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .dim-bar-label {
    font-size: 11px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--gray);
    font-weight: 600;
  }
  .dim-bar-pct { font-size: 12px; color: var(--gold); font-weight: 700; }
  .dim-bar-track {
    width: 100%;
    height: 4px;
    background: rgba(255,255,255,0.07);
    border-radius: 2px;
    overflow: hidden;
  }
  .dim-bar-fill {
    height: 100%;
    background: var(--gold);
    border-radius: 2px;
    width: 0%;
    transition: width 1.2s cubic-bezier(0.4,0,0.2,1);
  }

  .divider {
    width: 100%;
    max-width: 440px;
    height: 1px;
    background: rgba(255,255,255,0.07);
    margin: 4px 0 24px;
  }
  .share-note {
    font-size: 11px;
    color: var(--gray);
    text-align: center;
    margin-top: 14px;
    letter-spacing: 0.5px;
    opacity: 0.7;
  }

  .brand-footer { margin-top: 40px; text-align: center; }
  .brand-footer .logo { font-size: 18px; margin-bottom: 6px; }
  .brand-footer p { font-size: 11px; color: var(--gray); letter-spacing: 1px; line-height: 1.6; }
</style>
</head>
<body>

<!-- ══════════════════════════════════════
     SCREEN 1 — INTRO
══════════════════════════════════════ -->
<div class="screen active" id="screen-intro">
  <img class="logo-mark" src="data:image/png;base64,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" alt="WARLUS"/>
  <div class="logo">WARLUS</div>
  <div class="tagline">Alto Rendimiento</div>

  <div class="badge">Evaluación de Atleta</div>

  <h1 class="intro-headline">¿Qué tan<br><em>atleta</em><br>sos realmente?</h1>
  <p class="intro-sub">7 preguntas. 60 segundos. Descubrí tu nivel real en las 4 dimensiones que separan al atleta amateur del de alto rendimiento.</p>

  <div class="dims">
    <div class="dim-pill"><span>🧠</span><p>Mentalidad</p></div>
    <div class="dim-pill"><span>🔁</span><p>Consistencia</p></div>
    <div class="dim-pill"><span>⚡</span><p>Rendimiento</p></div>
    <div class="dim-pill"><span>🌙</span><p>Recuperación</p></div>
  </div>

  <button class="btn-primary" onclick="startQuiz()">DESCUBRIR MI ATHLETE SCORE</button>
</div>

<!-- ══════════════════════════════════════
     SCREEN 2 — PREGUNTAS
══════════════════════════════════════ -->
<div class="screen" id="screen-quiz">
  <div style="width:100%;max-width:440px">
    <div class="progress-bar-wrap">
      <div class="progress-bar-fill" id="progress-fill" style="width:0%"></div>
    </div>
  </div>
  <div class="q-meta">
    <span class="q-counter" id="q-counter">PREGUNTA 1 DE 7</span>
    <span class="q-dimension" id="q-dimension">MENTALIDAD</span>
  </div>
  <div class="q-text" id="q-text"></div>
  <div class="options" id="options-wrap"></div>
</div>

<!-- ══════════════════════════════════════
     SCREEN 3 — EMAIL
══════════════════════════════════════ -->
<div class="screen" id="screen-email">
  <img class="logo-mark" src="data:image/png;base64,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" alt="WARLUS"/>
  <div class="logo">WARLUS</div>

  <h2 class="email-headline">Tu <em>Athlete<br>Score</em> está listo.</h2>
  <p class="email-sub">Dejá tu mail y recibís tu análisis completo con el desglose por dimensión y tu plan de mejora.</p>

  <div class="input-wrap">
    <input type="text" id="input-name" placeholder="Tu nombre" autocomplete="given-name"/>
  </div>
  <div class="input-wrap">
    <input type="email" id="input-email" placeholder="Tu email" autocomplete="email"/>
  </div>
  <p class="privacy-note">Sin spam. Solo contenido de rendimiento.</p>

  <button class="btn-primary" onclick="submitAndShow()">VER MI ATHLETE SCORE</button>
  <button class="btn-secondary" onclick="showResult()">Ver sin guardar</button>
</div>

<!-- ══════════════════════════════════════
     SCREEN 4 — RESULTADO
══════════════════════════════════════ -->
<div class="screen" id="screen-result">
  <div class="logo">WARLUS</div>
  <div class="tagline" style="margin-bottom:24px">Athlete Score</div>

  <div class="score-ring-wrap">
    <svg class="score-ring-svg" viewBox="0 0 170 170">
      <circle class="score-ring-bg"   cx="85" cy="85" r="73"/>
      <circle class="score-ring-fill" id="ring-fill" cx="85" cy="85" r="73"
        stroke-dasharray="459" stroke-dashoffset="459"/>
    </svg>
    <div class="score-number">
      <span class="score-digit" id="score-digit">0</span>
      <span class="score-max">/ 100</span>
    </div>
  </div>

  <div class="score-label" id="score-label">—</div>
  <p class="score-desc" id="score-desc"></p>

  <!-- barras por dimensión -->
  <div class="dim-bars" id="dim-bars"></div>

  <div class="divider"></div>

  <button class="btn-primary" onclick="shareScore()">COMPARTIR MI ATHLETE SCORE</button>
  <button class="btn-secondary" onclick="restartQuiz()">Repetir el test</button>
  <p class="share-note">Retá a tu equipo — ¿quién llega a Elite?</p>

  <div class="brand-footer">
    <div class="logo" style="margin-top:36px">WARLUS</div>
    <p>No gana el que más entrena.<br>Gana el que mejor se recupera.</p>
  </div>
</div>

<script>
// ═══════════════════════════════════════
//  PREGUNTAS — 4 dimensiones, 7 preguntas
// ═══════════════════════════════════════
const QUESTIONS = [
  // ── MENTALIDAD ──
  {
    dimension: 'MENTALIDAD',
    text: '¿QUÉ HACÉS CUANDO\nFALLÁS UN ENTRENAMIENTO?',
    weight: 0.14,
    options: [
      { label: 'Lo compensa al día siguiente aunque no toque',     score: 0.2 },
      { label: 'Me frustra, pero sigo adelante',                   score: 0.6 },
      { label: 'Lo analizo para entender por qué pasó',            score: 0.9 },
      { label: 'Lo registro y ajusto el plan de la semana',        score: 1.0 },
    ]
  },
  {
    dimension: 'MENTALIDAD',
    text: '¿QUÉ HACÉS CUANDO SENTÍS\nQUE ENTRENÁS MUCHO\nY NO AVANZÁS?',
    weight: 0.14,
    options: [
      { label: 'Me desespero y cambio todo',                       score: 0.1 },
      { label: 'Entreno más duro para salir de ahí',               score: 0.4 },
      { label: 'Espero que pase sola con el tiempo',               score: 0.3 },
      { label: 'Busco qué variable cambiar (volumen, recovery, nutrición)', score: 1.0 },
    ]
  },

  // ── CONSISTENCIA ──
  {
    dimension: 'CONSISTENCIA',
    text: '¿CUÁNTAS SEMANAS\nSEGUIDAS ENTRENASTE SIN\nROMPER EL PLAN?',
    weight: 0.14,
    options: [
      { label: 'Menos de 2 semanas',                               score: 0.1 },
      { label: '2 a 4 semanas',                                    score: 0.4 },
      { label: '1 a 3 meses',                                      score: 0.75 },
      { label: 'Más de 3 meses',                                   score: 1.0 },
    ]
  },
  {
    dimension: 'CONSISTENCIA',
    text: '¿ENTRENÁS CON\nOBJETIVOS MEDIBLES\nO POR SENSACIÓN?',
    weight: 0.14,
    options: [
      { label: 'Por sensación, lo que puedo ese día',               score: 0.2 },
      { label: 'Tengo una idea general pero no lo mido',            score: 0.5 },
      { label: 'Tengo objetivos pero sin seguimiento sistemático',  score: 0.75 },
      { label: 'Registro series, tiempos, cargas y evolución',      score: 1.0 },
    ]
  },

  // ── RENDIMIENTO ──
  {
    dimension: 'RENDIMIENTO',
    text: '¿CÓMO PERIODIZÁS\nTU CARGA DE ENTRENAMIENTO?',
    weight: 0.14,
    options: [
      { label: 'No lo hago, entreno lo mismo siempre',              score: 0.1 },
      { label: 'Subo la intensidad cuando me siento bien',          score: 0.4 },
      { label: 'Alterno semanas fuerte y liviana intuitivamente',   score: 0.7 },
      { label: 'Tengo ciclos planificados de carga y descarga',     score: 1.0 },
    ]
  },

  // ── RECUPERACIÓN ──
  {
    dimension: 'RECUPERACIÓN',
    text: '¿CUÁNTAS PRÁCTICAS\nDE RECOVERY APLICÁS\nDE FORMA REGULAR?',
    weight: 0.15,
    options: [
      { label: 'Ninguna de forma sistemática',                      score: 0.0 },
      { label: '1 práctica (stretching o sueño cuidado)',           score: 0.4 },
      { label: '2 prácticas (temperatura + nutrición o similar)',   score: 0.75 },
      { label: '3 o más (sueño + temperatura + nutrición + movilidad)', score: 1.0 },
    ]
  },
  {
    dimension: 'RECUPERACIÓN',
    text: '¿CÓMO LLEGÁS A UN\nMESO CICLO DE ALTA\nINTENSIDAD?',
    weight: 0.15,
    options: [
      { label: 'Agotado antes de que empiece',                      score: 0.0 },
      { label: 'Bien pero sé que el final se me va a hacer difícil', score: 0.4 },
      { label: 'Fresco y listo para rendir al tope',                score: 0.85 },
      { label: 'Fui aumentando la carga gradualmente y llego óptimo', score: 1.0 },
    ]
  },
];

// índices por dimensión (para las barras)
const DIM_MAP = {
  'MENTALIDAD':    [0, 1],
  'CONSISTENCIA':  [2, 3],
  'RENDIMIENTO':   [4],
  'RECUPERACIÓN':  [5, 6],
};
const DIM_ICONS = {
  'MENTALIDAD':    '🧠',
  'CONSISTENCIA':  '🔁',
  'RENDIMIENTO':   '⚡',
  'RECUPERACIÓN':  '🌙',
};

// ═══════════════════════════════════════
//  NIVELES
// ═══════════════════════════════════════
const SCORE_TIERS = [
  { min: 90, label: 'ELITE',
    color: '#C8A84B',
    desc: 'Operás al nivel de un atleta de alto rendimiento. Tus cuatro dimensiones están alineadas. El margen de mejora está en los detalles y en sostener el nivel en el tiempo.' },
  { min: 75, label: 'COMPETIDOR',
    color: '#4A8CFF',
    desc: 'Tenés la estructura y la mentalidad de un atleta serio. Hay una o dos dimensiones que, si las optimizás, te llevan al nivel Elite.' },
  { min: 58, label: 'EN DESARROLLO',
    color: '#34C759',
    desc: 'Estás construyendo los cimientos correctos. Tu potencial es alto pero tu techo actual está limitado por inconsistencias en uno o más pilares clave.' },
  { min: 38, label: 'AMATEUR CONSCIENTE',
    color: '#FF9500',
    desc: 'Tenés la motivación, pero te faltan sistemas. Sin estructura en entrenamiento y recuperación, el esfuerzo no se convierte en progreso real.' },
  { min:  0, label: 'PUNTO DE PARTIDA',
    color: '#FF3B30',
    desc: 'Todos los grandes atletas empezaron acá. La diferencia es que ahora sabés exactamente dónde estás parado. Eso ya es una ventaja.' },
];

// ═══════════════════════════════════════
//  ESTADO
// ═══════════════════════════════════════
let currentQ = 0;
let answers  = [];

// ═══════════════════════════════════════
//  FLUJO
// ═══════════════════════════════════════
function startQuiz() {
  currentQ = 0;
  answers  = [];
  showScreen('screen-quiz');
  renderQuestion();
}

function renderQuestion() {
  const q = QUESTIONS[currentQ];
  const pct = (currentQ / QUESTIONS.length) * 100;

  document.getElementById('progress-fill').style.width  = pct + '%';
  document.getElementById('q-counter').textContent      = `PREGUNTA ${currentQ + 1} DE ${QUESTIONS.length}`;
  document.getElementById('q-dimension').textContent    = q.dimension;
  document.getElementById('q-text').textContent         = q.text;

  const wrap = document.getElementById('options-wrap');
  wrap.innerHTML = '';
  const letters = ['A','B','C','D'];
  q.options.forEach((opt, i) => {
    const btn = document.createElement('button');
    btn.className = 'option-btn';
    btn.innerHTML = `<span class="option-letter">${letters[i]}</span>${opt.label}`;
    btn.onclick = () => selectOption(i, btn);
    wrap.appendChild(btn);
  });
}

function selectOption(index, btn) {
  document.querySelectorAll('.option-btn').forEach(b => b.classList.remove('selected'));
  btn.classList.add('selected');
  setTimeout(() => {
    answers.push({ score: QUESTIONS[currentQ].options[index].score, weight: QUESTIONS[currentQ].weight, dim: QUESTIONS[currentQ].dimension });
    currentQ++;
    if (currentQ < QUESTIONS.length) {
      renderQuestion();
    } else {
      document.getElementById('progress-fill').style.width = '100%';
      setTimeout(() => showScreen('screen-email'), 300);
    }
  }, 350);
}

// ═══════════════════════════════════════
//  RESULTADO
// ═══════════════════════════════════════
function showResult() {
  const weighted = answers.reduce((acc, a) => acc + a.score * a.weight, 0);
  const maxPossible = answers.reduce((acc, a) => acc + a.weight, 0);
  const score = Math.round((weighted / maxPossible) * 100);
  const tier  = SCORE_TIERS.find(t => score >= t.min);

  showScreen('screen-result');

  // anillo
  const circumference = 459;
  const offset = circumference - (score / 100) * circumference;
  setTimeout(() => {
    const ring = document.getElementById('ring-fill');
    ring.style.stroke          = tier.color;
    ring.style.strokeDashoffset = offset;
  }, 120);

  // número animado
  let current = 0;
  const el    = document.getElementById('score-digit');
  el.style.color = tier.color;
  const interval = setInterval(() => {
    current = Math.min(current + (score / 75), score);
    el.textContent = Math.round(current);
    if (current >= score) clearInterval(interval);
  }, 16);

  document.getElementById('score-label').textContent  = tier.label;
  document.getElementById('score-label').style.color  = tier.color;
  document.getElementById('score-desc').textContent   = tier.desc;

  // barras por dimensión
  const barsWrap = document.getElementById('dim-bars');
  barsWrap.innerHTML = '';
  Object.entries(DIM_MAP).forEach(([dim, indices]) => {
    const dimAnswers = indices.map(i => answers[i]).filter(Boolean);
    const dimScore   = dimAnswers.length
      ? Math.round(dimAnswers.reduce((a,b) => a + b.score, 0) / dimAnswers.length * 100)
      : 0;

    const row = document.createElement('div');
    row.className = 'dim-bar-row';
    row.innerHTML = `
      <div class="dim-bar-header">
        <span class="dim-bar-label">${DIM_ICONS[dim]} ${dim}</span>
        <span class="dim-bar-pct">${dimScore}</span>
      </div>
      <div class="dim-bar-track">
        <div class="dim-bar-fill" id="bar-${dim}"></div>
      </div>`;
    barsWrap.appendChild(row);

    setTimeout(() => {
      document.getElementById(`bar-${dim}`).style.width = dimScore + '%';
    }, 300);
  });
}

// ═══════════════════════════════════════
//  COMPARTIR
// ═══════════════════════════════════════
function shareScore() {
  const score = document.getElementById('score-digit').textContent;
  const tier  = document.getElementById('score-label').textContent;
  const url   = window.location.origin + window.location.pathname;
  const text  = `Mi WARLUS Athlete Score es ${score}/100 — nivel ${tier}.\n¿Podés superarme?\nNo gana el que más entrena, gana el que mejor se recupera. 🦭`;

  if (navigator.share) {
    navigator.share({ title: 'WARLUS Athlete Score', text, url }).catch(() => {});
  } else if (navigator.clipboard) {
    navigator.clipboard.writeText(`${text}\n${url}`).then(() => {
      alert('¡Copiado! Pegalo en tu story.');
    });
  } else {
    alert(`${text}\n${url}`);
  }
}

function restartQuiz() {
  currentQ = 0;
  answers  = [];
  showScreen('screen-intro');
}

function showScreen(id) {
  document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
  document.getElementById(id).classList.add('active');
  window.scrollTo(0, 0);
}

// ═══════════════════════════════════════
//  SUBMIT EMAIL → Google Sheets
// ═══════════════════════════════════════
const SHEETS_URL = 'https://script.google.com/macros/s/AKfycbx9lX-I3v523cr3aiKH4bJvnHMVzWQFwdNzDBfqsGxy8JYL4w9JbBQb6_jGL8nMdigA/exec';

function submitAndShow() {
  const nombre = document.getElementById('input-name').value.trim();
  const email  = document.getElementById('input-email').value.trim();

  if (!email) {
    const inp = document.getElementById('input-email');
    inp.style.borderColor = '#FF3B30';
    inp.placeholder = 'Ingresá tu email para continuar';
    return;
  }

  const weighted    = answers.reduce((acc, a) => acc + a.score * a.weight, 0);
  const maxPossible = answers.reduce((acc, a) => acc + a.weight, 0);
  const score       = Math.round((weighted / maxPossible) * 100);
  const tier        = SCORE_TIERS.find(t => score >= t.min);

  fetch(SHEETS_URL, {
    method: 'POST',
    mode:   'no-cors',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ nombre, email, score, nivel: tier.label, test: 'athlete-score' })
  }).catch(() => {});

  showResult();
}
</script>
</body>
</html>
