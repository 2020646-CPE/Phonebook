#include<stdio.h>
#include<conio.h>
#include<string.h>
#include<stdlib.h>
#include<windows.h>
struct person
{
    char s2020646_name[35];
    char s2020646_address[50];
     char s2020646_father's_name[35];
     char s2020646_mother's_name[30];
     char s2020646_mble_no;
    char s2020646_gender[8];
    char s2020646_mail[100];
    char s2020646_fav_color[20];

    };
void menu();
void got();
void start();
void back();
void addrecord();
void listrecord();
void modifyrecord();
void deleterecord();
void searchrecord();
int main()
{
    system("color 5f");
    start();
    return 0;
}
void back()
{
    start();
}
void start()
{
    menu();
}
void menu()
{
    system("cls");
printf("\t\t**********WELCOME TO MINI PHONEBOOK*************");

printf("\n\n\t\t\t  MENU\t\t\n\n");
printf("\t1.Add New   \t2.List   \t3.Exit  \n\t4.Modify \t5.Search\t6.Delete");

switch(getch())
{
    case '1':

                addrecord();
    break;
   case '2': listrecord();
    break;
    case '3': exit(0);
    break;
    case '4': modifyrecord();
    break;
    case '5': searchrecord();
    break;
    case '6': deleterecord();
    break;
    default:
                system("cls");
                printf("\nEnter 1 to 6 only");
                printf("\n Enter any key");
                getch();

menu();
}
}
        void addrecord()
{
        system("cls");
        FILE *f;
        struct person p;
        f=fopen("project","ab+");
        printf("\n Enter your name here: ");
        got(p.S2020646_name);
        printf("\nEnter your address here: ");
        got(p.s2020646_address);
        printf("\nEnter your father's name here: ");
        got(p.s2020646_father's_name);
        printf("\nEnter your mother's name here: ");
        got(p.s2020646_mother's_name);
        printf("\nEnter your phone no here.:");
        scanf("%ld",&p.s2020646_mble_no);
        printf("Enter your gender here:");
        got(p.s2020646_gender);
        printf("\nEnter your e-mail here:");
         got(p.s2020646_mail);
        printf("\nEnter favorite color here:");
        got(p.s2020646_fav_color);
        fwrite(&p,sizeof(p),1,f);

      fflush(stdin);
        printf("\nrecord saved");

fclose(f);

    printf("\n\nEnter any key");

	 getch();
    system("cls");
    menu();
}
void listrecord()
{
    struct person p;
    FILE *f;
f=fopen("project","rb");
if(f==NULL)
{
printf("\nfile opening error in listing :");

exit(1);
}
while(fread(&p,sizeof(p),1,f)==1)
{
     printf("\n\n\n YOUR RECORD IS\n\n ");
        printf("\nName=%s\nAdress=%s\nFather name=%s\nMother name=%s\nMobile no=%ld\nSex=%s\nE-mail=%s\nCitizen no=%s",p.s2020646_name,p.s2020646_address,p.s2020646_father's_name,p.s2020646_mother's_name,p.s2020646_mble_no,p.s2020646_sex,p.s2020646_mail,p.s2020646_fav_color);

	 getch();
	 system("cls");
}
fclose(f);
 printf("\n Enter any key");
 getch();
    system("cls");
menu();
}
void searchrecord()
{
    struct person p;
FILE *f;
char name[100];

f=fopen("project","rb");
if(f==NULL)
{
    printf("\n error in opening\a\a\a\a");
    exit(1);

}
printf("\nEnter name of person to search\n");
got(name);
while(fread(&p,sizeof(p),1,f)==1)
{
    if(strcmp(p.name,name)==0)
    {
        printf("\n\tDetail Information About %s",name);
        printf("\nName:%s\naddress:%s\nFather name:%s\nMother name:%s\nMobile no:%ld\nsex:%s\nE-mail:%s\nfav color:%s",p.s2020646_name,p.s2020646_address,p.s2020646_father's_name,p.s2020646_mother's_name,p.s2020646_mble_no,p.s2020646_gender,p.s2020646_mail,p.s2020646_fav_color);
    }
        else
        printf("FILE CANNOT BE FOUND");

}
 fclose(f);
  printf("\n Enter any key");

	 getch();
    system("cls");
menu();
}
void deleterecord()
{
    struct person p;
    FILE *f,*ft;
	int flag;
	char name[100];
	f=fopen("project","rb");
	if(f==NULL)
		{

			printf("CONTACT'S DATA HAS NOT BEEN ADDED YET.");

		}
	else
	{
		ft=fopen("temp","wb+");
		if(ft==NULL)

            printf("file opaning error");
		else

        {


		printf("Enter CONTACT'S NAME:");
		got(name);

		fflush(stdin);
		while(fread(&p,sizeof(p),1,f)==1)
		{
			if(strcmp(p.name,name)!=0)
				fwrite(&p,sizeof(p),1,ft);
			if(strcmp(p.name,name)==0)
                flag=1;
		}
	fclose(f);
	fclose(ft);
	if(flag!=1)
	{
		printf("NO CONTACT'S RECORD TO DELETE.");
		remove("temp.txt");
	}
		else
		{
			remove("project");
			rename("temp.txt","project");
			printf("RECORD WAS SUCCESSFULLY DELETED.");

		}
	}
}
 printf("\n Enter any key here.");

	 getch();
    system("cls");
menu();
}

void modifyrecord()
{
    int c;
    FILE *f;
    int flag=0;
    struct person p,s;
	char  name[50];
	f=fopen("project","rb+");
	if(f==NULL)
		{

			printf("THE CONTACT'S INFORMATION HAS NOT BEEN ADDED YET..");
			exit(1);


		}
	else
	{
	    system("cls");
		printf("\nTO MODIFY, enter CONTACT'S NAME.:\n");
            got(name);
            while(fread(&p,sizeof(p),1,f)==1)
            {
                if(strcmp(name,p.name)==0)
                {



                    printf("\n Enter name:");
                    got(s.s2020646_name);
                    printf("\nEnter the address:");
                    got(s.s2020646_address);
                    printf("\nEnter father's name:");
                    got(s.s2020646_fathers's_name);
                    printf("\nEnter mother's name:");
                    got(s.s2020646mother's_name);
                    printf("\nEnter phone no:");
                    scanf("%ld",&s.s2020646mble_no);
                    printf("\nEnter gender:");
                    got(s.s2020646_gender);
                    printf("\nEnter e-mail:");
                    got(s.s2020646_mail);
                    printf("\nEnter favorite color\n");
                    got(s.s2020646_fave_color);
                    fseek(f,-sizeof(p),SEEK_CUR);
                    fwrite(&s,sizeof(p),1,f);
                    flag=1;
                    break;



                }
                fflush(stdin);


            }
            if(flag==1)
            {
                printf("\n Your data has been updated");

            }
            else
            {
                    printf(" \n There is no data available.");

            }
            fclose(f);
	}
	 printf("\n Enter any key");
	 getch();
    system("cls");
	menu();

}
void got(char *name)
{

   int i=0,j;
    char c,ch;
    do
    {
        c=getch();
                if(c!=8&&c!=13)
                {
                    *(name+i)=c;
                        putch(c);
                        i++;
                }
                if(c==8)
                {
                    if(i>0)
                    {
                        i--;
                    }
                   // printf("h");
                    system("cls");
                    for(j=0;j<i;j++)
                    {
                        ch=*(name+j);
                        putch(ch);

                    }

                }
    }while(c!=13);
      *(name+i)='\0';
}
