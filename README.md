# westernstudies[ag_revolution_adventure (2).html](https://github.com/user-attachments/files/26511013/ag_revolution_adventure.2.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Agricultural Revolution — Choose Your Own Adventure</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;700&family=Source+Serif+4:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --parchment: #f7f0e3;
    --parchment-dark: #ede3cc;
    --ink: #1a1208;
    --ink-muted: #5a4e38;
    --ink-faint: #8a7d66;
    --green: #2d6a4f;
    --green-light: #d8f3dc;
    --green-border: #74c69d;
    --red: #6b1a1a;
    --red-light: #fde8e8;
    --red-border: #e57373;
    --gold: #b5830a;
    --gold-light: #fef3c7;
    --border: #c9b99a;
    --shadow: rgba(26,18,8,0.10);
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--parchment);
    font-family: 'Source Serif 4', Georgia, serif;
    color: var(--ink);
    min-height: 100vh;
    background-image:
      radial-gradient(ellipse at 20% 10%, rgba(181,131,10,0.07) 0%, transparent 60%),
      radial-gradient(ellipse at 80% 90%, rgba(45,106,79,0.06) 0%, transparent 60%);
  }

  .header {
    text-align: center;
    padding: 2.5rem 1.5rem 1.5rem;
    border-bottom: 1px solid var(--border);
    background: rgba(255,255,255,0.35);
  }

  .header-eyebrow {
    font-family: 'Source Serif 4', serif;
    font-size: 11px;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 0.6rem;
    font-weight: 500;
  }

  .header h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(22px, 5vw, 38px);
    font-weight: 700;
    color: var(--ink);
    line-height: 1.2;
    margin-bottom: 0.5rem;
  }

  .header-sub {
    font-size: 14px;
    color: var(--ink-muted);
    font-style: italic;
    line-height: 1.6;
  }

  #game {
    max-width: 680px;
    margin: 0 auto;
    padding: 2rem 1.25rem 4rem;
  }

  .progress-section {
    margin-bottom: 1.5rem;
  }

  .progress-meta {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 6px;
  }

  .progress-label {
    font-size: 12px;
    color: var(--ink-faint);
    letter-spacing: 0.05em;
  }

  .score-tag {
    font-size: 13px;
    color: var(--gold);
    font-weight: 500;
    background: var(--gold-light);
    border: 1px solid #e9c96e;
    border-radius: 20px;
    padding: 2px 12px;
  }

  .progress-track {
    height: 6px;
    background: var(--parchment-dark);
    border-radius: 99px;
    overflow: hidden;
    border: 1px solid var(--border);
  }

  .progress-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--green) 0%, #52b788 100%);
    border-radius: 99px;
    transition: width 0.5s ease;
  }

  .scene-card {
    background: rgba(255,255,255,0.6);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 1.75rem;
    box-shadow: 0 2px 12px var(--shadow);
    animation: fadeUp 0.3s ease both;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(10px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .scene-eyebrow {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 1rem;
  }

  .scene-year {
    font-size: 11px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--ink-faint);
    font-weight: 500;
  }

  .scene-dot {
    width: 4px; height: 4px;
    border-radius: 50%;
    background: var(--border);
    flex-shrink: 0;
  }

  .scene-chapter {
    font-size: 11px;
    color: var(--gold);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    font-weight: 500;
  }

  .scene-icon {
    font-size: 32px;
    display: block;
    margin-bottom: 0.75rem;
    line-height: 1;
  }

  .scene-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(18px, 4vw, 26px);
    font-weight: 700;
    color: var(--ink);
    line-height: 1.25;
    margin-bottom: 1rem;
  }

  .scene-body {
    font-size: 15px;
    line-height: 1.8;
    color: var(--ink);
    margin-bottom: 1.25rem;
  }

  .fact-box {
    background: var(--gold-light);
    border-left: 3px solid var(--gold);
    border-radius: 0;
    padding: 0.85rem 1rem;
    margin: 0 0 1.5rem;
    font-size: 13px;
    color: var(--ink-muted);
    line-height: 1.7;
  }

  .fact-box strong { color: var(--ink); font-weight: 500; }
  .fact-label {
    font-size: 10px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--gold);
    font-weight: 500;
    margin-bottom: 4px;
  }

  .choices-label {
    font-size: 11px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--ink-faint);
    margin-bottom: 0.75rem;
    font-weight: 500;
  }

  .choices { display: flex; flex-direction: column; gap: 10px; }

  .choice-btn {
    background: rgba(255,255,255,0.8);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 1rem 1.1rem;
    text-align: left;
    cursor: pointer;
    font-size: 15px;
    font-family: 'Source Serif 4', serif;
    color: var(--ink);
    line-height: 1.55;
    transition: background 0.15s, border-color 0.15s, transform 0.1s;
    display: flex;
    align-items: flex-start;
    gap: 10px;
  }

  .choice-btn:hover {
    background: white;
    border-color: var(--ink-muted);
    transform: translateY(-1px);
    box-shadow: 0 3px 10px var(--shadow);
  }

  .choice-btn:active { transform: translateY(0); }

  .choice-letter {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 26px;
    height: 26px;
    min-width: 26px;
    border-radius: 50%;
    background: var(--parchment-dark);
    border: 1px solid var(--border);
    font-size: 12px;
    font-weight: 500;
    color: var(--ink-muted);
    font-family: 'Playfair Display', serif;
    margin-top: 1px;
  }

  .outcome-wrong {
    background: var(--red-light);
    border: 1px solid var(--red-border);
    border-radius: 8px;
    padding: 1rem 1.1rem;
    margin-bottom: 1.25rem;
    font-size: 14px;
    color: var(--red);
    line-height: 1.7;
  }

  .outcome-wrong strong { font-weight: 500; }

  .divider {
    border: none;
    border-top: 1px solid var(--border);
    margin: 1.25rem 0;
  }

  .retry-btn {
    background: var(--ink);
    color: var(--parchment);
    border: none;
    border-radius: 8px;
    padding: 0.75rem 1.5rem;
    font-size: 14px;
    font-family: 'Source Serif 4', serif;
    cursor: pointer;
    transition: opacity 0.15s;
  }

  .retry-btn:hover { opacity: 0.85; }

  .win-card {
    background: var(--green-light);
    border: 1px solid var(--green-border);
    border-radius: 12px;
    padding: 2rem 1.75rem;
    text-align: center;
    animation: fadeUp 0.4s ease both;
  }

  .win-badge {
    display: inline-block;
    background: var(--green);
    color: #d8f3dc;
    font-size: 11px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    padding: 4px 16px;
    border-radius: 20px;
    margin-bottom: 1rem;
    font-weight: 500;
  }

  .win-score {
    font-family: 'Playfair Display', serif;
    font-size: 54px;
    font-weight: 700;
    color: var(--green);
    line-height: 1;
    margin-bottom: 0.25rem;
  }

  .win-score-label {
    font-size: 12px;
    color: var(--green);
    opacity: 0.7;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 1.25rem;
  }

  .win-title {
    font-family: 'Playfair Display', serif;
    font-size: 22px;
    font-weight: 700;
    color: var(--ink);
    margin-bottom: 0.75rem;
  }

  .win-body {
    font-size: 14px;
    color: var(--ink-muted);
    line-height: 1.75;
    margin-bottom: 1.25rem;
  }

  .chain-box {
    background: rgba(255,255,255,0.6);
    border: 1px solid var(--green-border);
    border-radius: 8px;
    padding: 1rem;
    font-size: 13px;
    color: var(--green);
    line-height: 1.8;
    text-align: left;
    margin-bottom: 1.25rem;
  }

  .chain-box strong { color: var(--ink); font-weight: 500; display: block; margin-bottom: 4px; }

  .restart-btn {
    background: var(--ink);
    color: var(--parchment);
    border: none;
    border-radius: 8px;
    padding: 0.75rem 1.75rem;
    font-size: 14px;
    font-family: 'Source Serif 4', serif;
    cursor: pointer;
    transition: opacity 0.15s;
  }

  .restart-btn:hover { opacity: 0.82; }

  .mistake-note {
    font-size: 12px;
    color: var(--ink-faint);
    margin-top: 0.75rem;
    font-style: italic;
  }

  @media (max-width: 480px) {
    .header { padding: 1.75rem 1rem 1.25rem; }
    .scene-card { padding: 1.25rem; }
    #game { padding: 1.25rem 0.9rem 3rem; }
  }
