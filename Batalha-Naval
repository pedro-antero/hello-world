#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define DIM 10

struct boats_location{
  int x[5];
  int y[5];
  int t,c;
};
//Mostra o jogo
void show_Game(int np,char vet[][DIM]);
//Preenche os vetores com '-'
void fill_Out(char vet[][DIM]);
//inicia o jogo
void play_Game();

void last_play(int x,int y);
//insere a localização dos barcos no struct
void set_Boat_Location(char vet[][DIM], struct boats_location *boat1_size5,struct boats_location *boat1_size4,struct boats_location *boat1_size3,struct boats_location *boat1_size2,struct boats_location *boat2_size2,struct boats_location *boat1_size1,struct boats_location *boat2_size1,struct boats_location *boat3_size1,int n);

//Verifica se na cordenada passada há parte de barco
int is_boat(int x, int y, struct boats_location *boat1_size5,struct boats_location *boat1_size4,struct boats_location *boat1_size3,struct boats_location *boat1_size2,struct boats_location *boat2_size2,struct boats_location *boat1_size1,struct boats_location *boat2_size1,struct boats_location *boat3_size1);

//Mostra a localização dos barcos na tabela player
void set_Boat_Table();

//Verifica se todos os pontos do barco já foram atingidos e muda o simbolo caso verdadeiro
void check_Boat_Situation(char vet[][DIM],struct boats_location *boat1_size5,struct boats_location *boat1_size4,struct boats_location *boat1_size3,struct boats_location *boat1_size2,struct boats_location *boat2_size2,struct boats_location *boat1_size1,struct boats_location *boat2_size1,struct boats_location *boat3_size1);

// substitui as letras da tabela com numeros correspondentes
int replace_y(char);
//Verifica para o bot se a cordenada passada é desconhecida ou se é um barco
int is_unknown(int x, int y,char vet[][DIM]);
//verifica se a coordenada passada esta dentro do intervalo de 0 a 9
int is_out_of_table(int, int);


//verifica se a coordenada passada é acertou um barco ou agua
void shot_validation(int, int,char vet[][DIM],struct boats_location *boat1_size5,struct boats_location *boat1_size4,struct boats_location *boat1_size3,struct boats_location *boat1_size2,struct boats_location *boat2_size2,struct boats_location *boat1_size1,struct boats_location *boat2_size1,struct boats_location *boat3_size1);

//Verifica se há espaço para por um barco em determinada direção
int boat_Location_Validation(int, int, int, struct boats_location *boat1_size5,struct boats_location *boat1_size4,struct boats_location *boat1_size3,struct boats_location *boat1_size2,struct boats_location *boat2_size2,struct boats_location *boat1_size1,struct boats_location *boat2_size1,struct boats_location *boat3_size1);
//Verivica se todos os barcos já foram atigidos
int check_winner(struct boats_location *boat1_size5,struct boats_location *boat1_size4,struct boats_location *boat1_size3,struct boats_location *boat1_size2,struct boats_location *boat2_size2,struct boats_location *boat1_size1,struct boats_location *boat2_size1,struct boats_location *boat3_size1);


struct boats_location player_boat1_size5;
struct boats_location player_boat1_size4;
struct boats_location player_boat1_size3;
struct boats_location player_boat1_size2;
struct boats_location player_boat2_size2;
struct boats_location player_boat1_size1;
struct boats_location player_boat2_size1;
struct boats_location player_boat3_size1;

struct boats_location bot_boat1_size5;
struct boats_location bot_boat1_size4;
struct boats_location bot_boat1_size3;
struct boats_location bot_boat1_size2;
struct boats_location bot_boat2_size2;
struct boats_location bot_boat1_size1;
struct boats_location bot_boat2_size1;
struct boats_location bot_boat3_size1;

char player[DIM][DIM];
char bot[DIM][DIM];

