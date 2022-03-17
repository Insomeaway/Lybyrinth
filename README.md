#include<stdio.h>
#include<conio.h>
#include<windows.h>

char Map[9][12]={"*#*********",
				 "***###*###*",
				 "###**#****#",
				 "*#**###**#*",
				 "***********",
				 "#####*##*##",
				 "*##*****#*E",
				 "***#*###**#",
				 "*#*********"};

void pos(int a,int b)        //打印迷宫
{
	COORD pos;
	pos.X=b;
	pos.Y=a;
	SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE),pos);
}

void cycle()                 //控制方向
{	
	int x=0,y=0;
	char MOVE;
	while((x==6&&y==10)==0)
	{
		pos(x,y);
		MOVE=getch();              //getch():所在头文件为conio.h;用途：从控制台读取一个字符，但不显示在屏幕上
		if(MOVE=='w')
		{
			if(Map[x-1][y]=='*')
			{
				x--;
			}
		}
		if(MOVE=='s')
		{
			if(Map[x+1][y]=='*')
			{
				x++;
			}
		}
		if(MOVE=='a')
		{
			if(Map[x][y-1]=='*')
			{
				y--;
			}
		}
		if(MOVE=='d')
		{
			if(Map[x][y+1]=='*'||Map[x][y+1]=='E')
			{
				y++;
			}
		}
	}
}

int main()
{
	for(int Q=0;Q<9;Q++)
	{
		printf("%s\n",Map[Q]);
	}
	cycle();
	printf("恭喜你，完成迷宫\n");
	return 0;
}