</style>
</head>
<body>

<div class="header">
  <div class="header-eyebrow">Western Studies — Interactive History</div>
  <h1>The Agricultural Revolution</h1>
  <p class="header-sub">England, 1700. Can you guide your village into the modern world?</p>
</div>

<div id="game"></div>

<script>
const SCENES = [
  {
    id: "intro",
    label: "England, 1700",
    chapter: "The beginning",
    icon: "🌾",
    title: "Your village is struggling",
    body: "You are a landowner in rural England. Most of your neighbors farm small plots using the same methods as their grandparents — scattering seeds by hand, letting animals roam fields freely, and praying for good weather. Food is scarce, people are dying young, and your village rarely produces more than it needs to survive.\n\nA traveling merchant stops at your gate with news of 'new farming methods' spreading across the countryside. What do you do?",
    fact: "<strong>Historical context:</strong> In 1700, roughly 80% of people in England worked in agriculture. Most used open-field farming — inefficient strips of land shared among villagers with no crop rotation.",
    choices: [
      { text: "Listen to the merchant and learn about the new techniques", next: "enclosure", correct: true },
      { text: "Send him away — your grandfather's methods worked fine", next: "fail_tradition", correct: false }
    ]
  },
  {
    id: "enclosure",
    label: "The Land Question",
    chapter: "Decision 1 of 5",
    icon: "🔲",
    title: "Enclosure: fencing the commons",
    body: "The merchant tells you about the Enclosure Acts — wealthy landowners are fencing off shared 'common' land into large private farms. This is controversial. Poor farmers lose their land, but larger enclosed farms can be managed more efficiently.\n\nParliament has passed laws supporting enclosure. You have the money to buy up neighboring land. What do you choose?",
    fact: "<strong>Enclosure Acts (1700s–1800s):</strong> Over 5,000 acts enclosed roughly 6.8 million acres. Small farmers were displaced — but larger farms became far more productive and could feed growing cities.",
    choices: [
      { text: "Enclose the land and create a larger, managed farm", next: "crop_rotation", correct: true },
      { text: "Keep the common land shared — it feels more fair", next: "fail_commons", correct: false }
    ]
  },
  {
    id: "crop_rotation",
    label: "Soil & Science",
    chapter: "Decision 2 of 5",
    icon: "🔄",
    title: "The four-field rotation",
    body: "With your larger farm, you meet Charles Townshend — nicknamed 'Turnip Townshend' — who swears by a new system: rotating four crops across your fields each year (wheat, turnips, barley, and clover). Each plant restores something different to the soil. No more leaving fields empty for a year.\n\nYour neighbors think it sounds ridiculous. What do you do?",
    fact: "<strong>Four-field crop rotation:</strong> Introduced from the Netherlands, this method eliminated 'fallow' years, doubling or tripling yields on the same land. Turnips fed livestock through winter — keeping animals alive year-round for the first time.",
    choices: [
      { text: "Adopt the four-field rotation across your farm", next: "selective_breeding", correct: true },
      { text: "Stick to the two-field system your family has always used", next: "fail_rotation", correct: false }
    ]
  },
  {
    id: "selective_breeding",
    label: "Better Animals",
    chapter: "Decision 3 of 5",
    icon: "🐑",
    title: "Selective breeding",
    body: "Robert Bakewell, a famous English farmer, visits your county. He explains that by carefully choosing which animals breed — selecting only the biggest, healthiest sheep and cattle — each generation becomes larger and meatier.\n\nYour farm now has year-round fodder thanks to turnips. You can keep larger herds alive through winter. Do you try Bakewell's methods?",
    fact: "<strong>Robert Bakewell (1725–1795):</strong> His Leicester sheep tripled in size over decades of selective breeding. Average livestock weight at London markets roughly doubled between 1700 and 1800.",
    choices: [
      { text: "Yes — selectively breed only your best animals", next: "seed_drill", correct: true },
      { text: "No — let nature decide which animals reproduce", next: "fail_breeding", correct: false }
    ]
  },
  {
    id: "seed_drill",
    label: "New Machines",
    chapter: "Decision 4 of 5",
    icon: "⚙️",
    title: "Jethro Tull's seed drill",
    body: "It is now 1731. An inventor named Jethro Tull has created a mechanical seed drill — a horse-drawn machine that plants seeds in neat rows at a consistent depth. Before this, farmers scattered seeds by hand. Most seeds were eaten by birds or planted too shallow. The drill wastes almost nothing.\n\nIt costs money you barely have. Do you invest?",
    fact: "<strong>The seed drill (1701):</strong> Tull's invention increased germination rates dramatically. Seeds planted in rows could also be weeded with a horse-drawn hoe — one person could now do the work of many.",
    choices: [
      { text: "Buy the seed drill — it's an investment in efficiency", next: "population_boom", correct: true },
      { text: "The cost is too high — hand-sowing works well enough", next: "fail_drill", correct: false }
    ]
  },
  {
    id: "population_boom",
    label: "Unintended Consequences",
    chapter: "Decision 5 of 5",
    icon: "📈",
    title: "Something unexpected happens",
    body: "Within a generation, your farm produces twice the food on the same land with a fraction of the workers. The same is happening across England. More food means fewer famines — infant mortality drops, people live longer, and families grow larger.\n\nEngland's population explodes from 5 million in 1700 to over 9 million by 1800. But now there's a crisis: thousands of farmworkers no longer have jobs. They are flooding into towns. What should be done with this new landless workforce?",
    fact: "<strong>Population boom:</strong> England's population roughly doubled between 1750 and 1850. Agricultural efficiency created a massive surplus of cheap labor — workers who needed wages, who needed goods, and who were now living in cities.",
    choices: [
      { text: "These workers should move to towns and find work in new industries", next: "win", correct: true },
      { text: "Pass laws forcing displaced workers to return to farming", next: "fail_workers", correct: false }
    ]
  },
  {
    id: "fail_tradition",
    type: "fail",
    label: "Dead end",
    title: "Your village falls behind",
    body: "While neighboring villages modernize, yours continues to produce barely enough to feed itself. During a hard winter, famine strikes. Without surplus food, no population growth happens — and without a population boom, there are no extra workers to power the factories beginning to appear in cities. History leaves your village behind.",
    hint: "The Agricultural Revolution required openness to new methods. Traditional farming couldn't produce the food surplus or labor surplus needed to fuel industrialization.",
    retry: "intro"
  },
  {
    id: "fail_commons",
    type: "fail",
    label: "Dead end",
    title: "Shared land, shared poverty",
    body: "Common land continues to be divided among dozens of small farmers. Without the scale of larger enclosed farms, no single farmer can afford new equipment or apply new techniques systematically. Yields remain low. The surplus food that England needs to feed its growing cities never materializes.",
    hint: "Enclosure was economically painful for the poor — but it created the large, efficient farms that made agricultural innovation possible at scale.",
    retry: "enclosure"
  },
  {
    id: "fail_rotation",
    type: "fail",
    label: "Dead end",
    title: "Your soil exhausts itself",
    body: "Without crop rotation, your fields must lay fallow every other year to recover. Your yields plateau. You cannot produce enough surplus to hire more workers or buy new equipment. Meanwhile, farms using the four-field system dramatically outproduce yours.",
    hint: "Crop rotation was the foundation of the Agricultural Revolution — it unlocked year-round productivity and year-round livestock feeding.",
    retry: "crop_rotation"
  },
  {
    id: "fail_breeding",
    type: "fail",
    label: "Dead end",
    title: "Small animals, small returns",
    body: "Your livestock remains the same scraggly size as your grandfather's. You cannot produce the meat surplus that cities need. Without improved livestock, much of your turnip crop goes to waste — you grew it for winter feed, but have too few animals to consume it.",
    hint: "Selective breeding multiplied the food output per animal. Combined with year-round fodder from crop rotation, it was a force multiplier for food production.",
    retry: "selective_breeding"
  },
  {
    id: "fail_drill",
    type: "fail",
    label: "Dead end",
    title: "Seeds lost, yields low",
    body: "Your hand-sown fields continue to lose a huge percentage of seeds to birds and poor planting depth. Your neighbors with seed drills are producing significantly more on less land. You fall behind economically and cannot fund further improvements.",
    hint: "Mechanization — starting with tools like the seed drill — was how farming multiplied its output without multiplying its workforce.",
    retry: "seed_drill"
  },
  {
    id: "fail_workers",
    type: "fail",
    label: "Dead end",
    title: "The labor surplus has nowhere to go",
    body: "Forcing displaced workers back to farms that no longer need them creates poverty and unrest without solving anything. The workers who should have become England's factory workforce instead riot in the countryside. The Industrial Revolution stalls before it begins.",
    hint: "The displaced agricultural workers were not a problem — they were the Industrial Revolution's fuel. They became the factory workforce, the consumers, and the urban population that powered industrialization.",
    retry: "population_boom"
  }
];

