#pragma clang diagnostic push
#pragma ide diagnostic ignored "EndlessLoop"
#pragma ide diagnostic ignored "bugprone-integer-division"
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <conio.h>
#include <time.h>
#include <windows.h>
#define N 101
#define M 101
int Max(int x ,int y);
void line (int x1,int y1,int x2,int y2,char poto[N][M],char c);
int main ()
{
    const double pi = acos(-1.0);
    double m = 0,n;
    int end = 0;
    int x = 0,y = 0,i = 0,j,colock =0;
    int rx = 18,ry = 36;
    int cx = 40,cy = 40;
   char poto[N][M],*s = NULL;
    time_t t;
    t = time(&t);
    s = ctime(&t);
    do{
        for (i = 0;i<N;i++)
        {
            for (j = 0; j < M; j++) {
                poto[i][j] = ' ';
            }

        }
        poto[cx][cy] = '@';
        for(m = 0;m<=pi*2;m = m+0.03) // NOLINT(*-flp30-c)
        {
            x = (int)(cx + rx * cos(m) +0.5);
            y = (int )(cy + ry * sin(m) +0.5);
            poto[2*cy-x][y] = '*';
  }
        colock = 0;
        for (m = 0;m<=pi*2;m = m+pi/6)
        {
            x = (int)(cx + 16 * cos(m) + 0.5);
            y = (int)(cy + 32 * sin(m) + 0.5);
            switch(colock)
            {
                case 0:
                    poto[2*cy-x][y] = '1';
                    poto[2*cy-x][y+1] = '2';
                    break;
                case 1:
                    poto[2*cy-x][y] = '1';
                    break;
                case 2:
                    poto[2*cy-x][y] = '2';
                    break;
                case 3:
                    poto[2*cy-x][y] = '3';
                    break;
  case 4:
                    poto[2*cy-x][y] = '4';
                    break;
                case 5:
                    poto[2*cy-x][y] = '5';
                    break;
                case 6:
                    poto[2*cy-x][y] = '6';
                    break;
                case 7:
                    poto[2*cy-x][y] = '7';
                    break;
                case 8:
                    poto[2*cy-x][y] = '8';
                    break;
                case 9:
                    poto[2*cy-x][y] = '9';
                    break;
                case 10:
                    poto[2*cy-x][y] = '1';
                    poto[2*cy-x][y+1] = '0';
                     break;
                case 11:
                    poto[2*cy-x][y] = '1';
                    poto[2*cy-x][y+1] = '1';
                    break;
            }
            colock++;
        }
        t = time(&t);
        s = ctime(&t);
        m = (s[17]-'0')*10+s[18]-'0';
        x = (int)(cx+14*cos (pi*m/30)+0.5);
        y = (int)(cy+28*sin(pi*m/30)+0.5);
        poto[2*cy-x][y] = 's';
        line(cx,cy,2*cy-x,y,poto,'s');
        m = (s[14]-'0')*10+s[15]-'0';
        x = (int)(cx+12*cos(pi*m/30)+0.5);
        y = (int)(cy+24*sin(pi*m/30)+0.5);
        poto[2*cy-x][y] = 'M';
        line(cx,cy,2*cy-x,y,poto,'M');
        m = (s[14]-'0')*10+s[15]-'0';
        n = ((s[11]-'0')*10+s[12]-'0')/12;
        x = (int)(cx+10*cos(pi*n/6+pi*m/360)+0.5);
        y = (int)(cy+20 *sin(pi*n/6+pi*m/360)+0.5);
        poto[2*cy-x][y] = 'H';
        line(cx,cy,2*cy-x,y,poto,'H');
        system("cls");
        for( i = 20;i<62;i++)
        {
            for(j = 0;j<90;j++)
            {
                printf("%c",poto[i][j]);
            }
            putchar('\n');
        }
        Sleep(999);

    }while (end != -1);
    return 0;
}

#pragma clang diagnostic pop



