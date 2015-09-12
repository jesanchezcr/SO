# SO
#include <stdio.h>
#include <stdlib.h>

struct Estudiante{
char nombre[30];   
unsigned int edad;    
double peso;
float estatura;
char genero[20];//M o F
unsigned long int cedula;
short int num_materias;
int codigo;
};

void GuardarDatos(struct Estudiante *p){
  size_t r;
  FILE *ap;
  ap = fopen("datos.txt","w+");
  if(ap==NULL){
    perror("Error al abrir el archivo");
    exit(-1);
  } //handle error
  r = fwrite(p,sizeof(struct Estudiante),1,ap);
  if(r!=1){
    perror("Error al escribir el archivo");
    exit(-1);
  }
  r=fclose(ap);
  if(r!=0){
    perror("Error al cerrar el archivo");
    exit(-1);
  }
}
void CargarDatos(struct Estudiante *p){
printf("Ingrese su nombre : "); 
scanf("%s",(p->nombre));
printf("Ingrese su edad : "); 
scanf("%u",&(p->edad));
printf("Ingrese su peso : "); 
scanf("%lf",&(p->peso));
printf("Ingrese su estatura : "); 
scanf("%f",&(p->estatura));
printf("Ingrese su genero : "); 
scanf("%s",(p->genero));
printf("Ingrese su cedula : "); 
scanf("%ld",&(p->cedula));
printf("Ingrese su numero de materias : "); 
scanf("%hd",&(p->num_materias));
printf("Ingrese su codigo : "); 
scanf("%d",&(p->codigo));
};

void MostrarDatos(struct Estudiante *p){
printf("nombre: %s \nedad: %u\npeso: %lf\nestatura: %f\ngenero: %s\ncedula: %ld\nnum de materias %hd\ncodigo %d \n\n",
p->nombre,p->edad,p->peso,p->estatura,p->genero,p->cedula,p->num_materias,p->codigo);
};

int main() {
struct Estudiante *p;
p = malloc(sizeof(struct Estudiante));
CargarDatos(p);
MostrarDatos(p);
 GuardarDatos(p);
free(p);
return 0;
}
