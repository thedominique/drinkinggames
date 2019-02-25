#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <stdbool.h>

typedef enum suit {
	HEART = 3,
	CLUB = 2,
	DIAMOND = 1,
	SPADE = 0,
} suit_t;

typedef struct card{
	int value;
	suit_t suit; 
} card_t;


typedef struct deck {
	card_t cards[52];
	int count;
} deck_t;

bool getred(){
	char color;
	printf("Black or red?: ");
	scanf(" %c", &color);
	switch(color){
		case 'b': return false; 
		case 'r' : return true;
	}
	
}

card_t getcard(deck_t* deck){
	int index = rand()%deck->count;
	card_t card = deck->cards[index];
	deck->cards[index] = deck->cards[deck->count-1];
	deck->count--; 
	
	return card;
}

bool card_is_red(card_t card){
	return card.suit == HEART || card.suit == DIAMOND;
}

const char* suite_str(card_t card) {
	const char* suit_str;
	switch (card.suit) {
		case HEART:
			return "hearts";
		case CLUB:
			return "clubs";
		case DIAMOND:
			return "diamonds";
		case SPADE:
			return "spades";
	}
	return "?";
}

void printrules(){
	printf("Rules:\n");
}

void startgame(int *ans){
	printf("Do you want to start the game and get wrecked? \n ans : ");
	scanf(" %d", ans);
}

int main(int argc, char **argv)
{	int ans;
	deck_t deck;
	for(int i=0; i<52;i++){
		deck.cards[i].suit = i/13; // i/13 = 0,1,2,3
		deck.cards[i].value= i % 13; // 0,1,2,.....13
	}
	deck.count=52;
	
	srand(time(NULL));
	
	printrules();
	
	startgame(&ans);
	while (ans !=0){
		bool is_red = getred();
		card_t card = getcard(&deck);
		printf("%d %d %s\n", deck.count, card.value + 1, suite_str(card));
		if (is_red == card_is_red(card)) {
			printf("Pass!\n");
		} else {
			printf("Drink!\n");
		}	
	}

	return 0;
}
