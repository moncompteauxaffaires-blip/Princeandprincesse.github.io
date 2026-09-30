Le Prince et la Princesse - La Quete de Solaria




Télécharger
https://es-d-89840578520261002-01a0f121-4fcc-7e56-ad74-23473c52f39d.codepen.dev/

<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Le Prince et la Princesse</title>
  <style>
    body {
      background-color: #1a1a2e;
      color: #e0e0e0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      margin: 0;
    }
    .game-card {
      background: #16213e;
      padding: 2rem;
      border-radius: 12px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.5);
      max-width: 600px;
      width: 90%;
    }
    h1 {
      color: #f1c40f;
      text-align: center;
      margin-top: 0;
    }
    .story-text {
      font-size: 1.1rem;
      line-height: 1.6;
      margin-bottom: 1.5rem;
    }
    .choices {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
    button {
      background-color: #0f3460;
      color: #fff;
      border: 2px solid #e94560;
      padding: 12px 20px;
      border-radius: 8px;
      font-size: 1rem;
      cursor: pointer;
      transition: all 0.3s ease;
    }
    button:hover {
      background-color: #e94560;
    }
  </style>
</head>
<body>

<div class="game-card">
  <h1 id="title">Solaria</h1>
  <p id="story" class="story-text">Chargement de l'aventure...</p>
  <div id="choices" class="choices"></div>
</div>

<script>
  const storyData = {
    start: {
      text: "Le royaume de Solaria est plongé dans la nuit. Le Prince Élios et la Princesse Auria arrivent devant le Pont des Murmures, gardé par un Golem de Pierre aux yeux rouges. Que faites-vous ?",
      choices: [
        { text: "Élios attaque pendant qu'Auria gelé la créature (Combat)", nextStep: "combat" },
        { text: "Auria parle au Golem tandis qu'Élios cherche un mécanisme (Diplomatie)", nextStep: "diplomacy" }
      ]
    },
    combat: {
      text: "Élios attire l'attention du Golem. Auria lance son sort d'immobilisation juste à temps ! Les articulations du monstre gèlent. Vous traversez le pont sans encombre et atteignez la caverne de l'artefact.",
      choices: [
        { text: "Entrer directement dans la caverne", nextStep: "win" }
      ]
    },
    diplomacy: {
      text: "Auria entonne un chant ancien. Le Golem s'adoucit. Élios trouve un levier caché sous l'autel et désactive le gardien. Le passage est libre !",
      choices: [
        { text: "Entrer dans la caverne pour prendre la Larme de Soleil", nextStep: "win" }
      ]
    },
    win: {
      text: "Vous récupérez la Larme de Soleil ! La lumière revient sur le royaume de Solaria. Le Prince et la Princesse célèbrent la victoire.",
      choices: [
        { text: "Recommencer la partie", nextStep: "start" }
      ]
    }
  };

  function renderStep(stepKey) {
    const step = storyData[stepKey];
    document.getElementById('story').innerText = step.text;
    
    const choicesDiv = document.getElementById('choices');
    choicesDiv.innerHTML = '';

    step.choices.forEach(choice => {
      const btn = document.createElement('button');
      btn.innerText = choice.text;
      btn.onclick = () => renderStep(choice.nextStep);
      choicesDiv.appendChild(btn);
    });
  }

  // Lancement du jeu au chargement
  renderStep('start');
</script>

</body>
</html>
