#include <stdio.h>
#include<stdlib.h>
#include <strings.h>

void sort();
typedef struct node{
    size_t len;
    struct node*next;
    int free;
    char *chr[5];
    //int len;
}node;
static node pool[15];
static int curr=0;

void init(){
    int count=0;int i;
    node*temp=&pool;
    for(i=0;i<15;i++){
        pool[i].next=&pool[i+1];
        pool[i].free=1;
        char*n="";
        strcpy(pool[i].chr,n);
    }
    node*n=&pool;
}

void insert(char *chr){
    node*temp=&pool;int i;
    char chr2[5];int j;
    for(j=0;j<4;j++){
        chr2[j]=chr[j];
    }
    int c=0;
    while (chr[c] != '\0')
        c++;
    while(temp){
        if(temp->free==1){
            //printf("%s  %i\n",chr,c);
            temp->len=c;
            strcpy(temp->chr,chr2);
            temp->free=0;
            break;
        }
        temp=temp->next;
    }
    curr++;
    sort();
}

void sort(){
    node *tempi=&pool;node*tempj=&pool;
    char a[5];char b[5];
    while (tempi){
        tempj=&pool;
        while(tempj){
           // printf("%s,%i   %s,%i",tempi->chr,tempi->len,tempj->chr,tempj->len);
           
            if(strcasecmp(tempj->chr , tempi->chr) > 0){
                int i,j;
                i=tempi->len;j=tempj->len;
                tempi->len=j;tempj->len=i;
                strcpy(a,tempi->chr);
                strcpy(b,tempj->chr);
                strcpy(tempj->chr,a);
                strcpy(tempi->chr,b);
                
            }
           // i=0;j=0;
            tempj=tempj->next;
        }
      //  printf("\n");
        tempi=tempi->next;
    }
}
void delete(char*str){
    node*n=&pool;int i;
    while(n){
        if(strcmp(n->chr,str)==0){
            char* n2= "";
            strcpy(n->chr,n2);
            //printf("uieiue");
            sort();
            break;
        }
        n=n->next;
    }
    sort();
}

void print(){
    node*temp= (node *) &pool;
    int i;
    char *n="";
    while(temp){
        if(strcmp(n, temp->chr) != 0) {
            printf(" %s,%i ", temp->chr,temp->len);
        }
        temp=temp->next;
    }
    printf("\n");
}
void searchCaseless(char str[]){
    node*temp= (node *) &pool;
    while(temp){
        if(strcasecmp(str, temp->chr) == 0) {
            printf("%s found with length %i\n", temp->chr,temp->len);
            return;
        }
        temp=temp->next;
    }
    printf("\n");
    printf("%s not found");
}
void searchCase(char str[]){
    node*temp= (node *) &pool;
    while(temp){
        if(strcmp(str, temp->chr) == 0) {
            printf("%s found with length %i\n", temp->chr,temp->len);
            printf("\n");
            return;
        }
        temp=temp->next;
    }
    printf("%s not found\n");
}

void io(){
    char str[100];
    char splitStrings[10][10]; //can store 10 words of 10 characters
    int i, j, cnt;

    printf("Enter a string: ");
    gets(str);

    j = 0;
    cnt = 0;
    for (i = 0; i <= (strlen(str)); i++) {
        // if space or NULL found, assign NULL into splitStrings[cnt]
        if (str[i] == ' ' || str[i] == '\0') {
            splitStrings[cnt][j] = '\0';
            cnt++; //for next word
            j = 0; //for next word, init index to 0
        }
        else {
            splitStrings[cnt][j] = str[i];
            j++;
        }
    }
    printf("\nOriginal String is: %s", str);
    printf("\nStrings (words) after split by space:\n");
    char c[5];
    for (i = 0; i < cnt; i++) {
        for(j=0;j<4;j++){
            // printf("%c",splitStrings[i][j]);
            c[j]=splitStrings[i][j];
        }
        insert(splitStrings[i]);
        //printf("%s",c);
        //printf("\n");
    }

}

int main() {
    init();
    //print2(pool);
    io();
    //printf("Hello, World!\n");
    int op;char input[20];char input2[]="aaaa";int j;

    while(op!=3){
        printf("enter option: 1-> remove    2->insert     3->quit       4->view list      5->caseLess     6->case       :");
        scanf("%i",&op);
        if(op==1){
            printf("\nEnter a Word: ");
            scanf("%s",&input);
            for(j=0;j<4;j++){
                input2[j]=input[j];
            }
            printf("\n");
            delete(input2);
            print();
            continue;
        }
        if(op==2){
            printf("\nEnter a Word: ");
            scanf("%s",&input);
            int c=0;
            while (input[c] != '\0')
                c++;
            printf("\n");
            for(j=0;j<4;j++){
                input2[j]=input[j];
            }
            printf("---------\n");
            insert(input);
            //printf("%s\n",input2);
            print();
            continue;
        }
        if(op==3){
            exit(0);
        }
        if(op==4){
            print();
            sort();
            continue;
        }

        if(op==5){
            printf("\nEnter a Word: ");
            scanf("%s",&input);
            printf("\n");
            for(j=0;j<4;j++){
                input2[j]=input[j];
            }
            searchCaseless(input2);
        }
        if(op==6){
            printf("\nEnter a Word: ");
            scanf("%s",&input);
            printf("\n");
            for(j=0;j<4;j++){
                input2[j]=input[j];
            }
            searchCase(input2);
        }
    }
    return 0;
}