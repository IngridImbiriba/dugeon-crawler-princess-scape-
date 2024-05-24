#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <conio.h>
#include <string.h>
#include <time.h>
#include <unistd.h>
#include <windows.h> // Para reproducaoo de som no Windows

// Definicao das notas musicais
#define C 523
#define D 587
#define E 659
#define F 698
#define G 784
#define A 880
#define B 988


// Definicao das duracoes das notas
#define HALF 500
#define QUARTER 250
#define EIGHTH 125
#define SIXTEENTH 63

#define MAP_1_WIDTH 15
#define MAP_1_HEIGHT 15
#define MAP_2_WIDTH 30
#define MAP_2_HEIGHT 30
#define MAP_3_WIDTH 60
#define MAP_3_HEIGHT 68

// Função para reproduzir uma nota
void playTone(int frequency, int duration) {
    Beep(frequency, duration);
}
// Função para reproduzir 
void playprincessTheme() {
    // Notas do tema 
    int princessTheme[] = {  G, A, B, A, G, F, E, F, G, E, D, E, F, G, A, B, C, D, E, D, C, B, A, B, C, A, G, A, B, C, D, E, };
    // DuraÃƒ §Ãƒ µes das notas correspondentes
    int NoteDurations[] = { EIGHTH, QUARTER, QUARTER, QUARTER, HALF, EIGHTH, QUARTER, QUARTER,
                            QUARTER, QUARTER, QUARTER, QUARTER, QUARTER, QUARTER, QUARTER, HALF };

    // Reproduz as notas uma a uma
    int NumNotes = sizeof(princessTheme) / sizeof(princessTheme[0]);
    int i;
    for (i = 0; i < NumNotes; i++) {
        playTone(princessTheme[i], NoteDurations[i]);
        Sleep(50); // Pausa entre as notas
    }
}

void INTRO() {
//intro antes do menu
	system("color 06");
	 printf("\n\n");
    printf("  PPPPPPP    RRRRRRRR     IIIIIIIIIII  NNNN     NN   CCCCCC   EEEEEEEEE  SSSSSSSS    SSSSSSSS\n");
    printf("  PP    PP   RR    RRR       IIII      NN NN    NN  CC        EE         SS          SS      \n");
    printf("  PP    PP   RR    RRR       IIII      NN  NN   NN  CC        EE         SS          SS   \n");
    printf("  PPPPPPP    RRRRRRRR        IIII      NN   NN  NN  CC        EEEEEEEE     SSSSSSSS    SSSSSSS\n");
    printf("  PP         RRR    RR       IIII      NN    NN NN  CC        EE                 SSS        SS\n");
    printf("  PP         RR    RR        IIII      NN     NNNN  CC        EE                 SS          SS\n");
    printf("  PP         RR     RR    IIIIIIIIIII  NN      NNN   CCCCCC   EEEEEEEEE  SSSSSSSS   SSSSSSSS\n");
    printf("\n\n");
    printf("\t\t\t\t\t    SSSSSSSS   CCCCCC  AAAAA    PPPPPPPP   EEEEEEEEE\n");
    printf("\t\t\t\t\t  SS          CC      AA   AA   PP    PP  EE       \n");
    printf("\t\t\t\t\t  ss          CC     AAAAAAAAA  PP    PP  EE       \n");
    printf("\t\t\t\t\t    SSSSSSS   CC     AAAAAAAAA  PPPPPPPP  EEEEEEEE \n");
    printf("\t\t\t\t\t          SS  CC     AA     AA  PP        EE       \n");
    printf("\t\t\t\t\t           SS CC     AA     AA  PP        EE       \n");
    printf("\t\t\t\t\t    SSSSSSSS   CCCCC AA     AA  PP         EEEEEEEEE\n");

    usleep(1000000); // Espera por 1 segundo
    
    // Reproduz o tema princess Intro
    playprincessTheme();

    printf("\n\n\n\n");
    printf("\t\t\t\t               Loading...\n\n\n");
    usleep(500000); // Espera por 0,5 segundos

    printf("\t\t\t\t\t\t[    ]");
    fflush(stdout);
    usleep(500000); // Espera por 0,5 segundos

    printf("\r\t\t\t\t\t\t[==  ]");
    fflush(stdout);
    usleep(500000); // Espera por 0,5 segundos

    printf("\r\t\t\t\t\t\t[====]");
    fflush(stdout);
    usleep(500000); // Espera por 0,5 segundos
	
    printf("\n\n\n");
    system("cls");
}

//Void para delay
void delay(int segundos)
{
	int milli_seconds = 1000 * segundos;
	
	clock_t start_time = clock();
	
	while (clock() < start_time + milli_seconds);
	
}
//variaveis do player
typedef struct{
	int player_x;
	int player_y;
	int has_key;
	int vida;
}Player;

