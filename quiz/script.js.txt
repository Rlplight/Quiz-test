const quizData = [
  {
    question: "What is the capital of India?",
    a: "Mumbai",
    b: "New Delhi",
    c: "Kolkata",
    d: "Chennai",
    correct: "b"
  },
  {
    question: "Which planet is known as the Red Planet?",
    a: "Earth",
    b: "Venus",
    c: "Mars",
    d: "Jupiter",
    correct: "c"
  },
  {
    question: "Who wrote 'Romeo and Juliet'?",
    a: "William Shakespeare",
    b: "Charles Dickens",
    c: "J.K. Rowling",
    d: "Mark Twain",
    correct: "a"
  },
  {
    question: "What is 5 + 7?",
    a: "10",
    b: "11",
    c: "12",
    d: "13",
    correct: "c"
  },
  {
    question: "Which is the largest ocean on Earth?",
    a: "Indian Ocean",
    b: "Atlantic Ocean",
    c: "Arctic Ocean",
    d: "Pacific Ocean",
    correct: "d"
  }
];

const quiz = document.getElementById("quiz");
const submitBtn = document.getElementById("submit");
const result = document.getElementById("result");

function loadQuiz() {
  quiz.innerHTML = "";

  quizData.forEach((q, index) => {
    const div = document.createElement("div");

    div.innerHTML = `
      <p>${index + 1}. ${q.question}</p>
      <label><input type="radio" name="q${index}" value="a"> ${q.a}</label><br>
      <label><input type="radio" name="q${index}" value="b"> ${q.b}</label><br>
      <label><input type="radio" name="q${index}" value="c"> ${q.c}</label><br>
      <label><input type="radio" name="q${index}" value="d"> ${q.d}</label><br>
    `;

    quiz.appendChild(div);
  });
}

submitBtn.addEventListener("click", () => {
  let score = 0;

  quizData.forEach((q, index) => {
    const answer = document.querySelector(`input[name="q${index}"]:checked`);
    if (answer && answer.value === q.correct) {
      score++;
    }
  });

  result.innerText = `You scored ${score} out of ${quizData.length}`;
});

loadQuiz();