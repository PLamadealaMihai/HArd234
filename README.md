#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include"operation.c"

void main()
{
    const char file_name[]="Lab9.txt";
   Restaurand *F, *B, *value;
    List * list = NULL;
    List* list1 = NULL;
    List* list2 = NULL;
    int size;
    int id;
    int id1, id2;
    int numar;
    NodeList * current = NULL;

    while(1)
    {

        printf("*********************************MENU*********************************\n");
        printf("1.  Crearea listei in memoria dinamica.\n");
        printf("2.  Introducerea informatiei despre elementele listei de la tastatura.\n");
        printf("3.  Afisarea informatiei despre elementele listei la ecran.\n");
        printf("4.  Cautarea elementului in lista.\n");
        printf("5.  Modificarea campurilor unui element din lista.\n");
        printf("6.  Determinarea adresei ultimului element din lista.\n");
        printf("7.  Determinarea lungimei listei.\n");
        printf("8.  Interschimbarea a 2 elemente indicate in lista.\n");
        printf("9.  Sortarea listei.\n");
        printf("10. Adaugarea unui element nou la sfarsitul listei.\n");
        printf("11. Adaugarea unui element nou la inceputul listei.\n");
        printf("12. Inserarea unui element nou dupa elementul indicat al listei.\n");
        printf("13. Inserarea unui element nou inaintea elementului indicat in lista.\n");
        printf("14. Stergerea elementului indicat in lista.\n");
        printf("15. Divizarea listei in doua liste.\n");
        printf("16. Concatenarea a doua liste.\n");
        printf("17. Salvarea informatiei despre elementele listei in fisier.\n");
        printf("18. Citirea informatiei despre elementele listei din fisier.\n");
        printf("19. Eliberarea memoriei alocate pentru lista.\n");
        printf("0.  Iesire din program.\n");
        printf("**********************************************************************\n");

        printf("Alegeti una din variantele date : ");
        scanf("%d",&numar);
        switch(numar)
        {
        case 1:
            if(list!=NULL)
            {
                List_delete(list);
            }
            list = List_create();
            printf("\nLista a fost creata!!!\n");
            break;
        case 2:
            printf("Introduceti datele despre Restaurand : \n");
            printf("Dati numarul de elemente din lista : ");
            scanf("%d", &size);
            for(int i = 0; i < size; i++)
            {
                Read_Info(list);
            }
            break;
        case 3:
            printf("Informatii despre Restaurand : \n");
            List_print(list);
            break;
        case 4:
            printf("Dati id-ul pentru cautarea elementului : ");
            scanf("%d", &id);
            current = List_node_search(list,id);
            if(current)
            {
                printf("Restaurand cu acest indice este in lista\n");
                printf("Denumirea : %s\n", current->value->denumirea);
                printf("adresa : %s\n", current->value->adresa);
                printf("telefonul : %s\n", current->value->adresa);
                printf("categoria : %d\n",current->value->telefonul);
                printf("nr_de_locuri : %d\n", current->value->nr_de_locuri);
                printf("specializarea : %d\n", current->value->specializarea);
                printf("Adresa current: %p     Adresa next: %p\n", current, current->next);
            }
            else
            {
                printf("Restaurand cu asa nume nu este in lista!!!!");
            }
            break;
        case 5:
            printf("Dati indicele Restaurand ce doriti sa o modificati : ");
            scanf("%d", &id);
            Modify_Info_Element(list,id);
            printf("Modificarea a avut loc cu succes!!!\n");
            break;
        case 6:
            printf("Adresa ultimului element este %p",LastElement(list));
            break;
        case 7:
            printf("Lungimea liste este : %d elemente\n",List_size(list));
            break;
        case 8:
            printf("Dati primul id pentru interschimbare : ");
            scanf("%d", &id1);
            printf("Dati al doilea id pentru interschimbare : ");
            scanf("%d", &id2);
            List_swap_data(list,id1,id2);
            printf("Interschimbarea a avut loc cu succes!!!\n");
            break;
        case 9:
            printf("Sortarea listei dupa numarul de carti : \n");
            Sort_List(list);
            printf("Sortarea a avut loc cu succes!!!\n");
            break;
        case 10:
            F=malloc(sizeof(Restaurand));
            printf("Dati denumirea: ");
            fflush(stdin);
            gets(F->denumirea);
            printf("Dati adresa: ");
            fflush(stdin);
            gets(F->adresa);
            printf("telefonul: ");
            fflush(stdin);
            gets(F->telefonul);
            printf("Dati categoria : ");
            scanf("%d", &F->categoria);
            printf("Dati nr_de_locuri: ");
            scanf("%d", &F->nr_de_locuri);
            printf("Dati specializarea: ");
            scanf("%d", &F->specializarea);

            List_push_back(list,F);
            printf("\nAdaugarea la final a avut loc cu succes!!!!\n");
            break;
        case 11:
             F=malloc(sizeof(Restaurand));
            printf("Dati denumirea: ");
            fflush(stdin);
            gets(F->denumirea);
            printf("Dati adresa: ");
            fflush(stdin);
            gets(F->adresa);
            printf("Dati telefonul: ");
            fflush(stdin);
            gets(F->telefonul);
            printf("Dati categoria : ");
            scanf("%d", &F->categoria);
            printf("Dati nr_de_locuri: ");
            scanf("%d", &F->nr_de_locuri);
             printf("Dati specializarea: ");
            scanf("%d", &F->specializarea);

            List_push_front(list,F);
            printf("\nAdaugarea la inceput a avut loc cu succes!!!!\n");
            break;
        case 12:
            F=malloc(sizeof(Restaurand));
            printf("Dati denumirea: ");
            fflush(stdin);
            gets(F->denumirea);
            printf("Dati adresa: ");
            fflush(stdin);
            gets(F->adresa);
            printf("Dati telefonul: ");
            fflush(stdin);
            gets(F->telefonul);
            printf("Dati categoria : ");
            scanf("%d", &F->categoria);
            printf("Dati nr_de_locuri: ");
            scanf("%d", &F->nr_de_locuri);
            printf("Dati specializarea: ");
            scanf("%d", &F->specializarea);

            printf("Dati pozitia pentru inserarea ei : ");
            scanf("%d", &id);
            List_insert_after(list,id,F);
            printf("\nInserarea a avut loc cu succes!!!!\n");
            break;
        case 13:
           F=malloc(sizeof(Restaurand));
            printf("Dati denumirea: ");
            fflush(stdin);
            gets(F->denumirea);
            printf("Dati adresa: ");
            fflush(stdin);
            gets(F->adresa);
            printf("Dati telefonul: ");
            fflush(stdin);
            gets(F->telefonul);
            printf("Dati categoria : ");
            scanf("%d", &F->categoria);
            printf("Dati nr_de_locuri: ");
            scanf("%d", &F->nr_de_locuri);
            printf("Dati specializarea: ");
            scanf("%d", &F->specializarea);

            printf("Dati pozitia unde sa fie inserata acest Restaurand : ");
            scanf("%d",&id);
            List_insert_before(list,id,F);
            printf("\nInserarea a avut loc cu succes!!!\n");
            break;
        case 14:
            printf("Dati indicele Restaurand pentru a sterge din lista : ");
            scanf("%d", &id);
            List_element_delete(list,id);
            printf("Elementul a fost sters din lista\n");
            break;
        case 15:
            list2 = List_divide(list);
            printf("Lista a fost divizata!!");
            break;
        case 16:
            if(list2!=NULL)
            {
                List_print(list);
                printf("\n");
                List_print(list2);
                printf("\n");
                printf("\n Lista Concatenata : \n");
                list = List_merge(list,list2);
                List_print(list);
            }
            break;
        case 17:
            List_save_to_file(list,file_name);
            printf("Datele au fost salvate in fisier!!!\n");
            break;
        case 18:
            if(list!=NULL)
            {
                List_delete(list);
            }
            list = List_load_from_file(file_name);
            printf("Elementele din lista au fost citite!!!!\n");
            break;
        case 19:
            List_delete(list);
            printf("Memoria a fost eliberata!!!\n");
            break;
        case 0:
            printf("Am iesit din program!!!\n");
            return;
            break;
        default:
            printf("Numarul ales nu face parte din meniul dat. Mai alegeti inca o data\n");
        }
    }
}