int main(void) {
  int i;

  fill_Out(player);
  fill_Out(bot);

  set_Boat_Location(player, &player_boat1_size5, &player_boat1_size4,&player_boat1_size3,&player_boat1_size2,&player_boat2_size2,&player_boat1_size1,&player_boat2_size1,&player_boat3_size1,0);
  set_Boat_Table();       
            
  set_Boat_Location(bot, &bot_boat1_size5, &bot_boat1_size4,&bot_boat1_size3,&bot_boat1_size2,&bot_boat2_size2,&bot_boat1_size1,&bot_boat2_size1,&bot_boat3_size1,1);

  show_Game(1,player);
  show_Game(2,bot);

  play_Game();

  return 0;
}

void fill_Out(char vet[][DIM]){
  for(int i=0;i<10;i++){
    for(int j=0;j<10;j++){
      vet[i][j] = '-';
    }
  }
}

void show_Game(int np,char vet[][DIM]){
  if(np == 1){
    printf("\nPlayer Table:\n\n");
  }else{
    printf("\nBot Table:\n\n");
  }
  printf("");
  printf("   A B C D E F G H I J\n");
  for(int i=0;i<10;i++){
    printf("%-2d",i+1);
    printf(" ");
    for(int j=0;j<10;j++){
      printf("%c",vet[i][j]);
      printf(" ");
    }
    printf("\n");  
  }
  printf("\n");
}

