# Menu1
#include<stdio.h>
#include<windows.h>
#include<time.h>

void menu();
char orden(int);
int cuenta();

int u=0,d=0,t=0,c=0;
FILE *archivo,*cu;
char * caracteres = (char*)malloc(100 * sizeof(char));

int main()
{
    int x;
    char op;
    while(1){
    menu();
    scanf("%d",&x);
    if(x==5){
            system("cls");
            cuenta();
            u=d=t=c=0;
            system("pause");
            system("cls");
            }
            else{
    op=orden(x);
    system("cls");
    }
    if(op!='s'&& op!='S') {
            cuenta();
            u=d=t=c=0;
            system("pause");
            system("cls");
    }
    }
    return 0;
}


char orden(int x){
    char op;
    if(1==x) u++;
    if(2==x) d++;
    if(3==x) t++;
    if(4==x) c++;
    if(x<5){
    printf("Articulo agregado\n");
    printf("Desea agregar otra cosa? S/N \n");
    fflush(stdin);
    scanf("%c",&op);
    return op;
    }
}

void menu(){
archivo=fopen("menu.txt","r");
    while (feof(archivo) == 0)
 	{
 		fgets(caracteres,100,archivo);
 		printf("%s",caracteres);
 	}
    fclose(archivo);
    printf("\n");

}

int cuenta(){
struct tm *outtime;
time_t hora;
time(&hora);
outtime = localtime(&hora);
cu=fopen("cuenta.txt","a");
printf("%s\n", asctime(outtime));
fprintf(cu,"%s",asctime(outtime));
printf("Cuenta: \n %d Tortas \n %d Refrescos \n %d Hot Dog \n %d Agua Natural\nTotal: %d \n",u,d,t,c,u*60+d*15+t*30+c*12);
fprintf(cu,"Cuenta: \n %d Tortas \n %d Refrescos \n %d Hot Dog \n %d Agua Natural\nTotal: %d \n\n",u,d,t,c,u*60+d*15+t*30+c*12);
fclose(cu);
}
