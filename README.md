# approject
dassdasdasd
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AP Maths Quiz - Class 10</title>
    <style>
        :root {
            --color-bg-primary: #0f172a;
            --color-bg-secondary: #1e293b;
            --color-text-primary: #f1f5f9;
            --color-text-secondary: #cbd5e1;
            --color-accent: #38bdf8;
            --color-success: #10b981;
            --color-error: #ef4444;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            background-color: var(--color-bg-primary);
            color: var(--color-text-primary);
            padding: 20px;
            min-height: 100vh;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            background-color: var(--color-bg-secondary);
            padding: 40px;
            border-radius: 12px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
        }

        .header {
            text-align: center;
            margin-bottom: 30px;
        }

        .header h1 {
            color: var(--color-accent);
            font-size: 28px;
            margin-bottom: 10px;
        }

        .progress-bar {
            width: 100%;
            height: 8px;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 4px;
            margin-top: 20px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background-color: var(--color-accent);
            width: 0%;
            transition: width 0.3s ease;
        }

        .question-container {
            display: none;
        }

        .question-container.active {
            display: block;
            animation: fadeIn 0.3s ease;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }

        .question-num {
            color: var(--color-text-secondary);
            font-size: 14px;
            margin-bottom: 15px;
        }

        .question-text {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 25px;
            line-height: 1.4;
        }

        .options {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .option {
            padding: 15px 20px;
            background-color: var(--color-bg-primary);
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s ease;
            color: var(--color-text-secondary);
            font-size: 16px;
        }

        .option:hover {
            border-color: var(--color-accent);
            background-color: rgba(56, 189, 248, 0.05);
        }

        .option.selected {
            border-color: var(--color-accent);
            background-color: rgba(56, 189, 248, 0.1);
            color: var(--color-text-primary);
        }

        .option.correct {
            border-color: var(--color-success);
            background-color: rgba(16, 185, 129, 0.1);
            color: var(--color-success);
        }

        .option.incorrect {
            border-color: var(--color-error);
            background-color: rgba(239, 68, 68, 0.1);
            color: var(--color-error);
        }

        .feedback {
            margin-top: 20px;
            padding: 15px;
            border-radius: 8px;
            display: none;
        }

        .feedback.show {
            display: block;
        }

        .feedback-correct {
            background-color: rgba(16, 185, 129, 0.1);
            border: 1px solid var(--color-success);
            color: var(--color-success);
        }

        .feedback-incorrect {
            background-color: rgba(239, 68, 68, 0.1);
            border: 1px solid var(--color-error);
            color: var(--color-error);
        }

        .feedback-text {
            margin-bottom: 10px;
            font-weight: 600;
        }

        .explanation {
            font-size: 14px;
            margin-top: 10px;
            opacity: 0.9;
        }

        .buttons {
            display: flex;
            gap: 12px;
            margin-top: 30px;
            justify-content: center;
        }

        button {
            padding: 12px 30px;
            font-size: 16px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.2s ease;
        }

        .btn-next {
            background-color: var(--color-accent);
            color: var(--color-bg-primary);
            display: none;
        }

        .btn-next.show {
            display: inline-block;
        }

        .btn-next:hover {
            background-color: #0ea5e9;
        }

        .btn-prev {
            background-color: rgba(255, 255, 255, 0.1);
            color: var(--color-text-primary);
        }

        .btn-prev:hover {
            background-color: rgba(255, 255, 255, 0.2);
        }

        .results {
            display: none;
            text-align: center;
        }

        .results.show {
            display: block;
        }

        .score-circle {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            background: conic-gradient(var(--color-accent) 0deg, var(--color-accent) var(--score-angle), rgba(255, 255, 255, 0.1) var(--score-angle));
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 30px auto;
            font-size: 36px;
            font-weight: 700;
            color: var(--color-accent);
        }

        .score-text {
            font-size: 24px;
            margin: 20px 0;
            color: var(--color-accent);
        }

        .results-details {
            margin-top: 30px;
            text-align: left;
            background-color: var(--color-bg-primary);
            padding: 20px;
            border-radius: 8px;
            max-height: 300px;
            overflow-y: auto;
        }

        .result-item {
            padding: 12px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            font-size: 14px;
        }

        .result-item:last-child {
            border-bottom: none;
        }

        .result-item.correct-result {
            color: var(--color-success);
        }

        .result-item.incorrect-result {
            color: var(--color-error);
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>📊 AP Maths Quiz</h1>
            <p style="color: var(--color-text-secondary); margin-bottom: 15px;">Class 10 - Arithmetic Progressions</p>
            <div class="progress-bar">
                <div class="progress-fill"></div>
            </div>
        </div>

        <div id="quizContainer">
            <!-- Questions will be generated here -->
        </div>

        <div class="buttons">
            <button class="btn-prev" onclick="previousQuestion()">← Previous</button>
            <button class="btn-next" onclick="nextQuestion()">Next →</button>
            <button class="btn-next" id="finishBtn" onclick="finishQuiz()" style="display: none; background-color: #10b981;">Finish Quiz</button>
        </div>

        <div class="results" id="results">
            <h2 style="font-size: 24px; margin-bottom: 20px;">Quiz Completed! 🎉</h2>
            <div class="score-circle" id="scoreCircle">0/20</div>
            <div class="score-text" id="scoreText">Score: 0%</div>
            <button onclick="restartQuiz()" style="background-color: var(--color-accent); color: var(--color-bg-primary); margin-top: 20px;">Restart Quiz</button>
            <div class="results-details" id="resultDetails"></div>
        </div>
    </div>

    <script>
        const quizData = [
            {
                question: "1. Is 2, 4, 6, 8, 10, ... an AP? If yes, find d.",
                options: ["No", "Yes, d = 2", "Yes, d = 4", "Yes, d = 1"],
                correct: 1,
                explanation: "This is an AP with common difference d = 4 - 2 = 2."
            },
            {
                question: "2. Find the 10th term of AP: 3, 7, 11, 15, ...",
                options: ["35", "39", "43", "47"],
                correct: 1,
                explanation: "Using a_n = a + (n-1)d: a₁₀ = 3 + (10-1)×4 = 3 + 36 = 39"
            },
            {
                question: "3. What is the common difference in AP: 10, 5, 0, -5, ...?",
                options: ["5", "-5", "10", "15"],
                correct: 1,
                explanation: "d = 5 - 10 = -5. The difference is negative, so AP is decreasing."
            },
            {
                question: "4. Find the sum of first 5 terms of AP: 1, 3, 5, 7, ...",
                options: ["15", "20", "25", "30"],
                correct: 2,
                explanation: "S₅ = (5/2)[2(1) + (5-1)×2] = 2.5 × 10 = 25"
            },
            {
                question: "5. Which term of AP 5, 10, 15, 20, ... is 100?",
                options: ["15th", "18th", "20th", "22nd"],
                correct: 2,
                explanation: "100 = 5 + (n-1)×5 → 95 = (n-1)×5 → n = 20"
            },
            {
                question: "6. Salary increases by ₹1000 each year starting from ₹20,000. What is the 3rd year salary?",
                options: ["₹20,000", "₹21,000", "₹22,000", "₹23,000"],
                correct: 2,
                explanation: "a₃ = 20,000 + (3-1)×1,000 = 20,000 + 2,000 = ₹22,000"
            },
            {
                question: "7. Find the sum of AP: 2, 5, 8, 11, 14",
                options: ["30", "40", "50", "60"],
                correct: 1,
                explanation: "S₅ = (5/2)(first + last) = (5/2)(2 + 14) = (5/2)×16 = 40"
            },
            {
                question: "8. Is 1, 2, 4, 8, 16, ... an AP?",
                options: ["Yes", "No", "Maybe", "Can't determine"],
                correct: 1,
                explanation: "No, differences are: 1, 2, 4, 8 (not constant). This is a Geometric Progression (GP), not AP."
            },
            {
                question: "9. In AP: 20, 15, 10, 5, 0, -5, ... what is the 8th term?",
                options: ["-10", "-15", "-20", "-25"],
                correct: 1,
                explanation: "a₈ = 20 + (8-1)×(-5) = 20 - 35 = -15"
            },
            {
                question: "10. Find 'd' for AP where a = 5 and a₄ = 17",
                options: ["2", "3", "4", "5"],
                correct: 2,
                explanation: "a₄ = a + 3d → 17 = 5 + 3d → 12 = 3d → d = 4"
            },
            {
                question: "11. How many terms of AP 3, 6, 9, ... sum to 123?",
                options: ["7", "8", "9", "10"],
                correct: 2,
                explanation: "S_n = (n/2)[2(3) + (n-1)×3] = 123 → n = 9"
            },
            {
                question: "12. What is the 20th term of AP: -5, -2, 1, 4, ...?",
                options: ["52", "55", "58", "61"],
                correct: 0,
                explanation: "d = 3, a₂₀ = -5 + (20-1)×3 = -5 + 57 = 52"
            },
            {
                question: "13. A staircase has steps with heights 10cm, 20cm, 30cm, ... What is the height of 15th step?",
                options: ["140cm", "150cm", "160cm", "170cm"],
                correct: 1,
                explanation: "a₁₅ = 10 + (15-1)×10 = 10 + 140 = 150cm"
            },
            {
                question: "14. Sum of first 'n' terms of AP is Sₙ = (n/2)[2a + (n-1)d]. What does 'd' represent?",
                options: ["First term", "Common difference", "Last term", "Total sum"],
                correct: 1,
                explanation: "In this formula, 'd' is the common difference between consecutive terms."
            },
            {
                question: "15. Find the sum of first 10 terms of AP: 5, 10, 15, 20, ...",
                options: ["250", "275", "300", "325"],
                correct: 1,
                explanation: "S₁₀ = (10/2)[2(5) + 9×5] = 5[10 + 45] = 5 × 55 = 275"
            },
            {
                question: "16. Which of these is an AP? A: 1,3,5,7  B: 2,4,8,16  C: 10,20,30,40",
                options: ["A only", "B only", "C only", "A and C only"],
                correct: 3,
                explanation: "A is AP (d=2), B is GP (not AP), C is AP (d=10). So A and C are APs."
            },
            {
                question: "17. In AP, if a = 2 and d = 3, what is a₇?",
                options: ["20", "21", "22", "23"],
                correct: 0,
                explanation: "a₇ = 2 + (7-1)×3 = 2 + 18 = 20"
            },
            {
                question: "18. Find the common difference of AP: 7, 4, 1, -2, -5, ...",
                options: ["-3", "-2", "3", "2"],
                correct: 0,
                explanation: "d = 4 - 7 = -3. The AP is decreasing."
            },
            {
                question: "19. Sum of first 6 terms of AP 1, 2, 3, 4, 5, 6 is?",
                options: ["18", "20", "21", "24"],
                correct: 2,
                explanation: "S₆ = (6/2)[2(1) + 5×1] = 3 × 7 = 21"
            },
            {
                question: "20. A runner runs 1km, 1.2km, 1.4km daily for 10 days. Total distance?",
                options: ["13km", "14km", "19km", "21km"],
                correct: 2,
                explanation: "a=1, d=0.2, a₁₀=1+9(0.2)=2.8. S₁₀ = (10/2)(1+2.8) = 5 × 3.8 = 19km"
            }
        ];

        let currentQuestion = 0;
        let userAnswers = new Array(quizData.length).fill(null);
        let answered = new Set();

        function generateQuiz() {
            const container = document.getElementById('quizContainer');
            quizData.forEach((q, index) => {
                const div = document.createElement('div');
                div.className = 'question-container';
                div.id = `q${index}`;
                div.innerHTML = `
                    <div class="question-num">Question ${index + 1} of ${quizData.length}</div>
                    <div class="question-text">${q.question}</div>
                    <div class="options">
                        ${q.options.map((opt, i) => `
                            <div class="option" onclick="selectAnswer(${index}, ${i})">${opt}</div>
                        `).join('')}
                    </div>
                    <div class="feedback" id="feedback${index}"></div>
                `;
                container.appendChild(div);
            });
            showQuestion(0);
        }

        function showQuestion(index) {
            document.querySelectorAll('.question-container').forEach(q => q.classList.remove('active'));
            document.getElementById(`q${index}`).classList.add('active');
            currentQuestion = index;

            const progress = ((index + 1) / quizData.length) * 100;
            document.querySelector('.progress-fill').style.width = progress + '%';

            document.querySelector('.btn-prev').style.display = index === 0 ? 'none' : 'inline-block';
            document.querySelector('.btn-next').style.display = index === quizData.length - 1 ? 'none' : 'inline-block';
            document.getElementById('finishBtn').style.display = index === quizData.length - 1 ? 'inline-block' : 'none';
        }

        function selectAnswer(index, optionIndex) {
            const options = document.querySelectorAll(`#q${index} .option`);
            options.forEach(opt => opt.classList.remove('selected', 'correct', 'incorrect'));
            
            const correct = quizData[index].correct;
            userAnswers[index] = optionIndex;
            answered.add(index);

            options[optionIndex].classList.add('selected');
            
            const feedback = document.getElementById(`feedback${index}`);
            if (optionIndex === correct) {
                options[optionIndex].classList.add('correct');
                feedback.className = 'feedback show feedback-correct';
                feedback.innerHTML = `<div class="feedback-text">✓ Correct!</div><div class="explanation">${quizData[index].explanation}</div>`;
            } else {
                options[optionIndex].classList.add('incorrect');
                options[correct].classList.add('correct');
                feedback.className = 'feedback show feedback-incorrect';
                feedback.innerHTML = `<div class="feedback-text">✗ Incorrect. The correct answer is: ${quizData[index].options[correct]}</div><div class="explanation">${quizData[index].explanation}</div>`;
            }
        }

        function nextQuestion() {
            if (currentQuestion < quizData.length - 1) {
                showQuestion(currentQuestion + 1);
            }
        }

        function previousQuestion() {
            if (currentQuestion > 0) {
                showQuestion(currentQuestion - 1);
            }
        }

        function finishQuiz() {
            const correct = userAnswers.filter((ans, i) => ans === quizData[i].correct).length;
            const percentage = Math.round((correct / quizData.length) * 100);

            document.getElementById('quizContainer').style.display = 'none';
            document.querySelector('.buttons').style.display = 'none';
            document.getElementById('results').classList.add('show');
            document.getElementById('scoreCircle').textContent = `${correct}/${quizData.length}`;
            document.getElementById('scoreText').textContent = `Score: ${percentage}%`;

            let resultHTML = '';
            userAnswers.forEach((ans, i) => {
                const isCorrect = ans === quizData[i].correct;
                resultHTML += `<div class="result-item ${isCorrect ? 'correct-result' : 'incorrect-result'}"><strong>Q${i+1}:</strong> ${isCorrect ? '✓' : '✗'} ${quizData[i].options[ans] || 'Not answered'}</div>`;
            });
            document.getElementById('resultDetails').innerHTML = resultHTML;
        }

        function restartQuiz() {
            userAnswers = new Array(quizData.length).fill(null);
            answered = new Set();
            document.getElementById('quizContainer').style.display = 'block';
            document.querySelector('.buttons').style.display = 'flex';
            document.getElementById('results').classList.remove('show');
            document.querySelectorAll('.feedback').forEach(f => f.classList.remove('show'));
            document.querySelectorAll('.option').forEach(o => o.classList.remove('selected', 'correct', 'incorrect'));
            showQuestion(0);
        }

        generateQuiz();
    </script>
</body>
</html>