void set_Boat_Location(char vet[][DIM],struct boats_location *boat1_size5,struct boats_location *boat1_size4,struct boats_location *boat1_size3,struct boats_location *boat1_size2,struct boats_location *boat2_size2,struct boats_location *boat1_size1,struct boats_location *boat2_size1,struct boats_location *boat3_size1,int n){

  srand(time(NULL)+n);
  int x,y,sentido,position;

  //Barco de 5 espaço
  
    x = 1+rand()%8;
    y = 1+rand()%8;
  
    sentido = 1+rand()%4;
    switch(sentido){
      case 1:
        (*boat1_size5).x[0] = x;
        (*boat1_size5).y[0] = y;
        (*boat1_size5).x[1] = x+1;
        (*boat1_size5).y[1] = y;
        (*boat1_size5).x[2] = x-1;
        (*boat1_size5).y[2] = y;
        (*boat1_size5).x[3] = x-1;
        (*boat1_size5).y[3] = y+1;
        (*boat1_size5).x[4] = x-1;
        (*boat1_size5).y[4] = y-1;
        (*boat1_size5).t=5;
        (*boat1_size5).c=0;
        
        break;
      case 2:
        (*boat1_size5).x[0] = x;
        (*boat1_size5).y[0] = y;
        (*boat1_size5).x[1] = x;
        (*boat1_size5).y[1] = y-1;
        (*boat1_size5).x[2] = x;
        (*boat1_size5).y[2] = y+1;
        (*boat1_size5).x[3] = x-1;
        (*boat1_size5).y[3] = y+1;
        (*boat1_size5).x[4] = x+1;
        (*boat1_size5).y[4] = y+1;
        (*boat1_size5).t=5;
        (*boat1_size5).c=0;
        
        break;
      case 3:
        (*boat1_size5).x[0] = x;
        (*boat1_size5).y[0] = y;
        (*boat1_size5).x[1] = x-1;
        (*boat1_size5).y[1] = y;
        (*boat1_size5).x[2] = x+1;
        (*boat1_size5).y[2] = y;
        (*boat1_size5).x[3] = x+1;
        (*boat1_size5).y[3] = y-1;
        (*boat1_size5).x[4] = x+1;
        (*boat1_size5).y[4] = y+1;
        (*boat1_size5).t=5;
        (*boat1_size5).c=0;
        
        break;
      case 4:
        (*boat1_size5).x[0] = x;
        (*boat1_size5).y[0] = y;
        (*boat1_size5).x[1] = x;
        (*boat1_size5).y[1] = y+1;
        (*boat1_size5).x[2] = x;
        (*boat1_size5).y[2] = y-1;
        (*boat1_size5).x[3] = x+1;
        (*boat1_size5).y[3] = y-1;
        (*boat1_size5).x[4] = x-1;
        (*boat1_size5).y[4] = y-1;
        (*boat1_size5).t=5;
        (*boat1_size5).c=0;
        
        break;
    }
  
  //Barco de 4 espaços

  x = rand()%10;
  y = rand()%10;
  position = boat_Location_Validation(4,x,y, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1);
  while(position==0){
    x = rand()%10;
    y = rand()%10;
    position = boat_Location_Validation(4,x,y, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1);
  }
  switch(position){
    case 1:
      (*boat1_size4).x[0]=x;
      (*boat1_size4).y[0]=y;
      (*boat1_size4).x[1]=x;
      (*boat1_size4).y[1]=y-1;
      (*boat1_size4).x[2]=x;
      (*boat1_size4).y[2]=y-2;
      (*boat1_size4).x[3]=x;
      (*boat1_size4).y[3]=y-3;
      (*boat1_size4).t=4;
      (*boat1_size4).c=0;
      
      break;
    case 2:
      (*boat1_size4).x[0]=x;
      (*boat1_size4).y[0]=y;
      (*boat1_size4).x[1]=x-1;
      (*boat1_size4).y[1]=y;
      (*boat1_size4).x[2]=x-2;
      (*boat1_size4).y[2]=y;
      (*boat1_size4).x[3]=x-3;
      (*boat1_size4).y[3]=y;
      (*boat1_size4).t=4;
      (*boat1_size4).c=0;
      
      break;
    case 3:
      (*boat1_size4).x[0]=x;
      (*boat1_size4).y[0]=y;
      (*boat1_size4).x[1]=x;
      (*boat1_size4).y[1]=y+1;
      (*boat1_size4).x[2]=x;
      (*boat1_size4).y[2]=y+2;
      (*boat1_size4).x[3]=x;
      (*boat1_size4).y[3]=y+3;
      (*boat1_size4).t=4;
      (*boat1_size4).c=0;
      
      break;
    case 4:
      (*boat1_size4).x[0]=x;
      (*boat1_size4).y[0]=y;
      (*boat1_size4).x[1]=x+1;
      (*boat1_size4).y[1]=y;
      (*boat1_size4).x[2]=x+2;
      (*boat1_size4).y[2]=y;
      (*boat1_size4).x[3]=x+3;
      (*boat1_size4).y[3]=y;
      (*boat1_size4).t=4;
      (*boat1_size4).c=0;
      
      break;
  }

   //Barco de 3 espaços

  x = rand()%10;
  y = rand()%10;
  position = boat_Location_Validation(3,x,y, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1);
  while(position==0){
    x = rand()%10;
    y = rand()%10;
    position = boat_Location_Validation(3,x,y, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1);
  }
  switch(position){
    case 1:
      (*boat1_size3).x[0]=x;
      (*boat1_size3).y[0]=y;
      (*boat1_size3).x[1]=x;
      (*boat1_size3).y[1]=y-1;
      (*boat1_size3).x[2]=x;
      (*boat1_size3).y[2]=y-2;
      (*boat1_size3).t=3;
      (*boat1_size3).c=0;
      
      break;
    case 2:
      (*boat1_size3).x[0]=x;
      (*boat1_size3).y[0]=y;
      (*boat1_size3).x[1]=x-1;
      (*boat1_size3).y[1]=y;
      (*boat1_size3).x[2]=x-2;
      (*boat1_size3).y[2]=y;
      (*boat1_size3).t=3;
      (*boat1_size3).c=0;
      
      break;
    case 3:
      (*boat1_size3).x[0]=x;
      (*boat1_size3).y[0]=y;
      (*boat1_size3).x[1]=x;
      (*boat1_size3).y[1]=y+1;
      (*boat1_size3).x[2]=x;
      (*boat1_size3).y[2]=y+2;
      (*boat1_size3).t=3;
      (*boat1_size3).c=0;
      
      break;
    case 4:
      (*boat1_size3).x[0]=x;
      (*boat1_size3).y[0]=y;
      (*boat1_size3).x[1]=x+1;
      (*boat1_size3).y[1]=y;
      (*boat1_size3).x[2]=x+2;
      (*boat1_size3).y[2]=y;
      (*boat1_size3).t=3;
      (*boat1_size3).c=0;
      
      break;
  }

  //Barco de 2 espaços

  x = rand()%10;
  y = rand()%10;
  position = boat_Location_Validation(2,x,y, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1);
  while(position==0){
    x = rand()%10;
    y = rand()%10;
    position = boat_Location_Validation(2,x,y, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1);
  }
  switch(position){
    case 1:
      (*boat1_size2).x[0]=x;
      (*boat1_size2).y[0]=y;
      (*boat1_size2).x[1]=x;
      (*boat1_size2).y[1]=y-1;
      (*boat1_size2).t=2;
      (*boat1_size2).c=0;
      
      break;
    case 2:
      (*boat1_size2).x[0]=x;
      (*boat1_size2).y[0]=y;
      (*boat1_size2).x[1]=x-1;
      (*boat1_size2).y[1]=y;
      (*boat1_size2).t=2;
      (*boat1_size2).c=0;
      
      break;
    case 3:
      (*boat1_size2).x[0]=x;
      (*boat1_size2).y[0]=y;
      (*boat1_size2).x[1]=x;
      (*boat1_size2).y[1]=y+1;
      (*boat1_size2).t=2;
      (*boat1_size2).c=0;
      
      break;
    case 4:
      (*boat1_size2).x[0]=x;
      (*boat1_size2).y[0]=y;
      (*boat1_size2).x[1]=x+1;
      (*boat1_size2).y[1]=y;
      (*boat1_size2).t=2;
      (*boat1_size2).c=0;
      
      break;
  }

  x = rand()%10;
  y = rand()%10;
  position = boat_Location_Validation(2,x,y, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1);
  while(position==0){
    x = rand()%10;
    y = rand()%10;
    position = boat_Location_Validation(2,x,y, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1);
  }
  switch(position){
    case 1:
      (*boat2_size2).x[0]=x;
      (*boat2_size2).y[0]=y;
      (*boat2_size2).x[1]=x;
      (*boat2_size2).y[1]=y-1;
      (*boat2_size2).t=2;
      (*boat2_size2).c=0;
      
      break;
    case 2:
      (*boat2_size2).x[0]=x;
      (*boat2_size2).y[0]=y;
      (*boat2_size2).x[1]=x-1;
      (*boat2_size2).y[1]=y;
      (*boat2_size2).t=2;
      (*boat2_size2).c=0;
      
      break;
    case 3:
      (*boat2_size2).x[0]=x;
      (*boat2_size2).y[0]=y;
      (*boat2_size2).x[1]=x;
      (*boat2_size2).y[1]=y+1;
      (*boat2_size2).t=2;
      (*boat2_size2).c=0;
      
      break;
    case 4:
      (*boat2_size2).x[0]=x;
      (*boat2_size2).y[0]=y;
      (*boat2_size2).x[1]=x+1;
      (*boat2_size2).y[1]=y;
      (*boat2_size2).t=2;
      (*boat2_size2).c=0;
      
      break;
  }

  //Barco de 1 espaço
  x = rand()%10;
  y = rand()%10;
  int place = is_boat(x,y, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1);
  while(place!=0){
    x = rand()%10;
    y = rand()%10;
    place = is_boat(x,y, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1);
  }
  (*boat1_size1).x[0]=x;
  (*boat1_size1).y[0]=y;
  (*boat1_size1).t=1;
  (*boat1_size1).c=0;
  

  x = rand()%10;
  y = rand()%10;
  place = is_boat(x,y, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1);
  while(place!=0){
    x = rand()%10;
    y = rand()%10;
    place = is_boat(x,y, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1);
  }
  (*boat2_size1).x[0]=x;
  (*boat2_size1).y[0]=y;
  (*boat2_size1).t=1;
  (*boat2_size1).c=0;
  

  x = rand()%10;
  y = rand()%10;
  place = is_boat(x,y, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1);
  while(place!=0){
    x = rand()%10;
    y = rand()%10;
    place = is_boat(x,y, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1);
  }
  (*boat3_size1).x[0]=x;
  (*boat3_size1).y[0]=y;
  (*boat3_size1).t=1;
  (*boat3_size1).c=0;

}
void set_Boat_Table(){
  int a,b;
  //boat size 1
  a = player_boat1_size1.x[0];
  b = player_boat1_size1.y[0];
  player[a][b] = '#';
  
  a = player_boat2_size1.x[0];
  b = player_boat2_size1.y[0];
  player[a][b] = '#';
  
  a = player_boat3_size1.x[0];
  b = player_boat3_size1.y[0];
  player[a][b] = '#';

  //boat size 2
  for(int i =0;i<2;i++){
    a = player_boat1_size2.x[i];
    b = player_boat1_size2.y[i];
    player[a][b] = '#';
  }
  for(int i =0;i<2;i++){
    a = player_boat2_size2.x[i];
    b = player_boat2_size2.y[i];
    player[a][b] = '#';
  }

  //boat size 3
  for(int i =0;i<3;i++){
    a = player_boat1_size3.x[i];
    b = player_boat1_size3.y[i];
    player[a][b] = '#';
  }
  //boat size 4
  for(int i =0;i<4;i++){
    a = player_boat1_size4.x[i];
    b = player_boat1_size4.y[i];
    player[a][b] = '#';
  }
  //boat size 5
  for(int i =0;i<5;i++){
    a = player_boat1_size5.x[i];
    b = player_boat1_size5.y[i];
    player[a][b] = '#';
  }
  
}