const sceneMap = {};
SCENES.forEach(s => sceneMap[s.id] = s);

let score = 0;
let mistakes = 0;
let totalCorrect = 0;
const TOTAL = 5;

function render(id) {
  const scene = sceneMap[id];
  const game = document.getElementById('game');
  window.scrollTo({ top: 0, behavior: 'smooth' });

  if (id === 'win') {
    game.innerHTML = `
      <div class="win-card">
        <div class="win-badge">Mission complete</div>
        <div class="win-score">${score}</div>
        <div class="win-score-label">points</div>
        <div class="win-title">England is ready for the Industrial Revolution</div>
        <p class="win-body">By adopting enclosure, crop rotation, selective breeding, and mechanical tools, you created a food surplus and a population boom — and unleashed a landless workforce ready to power the factories of the Industrial Revolution.</p>
        <div class="chain-box">
          <strong>The cause-and-effect chain you triggered:</strong>
          Enclosure → large farms → crop rotation → food surplus → selective breeding → more food → seed drill → fewer workers needed → population boom → displaced workers flood cities → cheap urban labor → Industrial Revolution begins
        </div>
        ${mistakes > 0
          ? `<p class="mistake-note">You made ${mistakes} wrong turn${mistakes > 1 ? 's' : ''} along the way. Try again for a perfect score.</p>`
          : `<p class="mistake-note" style="color: var(--green); font-style: normal; font-weight: 500;">Perfect run — no wrong turns!</p>`}
        <br>
        <button class="restart-btn" onclick="restartGame()">Play again</button>
      </div>`;
    return;
  }

  if (scene.type === 'fail') {
    const pct = Math.round((totalCorrect / TOTAL) * 100);
    game.innerHTML = `
      <div class="progress-section">
        <div class="progress-meta">
          <span class="progress-label">Progress — ${totalCorrect} of ${TOTAL} decisions</span>
          <span class="score-tag">${score} pts</span>
        </div>
        <div class="progress-track"><div class="progress-fill" style="width:${pct}%"></div></div>
      </div>
      <div class="scene-card">
        <div class="scene-eyebrow">
          <span class="scene-year">${scene.label}</span>
        </div>
        <div class="scene-title">${scene.title}</div>
        <div class="scene-body">${scene.body.replace(/\n/g,'<br><br>')}</div>
        <div class="outcome-wrong">
          <strong>What went wrong:</strong> ${scene.hint}
        </div>
        <button class="retry-btn" onclick="render('${scene.retry}')">Try that decision again &rarr;</button>
      </div>`;
    return;
  }

  const pct = Math.round((totalCorrect / TOTAL) * 100);
  const letters = ['A','B','C'];
  const choicesHtml = scene.choices.map((c, i) =>
    `<button class="choice-btn" onclick="choose(${i},'${scene.id}')">
      <span class="choice-letter">${letters[i]}</span>
      <span>${c.text}</span>
    </button>`
  ).join('');

  game.innerHTML = `
    <div class="progress-section">
      <div class="progress-meta">
        <span class="progress-label">Progress — ${totalCorrect} of ${TOTAL} decisions</span>
        <span class="score-tag">${score} pts</span>
      </div>
      <div class="progress-track"><div class="progress-fill" style="width:${pct}%"></div></div>
    </div>
    <div class="scene-card">
      <div class="scene-eyebrow">
        <span class="scene-year">${scene.label}</span>
        <span class="scene-dot"></span>
        <span class="scene-chapter">${scene.chapter}</span>
      </div>
      ${scene.icon ? `<span class="scene-icon">${scene.icon}</span>` : ''}
      <div class="scene-title">${scene.title}</div>
      <div class="scene-body">${scene.body.replace(/\n\n/g,'</p><p style="margin-top:1em">').replace(/^/,'<p>').replace(/$/,'</p>')}</div>
      ${scene.fact ? `<div class="fact-box"><div class="fact-label">Historical record</div>${scene.fact}</div>` : ''}
      <div class="choices-label">Your decision:</div>
      <div class="choices">${choicesHtml}</div>
    </div>`;
}

function choose(idx, sceneId) {
  const choice = sceneMap[sceneId].choices[idx];
  if (choice.correct) {
    score += 100;
    totalCorrect++;
  } else {
    mistakes++;
    score = Math.max(0, score - 25);
  }
  render(choice.next);
}

function restartGame() {
  score = 0; mistakes = 0; totalCorrect = 0;
  render('intro');
}

render('intro');
</script>
</body>
</html>
