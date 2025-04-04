// Card data and images matching solitr.com
const cardImages = {
    back: 'https://www.solitr.com/images/card-back.png',
    hearts: {
        'A': 'https://www.solitr.com/images/cards/hearts/1.png',
        '2': 'https://www.solitr.com/images/cards/hearts/2.png',
        // Add all heart cards...
    },
    // Add other suits...
};

class SolitaireGame {
    constructor() {
        this.createDeck();
        this.setupGame();
    }

    createDeck() {
        this.deck = [];
        const suits = ['hearts', 'diamonds', 'clubs', 'spades'];
        const ranks = ['A','2','3','4','5','6','7','8','9','10','J','Q','K'];
        
        suits.forEach(suit => {
            ranks.forEach(rank => {
                this.deck.push({
                    suit,
                    rank,
                    color: (suit === 'hearts' || suit === 'diamonds') ? 'red' : 'black',
                    image: cardImages[suit][rank]
                });
            });
        });
    }

    setupGame() {
        // Setup tableau with 7 columns
        const columns = document.querySelectorAll('.column');
        columns.forEach((col, index) => {
            // Add face-down cards
            for (let i = 0; i < index; i++) {
                this.addCardToColumn(col, true);
            }
            // Add face-up card
            this.addCardToColumn(col, false);
        });

        // Setup stock
        const stock = document.querySelector('.stock');
        for (let i = 0; i < 24; i++) {
            this.addCardToElement(stock, true);
        }
    }

    addCardToColumn(column, faceDown) {
        const card = document.createElement('div');
        card.className = `card ${faceDown ? 'face-down' : ''}`;
        if (!faceDown) {
            card.innerHTML = `
                <div class="rank top">${this.deck[0].rank}</div>
                <div class="suit">${this.getSuitSymbol(this.deck[0].suit)}</div>
                <div class="rank bottom">${this.deck[0].rank}</div>
            `;
            card.style.color = this.deck[0].color;
        }
        column.appendChild(card);
        this.deck.shift();
    }

    getSuitSymbol(suit) {
        switch(suit) {
            case 'hearts': return '♥';
            case 'diamonds': return '♦';
            case 'clubs': return '♣';
            case 'spades': return '♠';
        }
    }
}

// Initialize game
document.addEventListener('DOMContentLoaded', () => {
    new SolitaireGame();
});