int boat_Location_Validation(int size, int x, int y, struct boats_location *boat1_size5,struct boats_location *boat1_size4,struct boats_location *boat1_size3,struct boats_location *boat1_size2,struct boats_location *boat2_size2,struct boats_location *boat1_size1,struct boats_location *boat2_size1,struct boats_location *boat3_size1){
  int position,cont;
  int up=0,down=0,right=0,left=0;
  for(int i=1;i<size;i++){
    if(y-i>=0){
      left++;
    }
    if(y+i<=9){
      right++;
    }
    if(x-i>=0){
      up++;
    }
    if(x+i<=9){
      down++;
    }
  }
  if(left==size-1){
    cont = 0;
    for(int i=0;i<size;i++){
      if(is_boat(x,y-i, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1) == 0){
        cont++; 
      }
    }
    if(cont==size){
      return position = 1;
    }
  }
  else if(up==size-1){
    cont = 0;
    for(int i=0;i<size;i++){
      if(is_boat(x-i,y, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1) == 0){
        cont++; 
      }
    }
    if(cont==size){
      return position = 2;
    }
  }
  else if(right==size-1){
    cont = 0;
    for(int i=0;i<size;i++){
      if(is_boat(x,y+i, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1) == 0){
        cont++; 
      }
    }
    if(cont==size){
      return position = 3;
    }
  }
  else if(down==size-1){
    cont = 0;
    for(int i=0;i<size;i++){
      if(is_boat(x+i,y, boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1) == 0){
        cont++; 
      }
    }
    if(cont==size){
      return position = 4;
    }
  }
  else{
    return position = 0;
  }
  return 0;
}

