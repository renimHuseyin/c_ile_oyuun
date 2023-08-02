// c dili ile oyun
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <conio.h>
#include<locale.h>
#include<unistd.h>

void canfonk(int can)
{
	if(can==2)
	{
		system("COLOR 4");
		printf("Muhafıza yakalndığınız için başa döndünüz. Kalan canınız 2'dir.");
		sleep(1);
		system("cls");
		system("COLOR 0D");
	}
	else if(can==1)
	{
		    system("COLOR 4");
			printf("Muhafıza yakalndığınız için başa döndünüz. Kalan canınız 1'dir.");
			sleep(1);
			system("cls");
		    system("COLOR 0D");
	}
}


//not: Avcı=5  Muhafız=2  Elmas=3
int main() {
	setlocale(LC_ALL,"turkish");
	int i,j,matris[10][10];
	system("COLOR D");
	srand(time(0));
	for(i=0;i<10;i++)
	{
		for(j=0;j<10;j++)
		{
			if(i==2 && j==4)
			{
				matris[i][j]=5;
		    }
		else
			matris[i][j]=0;
        }
    }
    //elmasları yerleştirme
    int x,m,n,a,b;
    int dizia[5];
    int dizib[5];
    for(x=0;x<5;x++)
    {
    	a=rand()%10 ;
     	b=rand()%10 ;
	
     if(matris[a][b]!=5 && matris[a][b]!=3)
     {
     dizia[x]=a;
     dizib[x]=b;
     matris[a][b]=3;
	 }
	 else
	 {
	 	x--;
	 }
   }
   //muhafızları yerleştirme
   int y;
   int dizim[5];
   int dizin[5];
   for(y=0;y<5;)
  
    {
	
   	m=rand()%10 ;
   	n=rand()%10 ;
   	if(matris[m][n]!=3 && matris[m][n]!=5 && matris[m][n]!=2)
   	{ 
    if(m==dizia[y]-1 && n==dizib[y]-1)
   	{
   		dizim[y]=m;
   		dizin[y]=n;
		matris[m][n]=2;	
		y++;
	}
	else if(m==dizia[y]-1 && n==dizib[y])
   	{
      	dizim[y]=m;
   		dizin[y]=n;	
   		matris[m][n]=2;
   		y++;
	}
	else if(m==dizia[y]-1 && n==dizib[y]+1)
   	{
   		dizim[y]=m;
   		dizin[y]=n;
		matris[m][n]=2;
		y++;
	}
	else if(m==dizia[y] && n==dizib[y]-1)
   	{
   		dizim[y]=m;
   		dizin[y]=n;	
   		matris[m][n]=2;
   		y++;
	}
	else if(m==dizia[y] && n==dizib[y]+1)
   	{
   		dizim[y]=m;
   		dizin[y]=n;
		matris[m][n]=2;
	  	y++;
	}
	else if(m==dizia[y]+1 && n==dizib[y]-1)
   	{
   		dizim[y]=m;
   		dizin[y]=n;	
   		matris[m][n]=2;
   	    y++;
	}
	else if(m==dizia[y]+1 && n==dizib[y])
   	{
   		dizim[y]=m;
   		dizin[y]=n;	
   		matris[m][n]=2;
   	    y++;
	}
	else if(m==dizia[y]+1 && n==dizib[y]+1)
   	{
   		dizim[y]=m;
   		dizin[y]=n;
		matris[m][n]=2;	
	    y++;
	}
    }
    }
    int can=3,e=2,d=4;
    int satira=2,sutuna=4;
    int p;
    etiket: 
    printf("HAZİNE AVCISI\n");
    printf(" Avcı=5\n");
    printf("Hareket Tuşları:\n");
    printf("Yukarı:w - Aşağı:s - Sağa:a - Sola:d\n");
    
    //gizleme
   int g,h;
   for(g=0;g<10;g++)
   {
   	for(h=0;h<10;h++)
   	{
   		if(matris[g][h]==3 || matris[g][h]==2 || matris[g][h]==0)
   		{
   			printf(" _   ",matris[g][h]);
		}
		else  
		{
			printf(" %d   ",matris[g][h]);
		}
	}
   	printf("\n\n");
   }
    
/*	for(i=0;i<10;i++)
	{
		for(j=0;j<10;j++)
		{
			printf(" %d   ",matris[i][j]);
	    }
		printf("\n\n");
	}*/
	
	   char durum[10]="TEBRİKLER";
	   char duruma[11]="KAZANDINIZ";
	   int f;
	   if(matris[dizia[0]][dizib[0]]==0 && matris[dizia[1]][dizib[1]]==0 && matris[dizia[2]][dizib[2]]==0 && matris[dizia[3]][dizib[3]]==0 && matris[dizia[4]][dizib[4]]==0 )
        {
        system("cls");
        system("COLOR 20");
             printf("*************************************************************");
		for(f=0;f<9;f++)
		{
			printf("\n*                            %c                              *",durum[f]);
			sleep(1);		
		}
		printf("\n*                                                           *");
		for(f=0;f<10;f++)
		{
		    printf("\n*                            %c                              *",duruma[f]);
		    sleep(1);	
		}
	    	printf("\n*                            :)                             *\n");
	    	printf("*************************************************************");
	    	printf("\n\n\n\n\n");
		return 0;
        }
	
	//mesafe tanımlama
    int m11,m12,m21,m22,m31,m32,m41,m42,m51,m52;
    m11=abs(satira-dizia[0]);
    m12=abs(sutuna-dizib[0]);
    m21=abs(satira-dizia[1]);
    m22=abs(sutuna-dizib[1]);
    m31=abs(satira-dizia[2]);
    m32=abs(sutuna-dizib[2]);
    m41=abs(satira-dizia[3]);
    m42=abs(sutuna-dizib[3]);
    m51=abs(satira-dizia[4]);
    m52=abs(sutuna-dizib[4]);
   /* if(m11<0)
    	m11=-1*m11;
	if(m12<0)
    	m12=-1*m12;
	if(m21<0)
    	m21=-1*m21;
	if(m22<0)
    	m22=-1*m22;
	if(m31<0)
    	m31=-1*m31;
	if(m32<0)
    	m32=-1*m32;
	if(m41<0)
    	m41=-1*m41;
	if(m42<0)
    	m42=-1*m42;
	if(m51<0)
    	m51=-1*m51;
	if(m52<0)
    	m52=-1*m52;*/
    	
	int t1,t2,t3,t4,t5;
	t1=m11+m12;
	t2=m21+m22;
	t3=m31+m32;
	t4=m41+m42;
	t5=m51+m52;
	
    if(matris[dizia[0]][dizib[0]]==0)
    	printf("1. Elmas alındı\n");
    else
    	printf("1. Elmasa olan mesafe:%d\n",t1);
    if(matris[dizia[1]][dizib[1]]==0)
    	printf("2. Elmas alındı\n");
	else
		printf("2. Elmasa olan mesafe:%d\n",t2);	
	if(matris[dizia[2]][dizib[2]]==0)
    	printf("3. Elmas alındı\n");
	else
		printf("3. Elmasa olan mesafe:%d\n",t3);	
	if(matris[dizia[3]][dizib[3]]==0)
    	printf("4. Elmas alındı\n");
	else
		printf("4. Elmasa olan mesafe:%d\n",t4);	
	if(matris[dizia[4]][dizib[4]]==0)
    	printf("5. Elmas alındı\n");
	else
		printf("5. Elmasa olan mesafe:%d\n",t5);	
	printf("Can Durumu: %d\n",can);

    //hareket
	for(;can>0;)
	{
	char hareket;
	hareket=getch();
   
   switch(hareket)
   {
   	case 'w': 
   	    if(e==0)
   	    	continue;
   	    
    	satira=e-1;
    	sutuna=d;
    	if(matris[e][d]!=2)
   	    {
   		matris[e][d]=0;
	    }
    	if(matris[e-1][d]!=2)
    	{
		matris[e-1][d]=5;
	    }
	    e--;
	    if(matris[e][d]==2)
    	{
		matris[2][4]=5;
		e=2;
		d=4;
		can--;
		canfonk(can);
		system("cls");
		}
	system("cls");
    goto etiket;
    break;
	
	case 's':
		if(e==9)
			continue;
		
		satira=e+1;
	    sutuna=d;
		if(matris[e][d]!=2)
        {
	    matris[e][d]=0;
	    } 
	    if(matris[e+1][d]!=2)
	    {
	   	 matris[e+1][d]=5;
	    }  
	    e++;
	    if(matris[e][d]==2)
	    {
		matris[2][4]=5;
	   	can--;
	   	e=2;
	   	d=4;
		canfonk(can);
		system("cls");
	    }
	    
	   
	system("cls");
	goto etiket;
	break;
	
	case 'a':
		if(d==0)
			continue;
		
    	 satira=e;
    	 sutuna=d-1;
    	 if(matris[e][d]!=2)
	    {
	    matris[e][d]=0;
	    } 
	    if(matris[e][d-1]!=2)
	    {
	    matris[e][d-1]=5;
	    }  
	    d--;
	    if(matris[e][d]==2)
	    {
		matris[2][4]=5;
	   	can--;
	   	e=2;
	   	d=4;	   	
		canfonk(can);
		system("cls");
		
	    }    
	system("cls");
	goto etiket;
	break;  
	
	case 'd':
		if(d==9)
			continue;
		
	    satira=e;
        sutuna=d+1;
	    if(matris[e][d]!=2)
	    {
	    matris[e][d]=0;
	    } 
	    if(matris[e][d+1]!=2)
	    {
	   	matris[e][d+1]=5;
	    }   
	    d++;
	    if(matris[e][d]==2)
	    {
	    can--;
	   	e=2;
	   	d=4;	
		matris[2][4]=5;	
		canfonk(can);
		system("cls");
	    }  
	system("cls");
	goto etiket;
	break;  
	
	default :system("COLOR 4");
	printf("yanlış tuşa bastınız");
	sleep(1);
	system("COLOR D");
	break;	
   }
   
   } 
    char bilgi[12]="KAYBETTİNİZ";
   	if(can==0)
	{
		system("cls");
		system("COLOR 4F");
		printf("***********************************************************************");
		for(f=0;f<11;f++)
		{
			printf(" \n*                                  %c                                  *",bilgi[f]);
			sleep(1);
		}
		 printf("\n*                                 :(                                  *\n");
		 printf("***********************************************************************");
		 printf("\n\n\n\n\n");
	}
  
	
	
	return 0;
}
