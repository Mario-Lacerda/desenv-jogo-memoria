# Desafio Dio - Desenvolvendo um Jogo da Memória



Neste projeto, criaremos um jogo da memória usando HTML, CSS e JavaScript. O jogo da memória é um jogo clássico em que os jogadores tentam combinar pares de cartas viradas para baixo.



### **Pré-requisitos**

- Conhecimento básico de HTML, CSS e JavaScript



### **Passos**



### **1. Criar um Tabuleiro de Jogo HTML**



Comece criando um tabuleiro de jogo HTML básico com um contêiner para as cartas:

plaintext



```plaintext
<div class="game-board">
  <!-- As cartas serão adicionadas aqui -->
</div>
```



### **2. Criar as Cartas HTML**



Em seguida, crie as cartas HTML. Cada carta deve ter uma face frontal e uma face traseira:

plaintext



```plaintext
<div class="card">
  <div class="card-front"></div>
  <div class="card-back"></div>
</div>
```



### **3. Adicionar Estilos CSS**



Agora, adicione estilos CSS para o tabuleiro de jogo e as cartas. Isso inclui estilos para o tamanho e layout do tabuleiro, bem como o design das cartas:

css



```css
.game-board {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 10px;
  margin: 0 auto;
}

.card {
  width: 100px;
  height: 100px;
  background-color: #fff;
  border: 1px solid #000;
  cursor: pointer;
}

.card-front {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 24px;
}

.card-back {
  background-color: #000;
}
```



### **4. Adicionar JavaScript para Controlar o Jogo**



Finalmente, adicione JavaScript para controlar o jogo. Isso inclui lógica para virar as cartas, verificar se elas correspondem e manter o controle dos pares combinados:

javascript



```javascript
const gameBoard = document.querySelector('.game-board');
const cards = document.querySelectorAll('.card');
let flippedCards = [];
let matchedCards = [];

// Adicione um evento de clique a cada carta
cards.forEach(card => {
  card.addEventListener('click', () => {
    // Verifique se a carta já foi combinada
    if (matchedCards.includes(card)) return;

    // Verifique se já existem duas cartas viradas
    if (flippedCards.length === 2) return;

    // Vire a carta
    card.classList.add('flipped');
    flippedCards.push(card);

    // Verifique se as duas cartas viradas correspondem
    if (flippedCards.length === 2) {
      if (flippedCards[0].innerHTML === flippedCards[1].innerHTML) {
        // As cartas correspondem, mantenha-as viradas
        matchedCards.push(...flippedCards);
        flippedCards = [];
      } else {
        // As cartas não correspondem, vire-as de volta
        setTimeout(() => {
          flippedCards.forEach(card => card.classList.remove('flipped'));
          flippedCards = [];
        }, 1000);
      }
    }

    // Verifique se todas as cartas foram combinadas
    if (matchedCards.length === cards.length) {
      alert('Parabéns, você venceu!');
    }
  });
});
```





### Módulo 1: Estrutura Básica



**HTML**

```
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Jogo da Memória</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <section class="tabuleiro">
        <!-- Cartas serão inseridas aqui -->
    </section>
    <button id="iniciar-jogo">Iniciar Jogo</button>
    <script src="game.js"></script>
</body>
</html>
```



**CSS**

```
.tabuleiro {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    perspective: 1000px;
}

.carta {
    width: 100px;
    height: 150px;
    margin: 10px;
    border: 1px solid #ccc;
    box-shadow: 3px 3px 5px rgba(0,0,0,0.3);
    cursor: pointer;
    transform-style: preserve-3d;
    transition: transform 0.5s;
}

.carta.virada {
    transform: rotateY(180deg);
}
```



**JavaScript**

```
document.getElementById('iniciar-jogo').addEventListener('click', iniciarJogo);

function iniciarJogo() {
    // Código para iniciar o jogo
}
```



### Módulo 2: Lógica do Jogo



**JavaScript**

```
function embaralharCartas(cartas) {
    for (let i = cartas.length - 1; i > 0; i--) {
        let j = Math.floor(Math.random() * (i + 1));
        [cartas[i], cartas[j]] = [cartas[j], cartas[i]];
    }
}

function virarCarta(carta) {
    carta.classList.add('virada');
    // Código para verificar se formou um par
}

function verificarPar(carta1, carta2) {
    if (carta1.dataset.imagem === carta2.dataset.imagem) {
        // É um par!
    } else {
        // Não é um par, desvirar as cartas
    }
}
```



### Módulo 3: Efeitos 3D no CSS



**CSS**

```
.carta .frente, .carta .verso {
    position: absolute;
    backface-visibility: hidden;
}

.carta .verso {
    transform: rotateY(180deg);
}
```



### Módulo 4: Condicionais e IIFE



**JavaScript**

```
(function() {
    const cartas = [];
    // Código para criar cartas e adicionar ao array
    embaralharCartas(cartas);
    // Código para adicionar evento de clique nas cartas
})();
```



### Módulo 5: Manipulação de Array



**JavaScript**

```
let cartas = [
    { id: 1, imagem: 'imagem1.png', virada: false },
    { id: 2, imagem: 'imagem2.png', virada: false },
    // Adicione todas as cartas
];

cartas.forEach(carta => {
    // Código para criar elemento da carta e adicionar ao tabuleiro
});
```





### **Conclusão**



Neste projeto, criamos um jogo da memória usando HTML, CSS e JavaScript. Este jogo pode ser personalizado com diferentes imagens ou palavras nas cartas para torná-lo mais desafiador ou divertido.