int is_boat(int x, int y, struct boats_location *boat1_size5,struct boats_location *boat1_size4,struct boats_location *boat1_size3,struct boats_location *boat1_size2,struct boats_location *boat2_size2,struct boats_location *boat1_size1,struct boats_location *boat2_size1,struct boats_location *boat3_size1 ){
  int cont = 0;
  for(int i = 0; i<5;i++){
    if((*boat1_size5).x[i]==x && (*boat1_size5).y[i]==y){
      cont=15;
    }
  }
  for(int i = 0; i<4;i++){
    if((*boat1_size4).x[i]==x && (*boat1_size4).y[i]==y){
      cont=14;
    }
  }
  for(int i = 0; i<3;i++){
    if((*boat1_size3).x[i]==x && (*boat1_size3).y[i]==y){
      cont=13;
    }
  }
  for(int i = 0; i<2;i++){
    if((*boat1_size2).x[i]==x && (*boat1_size2).y[i]==y){
      cont=12;
    }
  }
  for(int i = 0; i<2;i++){
    if((*boat2_size2).x[i]==x && (*boat2_size2).y[i]==y){
      cont=22;
    }
  }
  if((*boat1_size1).x[0]==x && (*boat1_size1).y[0]==y){
    cont=11;
  }
  if((*boat2_size1).x[0]==x && (*boat2_size1).y[0]==y){
    cont=21;
  }
  if((*boat3_size1).x[0]==x && (*boat3_size1).y[0]==y){
    cont=31;
  }
  return cont;
}

