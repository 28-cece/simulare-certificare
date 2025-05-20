<!DOCTYPE html>
<html lang="ro">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Simulare Certificare</title>
    <style>
      body { font-family: Arial, sans-serif; padding: 20px; background: #f0f4fa; }
      .card { background: white; border-radius: 10px; padding: 20px; box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1); max-width: 600px; margin: auto; }
      .question { font-size: 18px; font-weight: bold; }
      .options { margin-top: 15px; }
      .option-button { display: block; width: 100%; margin-bottom: 10px; padding: 10px; border: none; border-radius: 5px; cursor: pointer; text-align: left; }
      .option-button.correct { background-color: #d4edda; }
      .option-button.wrong { background-color: #f8d7da; }
      .option-button.neutral { background-color: #e2e6ea; }
      .next-button { margin-top: 20px; padding: 10px 20px; border: none; background-color: #007bff; color: white; border-radius: 5px; cursor: pointer; }
      .center { text-align: center; }
    </style>
  </head>
  <body>
    <div id="app"></div>

    <script>
      const questions = [
        {
          question: "Data alegerilor pentru funcția de Președinte al Republicii Moldova se stabilește prin:",
          options: [
            "Hotărârea Comisiei Electorale Centrale",
            "Hotărârea Curții Constituționale",
            "Hotărârea Parlamentului"
          ],
          correctIndex: 2
        },
        {
          question: "Durata mandatului Președintelui Republicii Moldova este:",
          options: ["4 ani", "5 ani", "6 ani"],
          correctIndex: 1
        },
        {
          question: "Alegerile locale generale se desfășoară o dată la:",
          options: ["2 ani", "3 ani", "4 ani"],
          correctIndex: 2
        },
        {
          question: "Ce autoritate organizează alegerile în Republica Moldova?",
          options: ["Guvernul", "Curtea Constituțională", "Comisia Electorală Centrală"],
          correctIndex: 2
        },
        {
          question: "Care este pragul electoral pentru partide în alegerile parlamentare?",
          options: ["4%", "5%", "6%"],
          correctIndex: 1
        }
      ];

      let current = 0;
      let score = 0;
      let selected = null;

      function render() {
        const app = document.getElementById("app");
        app.innerHTML = "";

        if (current >= questions.length) {
          app.innerHTML = `<div class='card center'><h2>Test finalizat</h2><p>Ai răspuns corect la ${score} din ${questions.length} întrebări.</p></div>`;
          return;
        }

        const question = questions[current];

        const card = document.createElement("div");
        card.className = "card";

        const qText = document.createElement("div");
        qText.className = "question";
        qText.innerText = question.question;
        card.appendChild(qText);

        const optionsDiv = document.createElement("div");
        optionsDiv.className = "options";

        question.options.forEach((opt, index) => {
          const button = document.createElement("button");
          button.className = "option-button";
          if (selected === null) button.classList.add("neutral");
          button.innerText = opt;
          button.disabled = selected !== null;
          if (selected !== null) {
            if (index === question.correctIndex) button.classList.add("correct");
            else if (index === selected) button.classList.add("wrong");
            else button.classList.add("neutral");
          }
          button.onclick = () => {
            selected = index;
            if (index === question.correctIndex) score++;
            render();
          };
          optionsDiv.appendChild(button);
        });

        card.appendChild(optionsDiv);

        if (selected !== null) {
          const nextBtn = document.createElement("button");
          nextBtn.className = "next-button";
          nextBtn.innerText = "Următoarea întrebare";
          nextBtn.onclick = () => {
            current++;
            selected = null;
            render();
          };
          card.appendChild(nextBtn);
        }

        app.appendChild(card);
      }

      render();
    </script>
  </body>
</html>
