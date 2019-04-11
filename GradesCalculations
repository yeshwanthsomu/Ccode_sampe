
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <string.h>

typedef struct{
  char ID[8]; 
  char last_name[30];
  char first_name[30]; 
  double labs[15];
  double hw[15];
  double midterm;
  double final;
}Grade;

  double percentange(Grade *G);
  double overall(Grade *G);


int main(int argc, char *argv[]){
    
  FILE *inptr;
  inptr = fopen(argv[1], "r");
    


  if(inptr == NULL)
    printf("Your file could not be input. Please input your file.\n");
  else{
    char skip[2000];
    fgets(skip, 2000, inptr); 
  


    int status = 0; 
    while(status != EOF){
      Grade G;
        
      status = fscanf(inptr, "%[^,],\"%[^,], %[^\"]\",", G.ID, G.last_name, G.first_name);
      if(status == EOF){
	break;
      }   

   
      for(int i = 0; i < 32; i++){
	char num[5];
	
	if(i < 15){
	  fscanf(inptr, "%[^,],", num);
	  if(num[0]=='-'){
	    G.hw[i]=-1; 
	  }else{
	    G.hw[i]=atof(num);
	  }
	}
	else if(i < 30){
	  fscanf(inptr, "%[^,],", num);
	   if(num[0]=='-'){
	    G.labs[i-15]=-1; 
	  }else{
	    G.labs[i-15]=atof(num);
	  }
	}
	else if(i == 30){
	  fscanf(inptr, "%[^,],", num);
	   if(num[0]=='-'){
	    G.midterm=-1; 
	  }else{
	    G.midterm=atof(num);
	  }
	}
	else{
	  fscanf(inptr, "%[^\n]\n", num);
	   if(num[0]=='-'){
	    G.final=-1; 
	  }else{
	    G.final=atof(num);
	  }
	}
      }
            
      overall(&G);
      percentage(&G);
      printf("\n\n");
    }
  }
  fclose(inptr);
    return 0;
}

double percentage(Grade *G){

    double per, labs_per = 0, hw_per = 0;
    double exam, final;
    
    for(int i = 0; i < 15; i++){
      	   if(G.labs[i]==-1){
	     labs_per += 100; 
	  }else{
	     labs_per += G.labs[i];
	  }
      	   if(G.hw[i]==-1){
	     hw_per += 100; 
	  }else{
	     hw_per += G.hw[i];
	  }
    }
      	   if(G.midterm==-1){
	     exam=100; 
	  }else{
	     exam=G.midterm;
	  }
      	   if(G.final==-1){
	     final=100; 
	  }else{
	     final=G.midterm;
	  }

    
	   per = (labs_per/150*15) + (hw_per/552*40) + (exam*0.2) + (final*0.25);
    printf("The grade of %s %s - (%s) - in this class is %lf%.\n", G.first_name, G.last_name, G.ID, per);
    return per;
}

double overall(Grade *G){
    double total = 0, labs_tot, hw_tot, midterm_tot = G.midterm, final_tot = G.final;
    
    for(int i = 0; i < 15; i++){
        labs_tot = G.labs[i]; 
	hw_tot = G.hw[i];
        if(labs_tot == -1){ 
		labs_tot = 10; 
	}
        if(hw_tot == -1){ 
		hw_tot = 100; 
	}
        total = total + labs_tot+ hw_tot;
    }
    if(midterm_tot == -1) {
      midterm_tot = 100;
    }
    if(final_tot == -1){
      final_tot = 100;
    }

    total = total + midterm_tot + final_tot;
    printf("Student %s %s (%s) has achieved %lf points so far.\n", G.first_name, G.last_name, G.ID, total);
    return total;
}