void play_Game(){
  srand(time(NULL));
  char coluna;
  int linha;
  int a,b,winner=0,cont = 0;
  int prev_A,prev_B,x,y, smartPlay = 0;

  while(winner==0){

    printf("\nDigite a linha alvo:");
    scanf("\n%d",&linha);
    printf("\nDigite a coluna alvo:");
    scanf("\n%c",&coluna);
    
    a=linha-1;
    b=replace_y(coluna);

    while((linha<0 || linha>10) || (coluna<65 || coluna >74)||bot[a][b]!='-'){
      printf("Coordenada inválida, insira de acordo com a tabela\n");
      printf("Digite a linha alvo:");
      scanf("\n%d",&linha);
      printf("Digite a coluna alvo:");
      scanf("\n\n%c",&coluna);
      a=linha-1;
      b=replace_y(coluna);
    }

    shot_validation(a,b,bot,&bot_boat1_size5, &bot_boat1_size4,&bot_boat1_size3,&bot_boat1_size2,&bot_boat2_size2,&bot_boat1_size1,&bot_boat2_size1,&bot_boat3_size1);

    check_Boat_Situation(bot,&bot_boat1_size5, &bot_boat1_size4,&bot_boat1_size3,&bot_boat1_size2,&bot_boat2_size2,&bot_boat1_size1,&bot_boat2_size1,&bot_boat3_size1);

    show_Game(1,player);
    printf("\nPlayer ultima jogada: ");
    last_play(a,b);
    //show_Game(2,bot);

    if(check_winner(&bot_boat1_size5, &bot_boat1_size4,&bot_boat1_size3,&bot_boat1_size2,&bot_boat2_size2,&bot_boat1_size1,&bot_boat2_size1,&bot_boat3_size1)==1){
      winner=1;
      printf("Player é o vencedor!!\n\n");
      break; 
    }

    //BOT Time
    if(smartPlay==1){
      x = prev_A;
      y = prev_B;
      a=(-1)+rand()%3;
      b=(-1)+rand()%3;
      while(a==0 && b==0){
        a=(-1)+rand()%3;
        b=(-1)+rand()%3;
      }
      while(is_out_of_table(prev_A+a,prev_B+b)==1){
        a=(-1)+rand()%3;
        b=(-1)+rand()%3;
      }
      prev_A+=a;
      prev_B+=b;
      while(is_unknown(prev_A,prev_B,player)==0){
        prev_A=rand()%10;
        prev_B=rand()%10;
        
      }
     
      shot_validation(prev_A,prev_B,player,&player_boat1_size5, &player_boat1_size4,&player_boat1_size3,&player_boat1_size2,&player_boat2_size2,&player_boat1_size1,&player_boat2_size1,&player_boat3_size1);

      if(is_boat(prev_A,prev_B,&player_boat1_size5, &player_boat1_size4,&player_boat1_size3,&player_boat1_size2,&player_boat2_size2,&player_boat1_size1,&player_boat2_size1,&player_boat3_size1) > 0){
      
        smartPlay = 1;
      }else{
        smartPlay = 0;
      }

      check_Boat_Situation(player,&player_boat1_size5, &player_boat1_size4,&player_boat1_size3,&player_boat1_size2,&player_boat2_size2,&player_boat1_size1,&player_boat2_size1,&player_boat3_size1);

      show_Game(1,player);
      show_Game(2,bot);
      printf("\nBot ultima jogada: ");
      last_play(prev_A,prev_B);

      if(check_winner(&player_boat1_size5, &player_boat1_size4,&player_boat1_size3,&player_boat1_size2,&player_boat2_size2,&player_boat1_size1,&player_boat2_size1,&player_boat3_size1)==1){
        winner=1;
        printf("BOT é o vencedor!!\n\n");
        break; 
      }

    }else{
      a=rand()%10;
      b=rand()%10;
      while(is_unknown(a,b,player)==0){
        a=rand()%10;
        b=rand()%10;
      }
      shot_validation(a,b,player,&player_boat1_size5, &player_boat1_size4,&player_boat1_size3,&player_boat1_size2,&player_boat2_size2,&player_boat1_size1,&player_boat2_size1,&player_boat3_size1);

      if(is_boat(a,b,&player_boat1_size5, &player_boat1_size4,&player_boat1_size3,&player_boat1_size2,&player_boat2_size2,&player_boat1_size1,&player_boat2_size1,&player_boat3_size1) > 0){
        prev_A = a;
        prev_B = b;
        smartPlay = 1;
      }

      check_Boat_Situation(player,&player_boat1_size5, &player_boat1_size4,&player_boat1_size3,&player_boat1_size2,&player_boat2_size2,&player_boat1_size1,&player_boat2_size1,&player_boat3_size1);

      show_Game(1,player);
      show_Game(2,bot);
      printf("\nBot ultima jogada: ");
      last_play(a,b);

      if(check_winner(&player_boat1_size5, &player_boat1_size4,&player_boat1_size3,&player_boat1_size2,&player_boat2_size2,&player_boat1_size1,&player_boat2_size1,&player_boat3_size1)==1){
        winner=1;
        printf("BOT é o vencedor!!\n\n");
        break; 
      }
    }
  }
}

