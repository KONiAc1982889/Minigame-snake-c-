#include <iostream>
#include <bits/stdc++.h>
#include <random>
#include <conio.h>
using namespace std;
bool setMar(char **field)
{

}

struct snakePart
{
    int x,y;
    snakePart* next;
    snakePart* prev;
};

void printField(char** field, int fieldHeight, int fieldWidth)
{
    for(int i=0; i<fieldHeight; i++)
    {
        for(int j=0; j<fieldWidth; j++)
        {
            cout<<field[i][j];
        }
        cout<<"×\n";

    }
    for(int j=0; j<fieldWidth; j++)
        cout<<"×";
}

void clearField(char** field, int fieldHeight, int fieldWidth)
{
    for(int i=0; i<fieldHeight; i++)
    {
        for(int j=0; j<fieldWidth; j++)
        {
            field[i][j] = ' ';
        }
    }
}


int main()
{

    setlocale(LC_ALL, "English");

    int fieldWidth,fieldHeight;

    do
    {
        system("cls");
        cout<<"Set the width: ";
        cin>>fieldWidth;
        cout<<"Set the height: ";
        cin>>fieldHeight;
    }
    while((fieldHeight<=2) or (fieldWidth<=2));

    char** field = new char*[fieldHeight];
    for(int i=0; i<fieldHeight; i++)
    {
        field[i]= new char[fieldWidth];
    }


    clearField(field,fieldHeight,fieldWidth);
    system("cls");
    for(int i=0; i<fieldHeight; i++)
    {
        for(int j=0; j<fieldWidth; j++)
        {
            cout<<field[i][j];
        }
        cout<<endl;
    }
    int appleX,appleY;
    int snakeXprev,snakeYprev;
    snakePart snake;
    snakePart* snakeHead = &snake;
    snake.x= rand() % fieldWidth;
    snake.y= rand() % fieldHeight;
    snake.next=NULL;
    snake.prev=NULL;

    bool viu=true;
    char c;
    appleX=rand() % fieldWidth;
    appleY=rand() % fieldHeight;


    int currentlengh=0;
    int l=0;
    snakePart*snakeCurrent=snakeHead;

    while(viu)
    {
        snakeXprev=snake.x;
        snakeYprev=snake.y;
        c = _getch();
        if((c=='w')or(c=='W'))
        {
            snake.y-=1;
            if(snake.y<0)snake.y=fieldHeight-1;
        }

        if((c=='d')or(c=='D'))
        {
            snake.x=(snake.x+1)%fieldWidth;
        }
        if((c=='s')or(c=='S'))
        {
            snake.y=(snake.y+1)%fieldHeight;
        }
        if((c=='a')or(c=='A'))
        {
            snake.x-=1;
            if(snake.x<0)snake.x=fieldWidth-1;
        }

        snakeCurrent=snakeHead;
        if(l>1)
        {
            snakeCurrent=snakeCurrent->next;
            while(snakeCurrent->next!=NULL)
            {
                if(field[snake.y][snake.x]=='*')
                {
                    viu=false;
                    break;
                }
                snakeCurrent= snakeCurrent->next;
            }
        }







        if ((snake.x == appleX) && (snake.y == appleY))
        {
            do
            {
                appleX = rand() % fieldWidth;
                appleY = rand() % fieldHeight;
            }
            while (field[appleY][appleX] != ' ');

            snakePart* newSegment = new snakePart;
            newSegment->x = snake.x;
            newSegment->y = snake.y;
            newSegment->next = snakeHead;
            snakeHead->prev = newSegment;
            snakeHead = newSegment;

            l++;
        }


        snakeCurrent=snakeHead;
        if(l>1)
        {
            while(snakeCurrent->next!=NULL)snakeCurrent=snakeCurrent->next;

            while(snakeCurrent->prev!=snakeCurrent->next)
            {
                snakeCurrent->x=snakeCurrent->prev->x;
                snakeCurrent->y=snakeCurrent->prev->y;
                snakeCurrent=snakeCurrent->prev;
            }
            snakeCurrent->y=snakeYprev;
            snakeCurrent->x=snakeXprev;
        }


        snakeCurrent=snakeHead;
        currentlengh=0;
        clearField(field,fieldHeight,fieldWidth);
        field[appleX][appleY]='+';
        while(snakeCurrent!=NULL)
        {
            if(currentlengh==0)  field[snakeCurrent->y][snakeCurrent->x] = 'o';
            else field[snakeCurrent->y][snakeCurrent->x] = '*';
            currentlengh++;
            snakeCurrent= snakeCurrent->next;
        }

        system("cls");
        cout<<"Your score: "<<l<<endl;

        printField(field, fieldHeight, fieldWidth);
    }

    cout<<"Game Over!"<<endl;
    cout<< "Your score: "<< l;
    return 0;
}
