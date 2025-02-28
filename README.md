# -7DaysOfCode---L-gica-JS-4-7-Mais-loops-e-randomiza-o
criar um programinha que comece com um valor específico pré-definido entre 0 a 10 para o número que você vai adivinhar (7, por exemplo).

📌 O que eu fiz nesse desafio?
Criei um jogo interativo onde o usuário tenta adivinhar um número primo gerado pelo sistema. Mas, como eu não queria que fosse apenas um jogo comum, fui além e adicionei elementos para torná-lo mais envolvente. 🚀

🎯 Como o jogo funciona?
1️⃣ O jogador insere seu nome e inicia o jogo.
2️⃣ O sistema escolhe um número primo aleatório entre 0 e 100.
3️⃣ O jogador tem 3 tentativas para acertar.
4️⃣ Se errar, o jogo destaca os números chutados e dá dicas com a raiz quadrada do número secreto.
5️⃣ Se acabar o tempo (10 segundos), o jogo revela a resposta e encerra.
6️⃣ Ranking de jogadores para registrar pontuações.

💻 Implementação Técnica
📌 Escolhendo um número primo aleatório
Utilizei Math.random() para selecionar um número primo da lista. O código é assim:

javascript

const primes = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97];
const secretNumber = primes[Math.floor(Math.random() * primes.length)];
Isso faz com que o número gerado seja sempre um primo e não um número aleatório qualquer.

📌 Implementando as tentativas
Para garantir que o usuário tenha três chances, usei um contador de tentativas:

javascript

let attempts = 3;
function checkGuess() {
    let guess = parseInt(document.getElementById("guess").value);
    
    if (guess === secretNumber) {
        document.getElementById("result").textContent = `🎉 Parabéns! Você acertou!`;
        clearInterval(timer);
    } else {
        attempts--;
        if (attempts > 0) {
            document.getElementById("result").textContent = `❌ Errou! Você tem ${attempts} tentativas restantes.`;
        } else {
            document.getElementById("result").textContent = `😢 Fim de jogo! O número era ${secretNumber}.`;
            clearInterval(timer);
        }
    }
}
📌 Temporizador de 10 segundos
Para evitar que o jogador fique tentando indefinidamente, implementei um timer regressivo:

javascript

let timeLeft = 10;
let timer = setInterval(() => {
    timeLeft--;
    document.getElementById("timeLeft").textContent = timeLeft;
    if (timeLeft === 0) {
        clearInterval(timer);
        document.getElementById("result").textContent = `⏳ Tempo esgotado! O número era ${secretNumber}.`;
    }
}, 1000);
Se o tempo acabar antes do jogador acertar, o jogo encerra automaticamente.

🎨 O Design do Jogo
Gradiente rosa e roxo 💜💖 para um visual moderno.
Botões estilizados com hover para uma experiência interativa.
Animações suaves para feedback imediato ao usuário.
📌 O que aprendi nesse desafio?
🔥 Como manipular números aleatórios com Math.random() para criar lógica de jogo.
🔥 Como usar estruturas de repetição e controle (if/else) para limitar tentativas.
🔥 Como criar um timer dinâmico para controlar o tempo de jogo.
🔥 Como estilizar e estruturar um jogo interativo sem depender apenas de alert().
![Captura de tela_28-2-2025_153631_](https://github.com/user-attachments/assets/74d468b2-86ea-4942-9e77-7e2bc724e185)

🚀 Melhorias futuras
✅ Salvar o progresso no localStorage, para que os jogadores possam continuar depois.
✅ Adicionar um placar global, mostrando o histórico de acertos de cada jogador.
✅ Criar níveis de dificuldade, com ranges diferentes de números primos.