Player player1; //Player no mapa 1
Player player2; //Player no mapa 2
Player player3; //Player no mapa 3

//variaveis dos monstros
typedef struct{
	int monster_x;
	int monster_y;
	int direction;
}Monster;

Monster monster1A; //Primeiro monstro nivel 1
Monster monster1B; //Segundo monstro nivel 1
Monster monster2A;
Monster monster2B;

void MAP_3() {  //fase 3

	player3.vida = 4; //quantidade de vida do personagem
	player3.player_x = 59;//local que o personagem nasce
	player3.player_y = 64;//local que o personagem nasce
	int chave_x = 5 , chave_y =56; // local onde aparece a chave
	int key_placed = 0;//verifica se o personagem tem a chave ou nao
  player2.has_key = 0;
	
	char map_3[MAP_3_HEIGHT][MAP_3_WIDTH] = {  //impressão do mapa da fase 3 60x60
      {'*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','D','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*'},
	{'*',' ',' ',' ',' ',' ',' ',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ',' ',' ',' ',' ',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*',' ',' ',' ',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*',' ',' ',' ',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ','R',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ', ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*',' ',' ',' ',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*',' ',' ',' ',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*',' ',' ',' ',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*',' ',' ',' ',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*',' ',' ',' ',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*',' ',' ',' ',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*',' ',' ','M',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*','*','*','*','>','*','*','*',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*','*','*','*','*','*','*','*','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*',' ',' ',' ',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*',' ',' ',' ',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','O',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*',' ',' ',' ',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ','*','*','*','*','*','*','*','*','*',' ',' ',' ','*','*','*','*','*','*','*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*',' ',' ','*',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*',' ',' ','*',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ','*','*','*',' ','*',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ','*','*','*',' ','*',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ',' ',' ',' ','*',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ',' ',' ',' ','*',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ','*','*','*','*','*','*','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ','*',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ','*',' ','*','*','*','*','*','*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ','*',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*','*','*','*','*','*','*','*','*','*','*','*','*'},
	{'*',' ','*','*','*','*','*','*','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ','*',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ','*',' ','*','*','*','*','*','*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*','*','<','*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ','*',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ','*',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ','#','#','#','#','#','#','#','#','#',' ','*'},
	{'*',' ','*','*','*','*','*',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ','#',' ',' ',' ',' ','H',' ',' ','#',' ','*'},
	{'*',' ',' ',' ',' ',' ','*',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ','#','#','#','#','#','#','#',' ','#',' ','*'},
	{'*',' ',' ',' ',' ',' ','*',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ','#',' ','*'},
	{'*','*','*','*',' ','*','*','*','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ','#','#','#','#','#','#','#','#','#',' ','*'},
	{'*',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ','*','*','*','*','*','*','*','*','*',' ','*'},
	{'*',' ',' ','*','*','*','*','*','*','*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*','*','*','*','*','*','*','*',' ',' ','*'},
	{'*','#',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*','*',' ',' ','*','*','*','*','*','*','*','*','*','*',' ',' ',' ','*','*','*','*','*','*','*','*','*','*','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*','#',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*','*',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*','#',' ','#','#','#','#','#','#','#',' ',' ','#','#','#','#','#','#','#','#','#','*',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ','*',' ','*','*','*','*','*','*','*','*','*'},
	{'*','#',' ','#',' ',' ',' ',' ','#','#',' ',' ','#',' ',' ',' ','#',' ',' ',' ','#','*',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*','#',' ','#',' ',' ',' ',' ','#','#',' ',' ','#',' ',' ',' ','#',' ',' ',' ','#','*',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ','*',' ','*',' ','*','*','*','*','*',' ','*'},
	{'*','#',' ','#',' ',' ','#',' ','#','#',' ',' ','#',' ','#',' ','#',' ','#',' ','#','*',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ','*',' ','*',' ','*',' ',' ','*',' ',' ','*'},
	{'*','#',' ','#',' ',' ','#',' ','#','#',' ',' ','#',' ','#',' ','#',' ','#',' ','#','*',' ',' ','*','*',' ',' ',' ',' ','*',' ','*',' ',' ',' ',' ',' ',' ','*',' ','*',' ',' ',' ',' ',' ','*',' ','*',' ','*',' ','*',' ',' ','*',' ','*','*'},
	{'*','#',' ','#',' ',' ','#',' ','#','#',' ',' ','#',' ','#',' ','#',' ','#',' ','#','*',' ',' ','*','*',' ',' ',' ','*','*',' ','*','*',' ',' ',' ',' ','*','*',' ','*','*',' ',' ',' ',' ','*',' ','*',' ','*',' ','*',' ',' ','*',' ',' ','*'},
	{'*','#',' ','#',' ',' ','#',' ','#','#',' ',' ','#',' ','#',' ','#',' ','#',' ','#','*',' ',' ','*','*',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ','*',' ','*',' ','*',' ','*',' ',' ','*',' ',' ','*'},
	{'*','#',' ','#',' ',' ','#',' ','#','#',' ',' ','#',' ','#',' ','#',' ','#',' ','#','*',' ',' ','*','*',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ','*','*','*',' ','*',' ','*',' ','*','*','*',' ','*'},
	{'*','#',' ','#','#','#','#',' ','#','#',' ',' ','#',' ','#',' ','#',' ','#',' ','#','*',' ',' ','*','*',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ','*',' ','*',' ',' ',' ','*',' ','*','*','*',' ','*'},
	{'*','#',' ',' ',' ',' ',' ',' ','#','#',' ',' ','#',' ','#',' ','#',' ','#',' ','#','*',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ',' ','*',' ','*','*','*','*','*',' ','*','*','*',' ','*'},
	{'*','#','#','#','#','#','#','#','#','#',' ',' ','#',' ','#',' ','#',' ','#',' ','#','*',' ',' ',' ',' ',' ',' ',' ','*',' ','B',' ','*',' ',' ',' ',' ','*',' ','b',' ','*',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*','#','#','#','#','#','#','#','#','#',' ',' ','#',' ','#',' ','#',' ','#',' ','#','*',' ',' ','*','*',' ',' ',' ','*','*','*','*','*',' ',' ',' ',' ','*','*','*','*','*',' ',' ',' ',' ','*','*','*','*',' ',' ','*','*','*','*','*','*','*'},
	{'*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','#',' ',' ',' ','#',' ',' ',' ',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*'},
	{'*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','#',' ',' ',' ','#',' ',' ',' ',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','D'},
	{'*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*'},

};

//local onde são gerados os monstros

    monster1A.monster_x = 36; 
    monster1A.monster_y = 59;
    
    monster1B.monster_x = 54;
    monster1B.monster_y = 41 ;
	
    monster2A.monster_x = 21;
    monster2A.monster_y = 62;
    
    monster2B.monster_x = 22;
    monster2B.monster_y = 16;
    
	
	char input;
	
		
		while(1){
			
		system("cls || clear");
		
		int y;
		int x;

  //impressão do mapa, personagem e monstros
  
    	for (y = 0; y < MAP_3_HEIGHT; y++) {
        	for (x = 0; x < MAP_3_WIDTH; x++) {
        		
            	if (x == player3.player_x && y == player3.player_y) {
                printf("& ");}
                
                else if (x == monster1A.monster_x && y == monster1A.monster_y) {
                printf("X ");}
                
                else if (x == monster1B.monster_x && y == monster1B.monster_y) {
                printf("X ");}
                
				else if (x == monster2A.monster_x && y == monster2A.monster_y) {
                printf("V ");} 
                
				else if (x == monster2B.monster_x && y == monster2B.monster_y) {
                printf("V ");}
                
				else {
                printf("%c ", map_3[y][x]);
            	}
        	}
        printf("\n");
    	}

    //imprimir a quantidade de vida na tela
    printf("Vida: %d\n\n", player3.vida);

    //função game over(caso a vida chegue em zero)
    if(player3.vida==0){
					system("cls || clear");

					printf("Voce deu seu melhor princesa NAO DESISTA!!!!!!\n\n"); delay(2);
					printf("Retornando pro menu..."); delay(2);
					player3.vida = player3.vida + 3; 

					MENU(); //retorna para o menu
				}
		
        input = getch();

        //movimentação personagem
		if (map_3[player3.player_y][player3.player_x] == '=') {
                    //MAP_2();
				}
        switch (input) {
            case 'a': //lado esquerdo
                if (map_3[player3.player_y][player3.player_x - 1] != '*' && map_3[player3.player_y][player3.player_x - 1] != '#') {
                    player3.player_x--;
                }
                break;
            case 'd': //lado direito
                if ((map_3[player3.player_y][player3.player_x + 1] != '*' && map_3[player3.player_y][player3.player_x + 1] != '#') &&
                    !(map_3[player3.player_y][player3.player_x] == 'D' && !player3.has_key)) {
                    player3.player_x++;
                }
              
            case 'w': //para cima
                if (map_3[player3.player_y - 1][player3.player_x] != '*' && map_3[player3.player_y - 1][player3.player_x] != '#') {
                    player3.player_y--;
                }
            
                break;
            case 's': //para baixo
                if (map_3[player3.player_y + 1][player3.player_x] != '*' && map_3[player3.player_y + 1][player3.player_x] != '#') {
                    player3.player_y++;
                }
                break;
                
            case 'i': //interação com o botao
              if (map_3[player3.player_y][player3.player_x] == 'O' && !key_placed) {
                    key_placed = 1;
                    map_3[chave_y][chave_x] = '@'; //aparece a chave em outro local
                } 
		    else if (map_3[player2.player_y][player3.player_x] == '@') {  //pegar chave
                    player3.has_key = 1;
                    map_3[player3.player_y][player3.player_x] = ' ';
                    printf("=========================\n// Voce pegou a chave! //\n========================="); delay(1);
		   }
               if (map_3[player3.player_y][player3.player_x] == 'D'&&player3.has_key) { //abrir porta
                    map_3[player1.player_y][player1.player_x] = '=';
                    printf("=========================\n// Voce abriu a porta! //\n========================="); delay(1);
                    printf("\n");
                    //conclusão do jogo
                    printf("=======================\n// Voce conseguiu princesa, seu principe ainda te espera!!! //\n======================="); delay(2); 
			 
    MENU(); //retorne ao menu
		     }
				break;						  
			}
          //função do teleporte 
   
			if (map_3[player3.player_y][player3.player_x] == '>' ) {
                player3.player_y=31;
                player3.player_x=29;
             	}
                  	else if (map_3[player3.player_y][player3.player_x] == '<') {
                        player3.player_y= 11;
                        player3.player_x= 8 ;
                  }

                  //função vida quando interage com os espinhos
      if(map_3[player3.player_y][player3.player_x] == '#'){
				player3.vida = player3.vida - 1;  
				player3.player_x = 59,	player3.player_y = 64;
				}
                //interação com personagem
                if(map_3[player3.player_y][player3.player_x] == 'H'){
                	
                	
			    printf("\t \t - QUEM ESTA INVADINDO MEU SONO?\n   \t \t - Ah mais uma princesa...elas sempre tentam fugir, saiba que nao foi a primeira a ser raptada, o monstro sempre é mais rapido \n \t \t - voce e uma princesa mas sua cara me parece de uma guerreira\n \t \t - Eu nao saiu da minha caverna ent nao sei explorar esse labirinto, porem duas amigas muito antigas minhas elas sabem de tudo daqui, elas ficam la embaixo procure por B ela sabera te ajudar :D  "); delay(20);
                      
		    }
		     if(map_3[player3.player_y][player3.player_x] == 'B'){
                
		         printf("\t \t -Mas uma...\n \t \t - sera que esse monstro ainda nao entendeu que ninguem vai querer ele se ele continuar raptando pessoas\n \t \t - H te mandou aqui, estou morrendo de saudade dela mas ela nao sai daquela caverna de espinho... \n eu tenho medo de la \n \t \t - Voce quer ajuda para sair? oh querida voce ira correr  bastante por todo esse labirinto ate encontrar a chave de fuga dessa masmora\n \t \t - Mas nisso apenas minha irma b podera ajudar, basta apenas procura-la na sala ao lado ");delay(20);
		    	
                }
		    if(map_3[player3.player_y][player3.player_x] == 'b'){
		    
		    
		    printf("\t \t - Oh quanto tempo nao recebo visitantes\n \t \t - Minha irma B te mandou para o lugar certo, conheço este lugar na ponta da minha mao\n \t \t - fui umas das unicas que passei bons anos tentando sair daqui... e poise\n \t \t - Mas querida espero que sua memoria seja boa pois nao tenho papel e tera que decorar a coordenada\n \t \t - esquerda, direita, direita,esquerda, direita, esquerda, direita, esquerda, esquerda, esquerda, direita e finalmente direita "); delay(25);
		    }
		    if(map_3[player3.player_y][player3.player_x] == 'M'){  

                
                 printf("\t \t - Uma princesa oh que surpresa- diz sem alegria no rosto\n \t \t - voce chegou no lugar certo, mas a partir daqui as coisas ficaram dificeis\n \t \t - Voce ira entrar pelo espelho magico '>' assim aparecendo na sala onde o monstro se esconde aperte o botao que acionara a chave aqui no labirinto de fora\n \t \t - em seguinda retorne para sala e saia pela porta \n \t \t - Um ALERTA  ele estara correndo até voce entao fuja o maximo que puder");delay(30);
		    
                }

        }
       
        
      int dx = player3.player_x - monster2A.monster_x;
    	int dy = player3.player_y - monster2A.monster_y;

    	int step_x = (dx > 0) ? 1 : -1;
    	int step_y = (dy > 0) ? 1 : -1;

    	// Verifica se o monstro alcanÃ§ou o jogador
    	if (dx == 0 && dy == 0) {
       		player3.vida = player3.vida - 1; 
    	}

    // Movimento do monstro em direçao ao jogador
    	if (abs(dx) > abs(dy)) {
        	if (map_3[monster2A.monster_y][monster2A.monster_x + step_x] != '*' && map_3[monster2A.monster_y][monster2A.monster_x + step_x] != '#') {
            	monster2A.monster_x += step_x;
        	}
    	} else {
        	if (map_3[monster2A.monster_y + step_y][monster2A.monster_x] != '*' && map_3[monster2A.monster_y + step_y][monster2A.monster_x] != '#') {
            monster2A.monster_y += step_y;
        	}
    	}
    	
    	int dx2 = player3.player_x - monster2B.monster_x;
    	int dy2 = player3.player_y - monster2B.monster_y;

    	int step_x2 = (dx2 > 0) ? 1 : -1;
    	int step_y2 = (dy2 > 0) ? 1 : -1;

    	// Verifica se o monstro alcanço o jogador
    	if (dx2 == 0 && dy2 == 0) {
       		player3.vida = player3.vida - 1; 
    	}

    // Movimento do monstro em direção ao jogador
    	if (abs(dx2) > abs(dy2)) {
        	if (map_3[monster2B.monster_y][monster2B.monster_x + step_x2] != '*' && map_3[monster2B.monster_y][monster2B.monster_x + step_x2] != '#') {
            	monster2B.monster_x += step_x2;
        	}
    	} else {
        	if (map_3[monster2B.monster_y + step_y2][monster2B.monster_x] != '*' && map_3[monster2B.monster_y + step_y2][monster2B.monster_x] != '#') {
            	monster2B.monster_y += step_y2;
        	}
    	}

     //movimentação monstro nivel 1
    	monster1A.direction = rand() % 4;
	
    	switch (monster1A.direction) {
        	case 0: 
        		if (map_3[monster1A.monster_y][monster1A.monster_x - 1] != '*' && map_3[monster1A.monster_y][monster1A.monster_x - 1] != '#' ) {
                    monster1A.monster_x--;
                }
            	break;
        	case 1: 
        		if (map_3[monster1A.monster_y][monster1A.monster_x + 1] != '*' && map_3[monster1A.monster_y][monster1A.monster_x + 1] != '#' ) {
        		    monster1A.monster_x++;
			    }
            	break;
        	case 2: 
            	if (map_3[monster1A.monster_y - 1][monster1A.monster_x] != '*' && map_3[monster1A.monster_y - 1][monster1A.monster_x] != '#' ) {
                    monster1A.monster_y--;
                }
            	break;
        	case 3:
        		if (map_3[monster1A.monster_y + 1][monster1A.monster_x] != '*' && map_3[monster1A.monster_y + 1][monster1A.monster_x] != '#'  ) {
                    monster1A.monster_y++;
                }
            	break;   
    		}
    	
    		monster1B.direction = rand() % 4;
	
    	switch (monster1B.direction) {
        	case 0: 
        		if (map_3[monster1B.monster_y][monster1B.monster_x - 1] != '*' && map_3[monster1B.monster_y][monster1B.monster_x - 1] != '#' ) {
                    monster1B.monster_x--;
                }
           		break;
        	case 1: 
        		if (map_3[monster1B.monster_y][monster1B.monster_x + 1] != '*' && map_3[monster1B.monster_y][monster1B.monster_x + 1] != '#' ) {
        		    monster1B.monster_x++;
			    }
            	break;
        	case 2: 
            	if (map_3[monster1B.monster_y - 1][monster1B.monster_x] != '*' && map_3[monster1B.monster_y - 1][monster1B.monster_x] != '#' ) {
                    monster1B.monster_y--;
                }
            	break;
        	case 3:
        		if (map_3[monster1B.monster_y + 1][monster1B.monster_x] != '*' && map_3[monster1B.monster_y + 1][monster1B.monster_x] != '#'  ) {
                    monster1B.monster_y++;
                }
            	break;   
    		}

      //interaçao do personagem com o monstro
			if (player3.player_x == monster1A.monster_x && player3.player_y == monster1A.monster_y || player3.player_x == monster1B.monster_x && player3.player_y == monster1A.monster_y){
			
			 player3.vida--;	
		
    }
}


void MAP_2() { //fase 2

	player2.vida = 4; //quantidade de vida do personagem
	player2.player_x = 1;//local onde o personagem nasce
	player2.player_y = 26; //local onde o personagem nasce
	int chave_x = 26 , chave_y =3; //local onde ira aparecer a chave
  int monstro_x = 4, monstro_y = 16; //impressão do monstro nivel 1
  int key_placed = 0; //tem a chave ou nao
  player2.has_key = 0;
	
	char map_2[MAP_2_HEIGHT][MAP_2_WIDTH] = { //impressão mapa fase 2
    {'*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*'},
    {'*','#','#','#','#','#','#','#','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ','*','*','*','*',' ','*'},
    {'*','#',' ',' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ','*',' ',' ',' ',' ','*'},
    {'*','#',' ','#','#','#','#',' ','*',' ','*',' ','*','*','*','*','*','*','*','*','*','*',' ',' ','*',' ',' ','*',' ','*'},
    {'*','#',' ','#','O',' ','#',' ','*',' ','*',' ','*',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ','*',' ',' ','*',' ','*'},
    {'*','#',' ','#',' ',' ','#',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*','*',' ','*'},
    {'*','#',' ','#','#',' ','#',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},  
    {'*','#',' ',' ',' ',' ','#',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*','#','#','#','#','#','#',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*','*','*','*','*','*','*',' ','*','*','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*','*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*','*',' ',' ',' ',' ','*','*','*','*','*','*','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*','*',' ',' ','*',' ','*',' ',' ',' ',' ',' ',' ',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*','*',' ',' ','*',' ','*',' ',' ','*','*','*','*','*','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*','*',' ',' ','*','*','*',' ',' ','*','*',' ',' ',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*',' ',' ',' ',' ',' ',' ',' ',' ',' ','*','*','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*',' ',' ',' ',' ',' ',' ',' ',' ',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*','*','*','*','*','*','*','*','*','*','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*','#','#','#','#','#','#','#','#','#','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*',' ','#',' ',' ',' ','#',' ',' ',' ',' ',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*',' ','#',' ','#',' ','#',' ','#',' ','*','*','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'*',' ','#',' ','#',' ','#',' ','#',' ','*',' ',' ',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ','*',' ',' ','*'},
    {'D',' ',' ',' ','#',' ',' ',' ','#',' ','*',' ',' ',' ',' ',' ',' ',' ','*',' ',' ',' ','*',' ',' ',' ','*',' ',' ','D'},
    {'*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*','*'},      

};
	
	 
 
	char input;
		
		while(1){
		
		system("cls");
		
		int y;
		int x;
  
		//movimentação monstro nivel 1
		int movimento = rand() % 4; 

          switch (movimento)
        {
            case 0: 
                if (map_2[monstro_y - 1][monstro_x] != '*')
                {
                    monstro_y--;
                }
                break;
            case 1: 
                if (map_2[monstro_y + 1][monstro_x] != '*')
                {
                    monstro_y++;
                }
                break;
            case 2: 
                if (map_2[monstro_y][monstro_x - 1] != '*')
                {
                    monstro_x--;
                }
                break;
            case 3:
                if (map_2[monstro_y][monstro_x + 1] != '*')
                {
                    monstro_x++;
                }
                break;
        }

		//impressão do mapa, personagem e monstro
    	for (y = 0; y < MAP_2_HEIGHT; y++) {
        	for (x = 0; x < MAP_2_WIDTH; x++) {
            	if (x == player2.player_x && y == player2.player_y) {
                printf("& ");
            	} 
			
		      else if (x == monstro_x && y == monstro_y) {
                printf("X ");
            	} 
            
            	else {
                printf("%c ", map_2[y][x]);
            	}
        	}
        printf("\n");
    }
    
    printf("Vida: %d\n\n", player2.vida);//impressão da vida
    if(player2.vida==0){ //caso a vida zere
					system("cls");

					printf("Voce deu seu melhor princesa NAO DESITA!!!\n\n"); delay(2); //função gamer over
					printf("Retornando pro menu..."); delay(2);
					player2.vida = player2.vida + 3; 

					MENU(); //retorna ao menu
				}
		
        input = getch();

  //mudança da fase 2 para fase 3
		if (map_2[player2.player_y][player2.player_x] == '=') {
                    MAP_3();
				}
		
        switch (input) {
            case 'a'://para esquerda
                if (map_2[player2.player_y][player2.player_x - 1] != '*') {  //fisica//
                    player2.player_x--;
                }
              
                break;
            case 'd'://para direita
                if (map_2[player2.player_y][player2.player_x + 1] != '*') {
                    player2.player_x++;
                }
             
                break;
            case 'w'://para cima
                if (map_2[player2.player_y - 1][player2.player_x] != '*') {
                    player2.player_y--;
                }
              
                break;
            case 's'://para baixo
                if (map_2[player2.player_y + 1][player2.player_x] != '*') {
                    player2.player_y++;
                }
               
                break;
            case 'i': 
            //interação com o botao
               if (map_2[player2.player_y][player2.player_x] == 'O' && !key_placed) {
                    key_placed = 1; //tem chave
                    map_2[chave_y][chave_x] = '@';//aparece a chave
                } 
		    else if (map_2[player2.player_y][player2.player_x] == '@') { //função pegar chave
                    player2.has_key = 1;
                    map_2[player2.player_y][player2.player_x] = ' ';
                    printf("=========================\n// Voce pegou a chave! //\n========================="); delay(1);
		   }
               if (map_2[player2.player_y][player2.player_x] == 'D'&&player2.has_key) { função abrir porta
                    map_2[player1.player_y][player1.player_x] = '=';
                    printf("=========================\n// Voce abriu a porta! //\n========================="); delay(1);
                    printf("\n");
                    printf("=======================\n// Ande para avancar //\n======================="); delay(2);
                    MAP_3();
				}
				
                break;
          }
          //interaçao do personagem com os espinhos
        if(map_2[player2.player_y][player2.player_x] == '#'){
				player2.vida = player2.vida - 1;  
				player2.player_x = 1,	player2.player_y = 26;
				}
        }
    }
void MAP_1() { //fase 1

	player1.vida = 4; // quantidade de vida do personagem
	player1.player_x = 1; //local onde  a personagem nasce
	player1.player_y = 8; //local onde  a personagem nasce
	
	char map_1[MAP_1_HEIGHT][MAP_1_WIDTH] = {
            {'*', '*', '*', '*', '*', '*', '*', '*', '*', '*', '*', '*', '*', '*', '*'},
            {'*', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', '@', '*'},
            {'*', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', '*', ' ', ' ', ' ', '*'},
            {'*', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', '*', ' ', ' ', ' ', '*'},
            {'*', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', '*', '*', '*', '*', '*'},
            {'*', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', '*'},
            {'*', '*', '*', '*', '*', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', '*'},
            {'*', ' ', ' ', ' ', '*', '*', '*', '*', '*', '*', '*', ' ', ' ', ' ', '*'},
            {'*', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', '*', ' ', ' ', ' ', '*'},
            {'*', ' ', ' ', ' ', '*', '*', '*', '*', ' ', ' ', '*', ' ', ' ', ' ', '*'},
            {'*', ' ', ' ', ' ', '*', ' ', ' ', '*', ' ', ' ', '*', ' ', ' ', ' ', '*'},
            {'*', '*', '*', '*', '*', ' ', ' ', '*', ' ', ' ', '*', ' ', ' ', ' ', '*'},
            {'*', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', '*', ' ', ' ', ' ', '*'},
            {'D', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', '*'},
            {'*', '*', '*', '*', '*', '*', '*', '*', '*', '*', '*', '*', '*', '*', '*'},

	};
	
 
   
	
	char input;
	
		
		while(1){
		system("cls || clear");
		
		int y;
		int x;
  
	//impresão do mapa e personagem	
    	for (y = 0; y < MAP_1_HEIGHT; y++) {
        	for (x = 0; x < MAP_1_WIDTH; x++) {
            	if (x == player1.player_x && y == player1.player_y) {
                printf("& ");
            	} else {
                printf("%c ", map_1[y][x]);
            	}
        	}
        printf("\n");
    	}
    //im´pressão da vida
    printf("Vida: %d\n\n", player1.vida);
		
        input = getch();
        //passagem da fase 1 para fase 2
		if (map_1[player1.player_y][player1.player_x] == '=') {
                    MAP_2();
				}

    //movimentação personagem fase 1
        switch (input) {
            case 'a': 
                if (map_1[player1.player_y][player1.player_x - 1] != '*' ) {
                    player1.player_x--;
                }
                break;
            case 'd':
                if ((map_1[player1.player_y][player1.player_x + 1] != '*' ) &&
                    !(map_1[player1.player_y][player1.player_x] == 'D' && !player1.has_key)) {
                    player1.player_x++;
                }
                break;
            case 'w':
                if (map_1[player1.player_y - 1][player1.player_x] != '*' ) {
                    player1.player_y--;
                }
                break;
            case 's':
                if (map_1[player1.player_y + 1][player1.player_x] != '*' ) {
                    player1.player_y++;
                }
                break;
            case 'i':
                if (map_1[player1.player_y][player1.player_x] == '@') {
                    map_1[player1.player_y][player1.player_x] = ' ';
                    player1.has_key = 1;
                    printf("=========================\n// Voce pegou a chave! //\n========================="); delay(1);
                    
                }
		         else if (map_1[player1.player_y][player1.player_x] == 'D' && player1.has_key) {
                    map_1[player1.player_y][player1.player_x] = '=';
                    printf("=========================\n// Voce abriu a porta! //\n========================="); delay(1);
                    printf("\n");
                    printf("=======================\n// Ande para avancar //\n======================="); delay(2);
				}
				
                break;
        }
    }
  
}

void TUTORIAL(){ 
//função tutorial
//caso jogador queira saber o tutorial	
	system("cls || clear");
	
	printf("TUTORIAL:"); 
	
	printf("\n\n JOGO:\n\n"); 
	printf(" O jogo eh do estilo aventura/puzzle onde o objetivo eh o jogador conseguir passar de tres fases. Em cada fase o jogador deve se\n"); 
	printf(" movimentar para pegar uma chave para abrir a porta fechada.\n"); 
	printf(" O jogador possui os seguintes comando:\n\n"); 
	printf("     W: O jogador movimenta uma unidade para cima;\n\n"); 
	printf("     A: O jogador movimenta uma unidade para esquerda;\n\n"); 
	printf("     S: O jogador movimenta uma unidade para baixo;\n\n");
	printf("     D: O jogador movimenta uma unidade para direita;\n\n");
	printf("     I: O jogador interage com o objeto que esta em cima.\n\n");
	
	printf("\n O jogo possui os seguintes elementos nas fases:\n\n");
	
	printf("     &: Simbolo que representa o jogador.\n\n");
	printf("     *: Simbolo que representa uma parede, o jogador ao se movimentar nao pode passar pela parede.\n\n");
	printf("     @: Simbolo que representa a chave para abrir a porta para finalizar a fase, a porta abre no momento que o jogador interage\n");
	printf("     com a chave.\n\n");
	printf("     D: Simbolo que representa a porta fechada.\n\n");
	printf("     =: Simbolo que representa a porta aberta quando o jogador interage com a chave.\n\n");
	printf("     O: Simbolo que representa um botao que o usuario pode interagir, o botao fica no chao e o jogador deve ficar em cima dele\n");
	printf("     para poder interagir.\n\n");
	printf("     #: Simbolo que representa um espinho. A fase eh reiniciada quando o jogador toca no espinho, caso a fase seja reiniciada\n");
	printf("     tres vezes, o jogo volta para o menu principal.\n\n");
	printf("     >: Simbolo que representa um teletransporte. O teletransporte sempre deve vir em pares, quando o jogador toca em um ele\n");
	printf("     eh transportado para o outro e vice-versa.\n\n");
	printf("     X: Simbolo que representa o monstro nivel 1. O mostro tem um movimento aleatorio, logo, ele movimenta um bloco para\n");
	printf("     cima ou para direita ou para esquerda ou para baixo. O monstro sempre faz uma movimentacao depois do usuario se\n");
	printf("     movimentar ou interagir com um objeto.\n\n");
	printf("     V: Simbolo que representa o monstro nivel 2. O mostro nivel dois tem uma inteligencia de se movimentar na direcao do\n");
	printf("     jogador. O monstro nao precisa saber desviar de obstaculos, ele sempre vai andar em linha reta em direcao do jogador.\n\n");
	
	printf("Deseja retornar ao menu?\n1:Sim   2: Nao"); //escolha de voltar para o menu
			int escolha;
			scanf("%i", &escolha);
			if (escolha == 1){
				MENU();
            }
            else {
            	TUTORIAL();
			}
			

            
}

void MENU(){

	int escolha = 0;
	do{
	system("cls || clear");
	//impressão do menu
	INTRO();
	 printf("\n\n");
    printf("  PPPPPPP    RRRRRRRR     IIIIIIIIIII  NNNN     NN   CCCCCC   EEEEEEEEE  SSSSSSSS    SSSSSSSS\n");
    printf("  PP    PP   RR    RRR       IIII      NN NN    NN  CC        EE         SS          SS      \n");
    printf("  PP    PP   RR    RRR       IIII      NN  NN   NN  CC        EE         SS          SS   \n");
    printf("  PPPPPPP    RRRRRRRR        IIII      NN   NN  NN  CC        EEEEEEEE     SSSSSSSS    SSSSSSS\n");
    printf("  PP         RRR    RR       IIII      NN    NN NN  CC        EE                 SSS        SS\n");
    printf("  PP         RR    RR        IIII      NN     NNNN  CC        EE                 SS          SS\n");
    printf("  PP         RR     RR    IIIIIIIIIII  NN      NNN   CCCCCC   EEEEEEEEE  SSSSSSSS   SSSSSSSS\n");
    printf("\n\n");
    printf("\t\t\t\t\t    SSSSSSSS   CCCCCC  AAAAA    PPPPPPPP   EEEEEEEEE\n");
    printf("\t\t\t\t\t  SS          CC      AA   AA   PP    PP  EE       \n");
    printf("\t\t\t\t\t  ss          CC     AAAAAAAAA  PP    PP  EE       \n");
    printf("\t\t\t\t\t    SSSSSSS   CC     AAAAAAAAA  PPPPPPPP  EEEEEEEE \n");
    printf("\t\t\t\t\t          SS  CC     AA     AA  PP        EE       \n");
    printf("\t\t\t\t\t           SS CC     AA     AA  PP        EE       \n");
    printf("\t\t\t\t\t    SSSSSSSS   CCCCC AA     AA  PP         EEEEEEEEE\n");

//escolha do jogador
	printf("\t\t\t\t\t      1: Jogar\n");
	printf("\t\t\t\t\t      2: Tutorial\n");
	printf("\t\t\t\t\t      3: Sair\n");
	
	scanf("%i", &escolha); 
	if (escolha == 1){ //jogar
		MAP_1();
	}
	if (escolha == 2){ //tutorial
		TUTORIAL();
	}
	if (escolha == 3){ //sair
		printf("Voce viveu eternanente presa ao castelo do monstro sonhando como seria sua vida com o principe...");
		exit (0);
		
	}
}
	while(escolha != 0);
}

int main(){

	srand(time(NULL));
	system("color 06");
	//intro();
  MENU();

}