int is_unknown(int x, int y,char vet[][DIM]){
  if(vet[x][y]=='-' || vet[x][y]=='#'){
    return 1;
  }else{
    return 0;
  }
  return 0;
}

int replace_y(char coluna){
  int b;
  switch(coluna){
    case 'A':
      b = 0;
      break;
    case 'B':
      b = 1;
      break;
    case 'C':
      b = 2;
      break;
    case 'D':
      b = 3;
      break;
    case 'E':
      b = 4;
      break;
    case 'F':
      b = 5;
      break;
    case 'G':
      b = 6;
      break;
    case 'H':
      b = 7;
      break;
    case 'I':
      b = 8;
      break;
    case 'J':
      b = 9;
      break;  
  }
  return b;
}

void shot_validation(int x, int y,char vet[][DIM], struct boats_location *boat1_size5,struct boats_location *boat1_size4,struct boats_location *boat1_size3,struct boats_location *boat1_size2,struct boats_location *boat2_size2,struct boats_location *boat1_size1,struct boats_location *boat2_size1,struct boats_location *boat3_size1){

  int a = is_boat(x,y,boat1_size5, boat1_size4, boat1_size3, boat1_size2, boat2_size2, boat1_size1, boat2_size1,boat3_size1);
  if(a>0){
    switch(a){
      case 15:
        (*boat1_size5).c++;
        vet[x][y] = 'P';
        break;
      case 14:
        (*boat1_size4).c++;
        vet[x][y] = 'P';
        break;
      case 13:
        (*boat1_size3).c++;
        vet[x][y] = 'P';
        break;
      case 12:
        (*boat1_size2).c++;
        vet[x][y] = 'P';
        break;
      case 22:
        (*boat2_size2).c++;
        vet[x][y] = 'P';
        break;
      case 11:
        (*boat1_size1).c++;
        vet[x][y] = 'P';
        break;
      case 21:
        (*boat2_size1).c++;
        vet[x][y] = 'P';
        break;
      case 31:
        (*boat3_size1).c++;
        vet[x][y] = 'P';
        break;
    }
  }else{
    vet[x][y]='A';
  }

}

void check_Boat_Situation(char vet[][DIM], struct boats_location *boat1_size5,struct boats_location *boat1_size4,struct boats_location *boat1_size3,struct boats_location *boat1_size2,struct boats_location *boat2_size2,struct boats_location *boat1_size1,struct boats_location *boat2_size1,struct boats_location *boat3_size1){
  int a,b;
  if((*boat1_size5).c == (*boat1_size5).t){
    for(int i=0;i<5;i++){
      a=(*boat1_size5).x[i];
      b=(*boat1_size5).y[i];
      vet[a][b] = 'X';
    }
  }
  if((*boat1_size4).c == (*boat1_size4).t){
    for(int i=0;i<4;i++){
      a=(*boat1_size4).x[i];
      b=(*boat1_size4).y[i];
      vet[a][b] = 'X';
    }
  }
  if((*boat1_size3).c == (*boat1_size3).t){
    for(int i=0;i<3;i++){
      a=(*boat1_size3).x[i];
      b=(*boat1_size3).y[i];
      vet[a][b] = 'X';
    }
  }
  if((*boat1_size2).c == (*boat1_size2).t){
    for(int i=0;i<2;i++){
      a=(*boat1_size2).x[i];
      b=(*boat1_size2).y[i];
      vet[a][b] = 'X';
    }
  }
  if((*boat2_size2).c == (*boat2_size2).t){
    for(int i=0;i<2;i++){
      a=(*boat2_size2).x[i];
      b=(*boat2_size2).y[i];
      vet[a][b] = 'X';
    }
  }
  if((*boat1_size1).c == (*boat1_size1).t){
    a=(*boat1_size1).x[0];
    b=(*boat1_size1).y[0];
    vet[a][b] = 'X';
  }
  if((*boat2_size1).c == (*boat2_size1).t){
    a=(*boat2_size1).x[0];
    b=(*boat2_size1).y[0];
    vet[a][b] = 'X';
  }
  if((*boat3_size1).c == (*boat3_size1).t){
    a=(*boat3_size1).x[0];
    b=(*boat3_size1).y[0];
    vet[a][b] = 'X';
  }
}

int check_winner(struct boats_location *boat1_size5,struct boats_location *boat1_size4,struct boats_location *boat1_size3,struct boats_location *boat1_size2,struct boats_location *boat2_size2,struct boats_location *boat1_size1,struct boats_location *boat2_size1,struct boats_location *boat3_size1){

  if( ((*boat1_size5).c==(*boat1_size5).t) && ((*boat1_size4).c==(*boat1_size4).t) && ((*boat1_size3).c==(*boat1_size3).t) && ((*boat1_size2).c==(*boat1_size2).t) && ((*boat2_size2).c==(*boat2_size2).t) && ((*boat1_size1).c==(*boat1_size1).t) && ((*boat2_size1).c==(*boat2_size1).t) && ((*boat3_size1).c==(*boat3_size1).t)){

    return 1;
  }else{
    return 0;
  }
  return 0;
}

int is_out_of_table(int x, int y){
  if((x<0 || x >9)||(y<0 || y >9)){
    return 1;
  }else{
    return 0;
  }
  return 0;
}

void last_play(int x,int y){
  switch(y){
    case 0:
      printf("\nJogada: %dA\n",x+1);
      break;
    case 1:
      printf("\nJogada: %dB\n",x+1);
    break;
    case 2:
      printf("\nJogada: %dC\n",x+1);
    break;
    case 3:
      printf("\nJogada: %dD\n",x+1);
    break;
    case 4:
      printf("\nJogada: %dE\n",x+1);
    break;
    case 5:
      printf("\nJogada: %dF\n",x+1);
    break;
    case 6:
      printf("\nJogada: %dG\n",x+1);
    break;
    case 7:
      printf("\nJogada: %dH\n",x+1);
    break;
    case 8:
      printf("\nJogada: %dI\n",x+1);
    break;
    case 9:
      printf("\nJogada: %dJ\n",x+1);
    break;
  }
}
