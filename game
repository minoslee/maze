
#include <stdio.h>
#include <conio.h>
#include <time.h>
#include <windows.h>
#include <stdlib.h>
#include <string.h>

int code [17][24]= {
                        0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
                        0,-1,0,0,0,0,0,0,0,0,0,0,0,-1,0,0,0,0,0,0,0,0,0,0,
                        0,-1,-1,-1,-1,-1,-1,0,0,0,0,0,0,-1,0,0,0,0,0,-1,-1,-1,0,0,
                        0,-1,0,0,0,-1,0,0,0,0,0,0,0,-1,0,0,0,0,0,-1,0,0,0,0,
                        0,-1,-1,-1,-1,-1,0,-1,-1,-1,-1,-1,0,-1,0,-1,-1,-1,-1,-1,-1,-1,0,0,
                        0,-1,0,0,-1,0,-1,0,0,0,0,-1,0,-1,-1,-1,0,0,0,0,0,0,0,0,
                        0,-1,-1,-1,-1,-1,-1,0,0,0,0,-1,0,0,0,-1,0,0,0,0,0,0,0,0,
                        0,-1,0,0,0,0,0,0,0,0,0,-1,0,0,0,-1,-1,-1,-1,-1,-1,-1,-1,0,
                        0,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,0,-1,0,0,-1,0,0,0,0,
                        0,0,0,0,0,0,-1,0,0,0,0,0,0,0,-1,0,-1,0,0,-1,0,0,0,0,
                        0,0,0,0,0,0,-1,0,0,0,0,0,0,0,-1,0,-1,-1,-1,-1,0,-1,-1,0,
                        0,0,0,0,0,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,0,0,0,0,-1,0,0,
                        0,0,0,0,0,-1,0,0,0,0,0,0,0,-1,0,0,0,0,0,0,0,-1,0,0,
                        0,0,-1,-1,-1,-1,0,0,0,0,0,0,0,-1,-1,-1,-1,-1,-1,-1,-1,-1,0,0,
                        0,-1,-1,0,0,0,0,0,0,0,0,0,0,-1,0,0,0,0,0,0,0,0,0,0,
                        0,0,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,0,0,0,0,0,0,0,0,0,0,
                        0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
                   };

int x1,y1,x2,y2;//初始位置
char ch;
int flag;
int num,num1,num2;//剩余数字
int cnt;//记录数字大小
int step1,step2;//记录步数
int f;//标记声音
int fast = 999; //记录最快成绩
FILE *fp1 ,*fp2;
int t = 1;
//位置函数
void Gotoxy(int x,int y)
{
    COORD pos;
    pos.X=x;
    pos.Y=y;
    SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE),pos);//定位光标位置
}


//载入特效
void Load()
{
    int i = 0;
    Gotoxy(15,8);
    printf("游戏正在加载....");
    Gotoxy(15,10);
    for (i = 1; i <= 40; ++i)
    {
        putchar('-');
    }
    for (i = 1; i <= 40; ++i)
    {
        putchar('\b');
    }
    for (i = 1; i <= 40; ++i)
    {
        putchar('>');
        Sleep(100);
    }
    system("cls");
}

//帮助
void Help()
{
	Gotoxy(0,13);
    printf("\t\t\t      游戏说明\n");
    printf("\t\t1.单人模式中使用上下左右键控制位置\n");
    printf("\t\t2.双人模式中玩家一使用上下左右键控制，玩家二使用wasd控制\n");
    printf("\t\t3.双人模式中先吃到4个数字的玩家获胜\n");
    printf("\t\t4.按t键开启音效，按f键关闭音效\n");
    printf("\t\t5.游戏默认关闭音效\n");
    printf("\t\t6.吃光地图中7个数字即可获胜,该局游戏结束,并自动开始下一局游戏\n");
    printf("\t\t7.游戏过程中可随时按ESC键退出\n");
}

//显示主页面

void ShowMain()
{
    while(1)
    {
        Gotoxy(4,5);
        printf("数");
        Sleep(200);
        Gotoxy(8,5);
        printf("字");
        Sleep(200);
        Gotoxy(12,5);
        printf("迷");
        Sleep(200);
        Gotoxy(16,5);
        printf("宫");
        Sleep(200);
        Gotoxy(20,5);
        printf(" V");
        Sleep(200);
        Gotoxy(22,5);
        printf("1.3");
        Sleep(200);
        //printf("\t\t\t        数字迷宫v 1.03\n\n");
        Gotoxy(30,4);
        printf("1.开始标准模式(单人模式)");
        Sleep(200);
        Gotoxy(30,6);
        printf("2.开始竞技模式(双人模式)");
        Sleep(200);
        Gotoxy(30,8);
        printf("3.帮助");
        Sleep(200);
        Gotoxy(30,12);
        printf("0.退出\n");

        int choose;
        scanf("%d",&choose);
        if(choose == 1)
        {
            printf("qqq");
            flag = 1;
            break;
        }
        else if (choose == 2)
        {
            flag = 2;
            break;
        }
        else if (choose == 3)
        {
            //system("cls");
            Help();
        }
        else if (choose == 0)
        {
            flag = 0;
            break;
        }
    }
    printf("QAQ");
}

//根据数组输出图像
void SetCode(int num)
{
    if(num == 0)
    {
        printf("■");
    }
    else if(num == -1)
    {
        printf("  ");
    }
    else if (num >= 1&&num <= 7)
    {
        printf("%d ",num);
    }
}

//通过随机函数在走廊处随机生成数字
void SetNum()
{
    while(cnt<=7)
    {
        int x = rand()%17;
        int y = rand()%24;
        if(code[x][y] == -1&&x != 1&&y != 1)
        {
            code[x][y] = cnt++;
        }
        else
            SetNum();
    }
}

//生成地图主体函数：
void SetWindow()
{
    for(int i = 0; i <= 16; i++)
    {
        printf("\t\t");
        for(int j = 0 ; j <= 23; j++)
        {
            SetCode(code[i][j]);
        }
        printf("\n");
    }
    Gotoxy(18,1);//确定初始位置
    printf("\1 ");
    if(flag == 2)
    {
        Gotoxy(58,2);
        printf("\2 ");
    }
}



void UpKey1()
{
    if(code[x1-1][y1] != 0)
        x1--;
}
void DownKey1()
{
    if(code[x1+1][y1] != 0)
        x1++;
}
void LeftKey1()
{
    if(code[x1][y1-1] != 0)
        y1--;
}
void RightKey1()
{
    if(code[x1][y1+1] != 0)
        y1++;
}

void UpKey2()
{
    if(code[x2-1][y2] != 0)
        x2--;
}
void DownKey2()
{
    if(code[x2+1][y2] != 0)
        x2++;
}
void LeftKey2()
{
    if(code[x2][y2-1] != 0)
        y2--;
}
void RightKey2()
{
    if(code[x2][y2+1] != 0)
        y2++;
}

//覆盖原来表情
void GoToXYSpace(char ch)
{
    if(ch==72||ch==75||ch==77||ch==80)
    {
        Gotoxy(2*y1+16,x1);
        printf("  ");
    }
    else
    {
        Gotoxy(2*y2+16,x2);
        printf("  ");
    }
}

//移动表情
void MoveEmoji()
{
    if(ch==72||ch==75||ch==77||ch==80)
    {
        Gotoxy(2*y1+16,x1);
        printf("\1 ");
    }
    else
    {
        Gotoxy(2*y2+16,x2);
        printf("\2 ");
    }
}

//判断方向
void Direction(char ch)
{
    if(ch == 72||ch == 75||ch == 77||ch == 80)
    {
        switch (ch)//判断方向并计步
        {
        case 72:
            UpKey1();
            break;//上
        case 80:
            DownKey1();
            break;//下
        case 75:
            LeftKey1();
            break;//左
        case 77:
            RightKey1();
            break;//右
        }
        step1++;
    }
    else
    {
        switch(ch)
        {
        case 119:
            UpKey2();
            break;//w
        case 115:
            DownKey2();
            break;//s
        case 97:
            LeftKey2();
            break;//a
        case 100:
            RightKey2();
            break;//d
        }
        step2++;
    }
}

//检查剩余数字
int CheckLeftNum()
{
    if(num>=7)
        return 1;
    return 0;
}

//判断是否吃掉数字并计数
void CountNum(int x,int y)
{
    if(code[x][y] >= 1 && code[x][y] <= 7)
    {
        num++;
        code[x][y] = -1; //改变状态
        if(f)
            Beep(523,500);
        if(ch == 72||ch == 75||ch == 77||ch == 80)
            num1++;
        else
            num2++;
    }
}

void Information()
{
    Gotoxy(1,1);
    printf("当前步数");
    Gotoxy(1,2);
    printf("玩家1 ：%d",step1);
    if(flag == 2)
    {
        Gotoxy(1,3);
        printf("玩家2 ：%d",step2);
    }
    Gotoxy(1,4);
    printf("按t开启音效\n");
    Gotoxy(1,5);
    printf("按f关闭音效\n");
    Gotoxy(40,22);
    printf("数字迷宫 v1.3");
    Gotoxy(60,22);
    printf("design by lzh  ");
    Gotoxy(65,1);
    printf("当前得分");
    Gotoxy(65,2);
    printf("玩家1：");
    Gotoxy(72,2);
    printf("%d",num1);
    if(flag == 2)
    {
        Gotoxy(65,4);
        printf("玩家2：");
        Gotoxy(72,4);
        printf("%d",num2);
    }
    int i = 999;
    fp1 = fopen("rank.txt","r");
    fscanf(fp1,"%d",&i);
    Gotoxy(1,20);
    printf("当前最快记录为%d s",i);
    fclose(fp1);
}

// 随机变化5种颜色
void ChangeColor()
{
    int color;
    color = rand()%4;
    switch(color)
    {
    case 0:
        system("color 6f");
        break;
    case 1:
        system("color 07");
        break;
    case 2:
        system("color 30");
        break;
    case 3:
        system("color 70");
        break;
    }
}

void Begin()
{
	x1 = 1;
    y1 = 1;
    x2 = 2;
    y2 = 21;
    cnt = 1;
    step1 = 0;
    step2 = 0;
    system("cls");
    srand((unsigned)time(NULL));
    printf("2");
    SetNum(); //生成随机数
    SetWindow(); //生成地图
}

//单人模式
void OneP()
{
    while(flag != 0)
    {
        Begin();
        int startTime = clock(); //获取当前时间
        while(1)
        {
            ch = getch();
            if(ch == 27)  //判断ESC键
                exit(0);
            while(!(ch==72||ch==75||ch==77||ch==80)) //防止误触
            {
                if(ch == 't')  //判断是否开启音效
                {
                    f = 1;
                }
                else if (ch == 'f')
                    f = 0;
                else
                    ch = getch();
            }
            if(t = 0)
                break;
            GoToXYSpace(ch);//清除上次位置
            Direction(ch);//判断输入方向
            MoveEmoji();//移动表情 );
            CountNum(x1,y1); //统计数字个数
            Information(); //显示提示信息
            if(CheckLeftNum())
            {
                num = 0;
                step1 = 0;
    			step2 = 0;
    			num1 = 0;
				num2 = 0;
                int endTime = clock();
                int time = endTime - startTime;//计算用时
                if (time/1000 < fast)
                {
                    fast = time/1000;
                    fp2 = fopen("rank.txt","wb+");
                    fprintf(fp2,"%d",fast);
                    fclose(fp2);
                }
                ChangeColor();
                Gotoxy(30,19);
                printf("<(￣︶￣)> 用时%d s~",time/1000);
                Sleep(1000);
                MessageBox(NULL,"Bingo~ QVQ  进入下一关","Good job",MB_OK);
                break;
            }
        }
    }
}

//双人模式
void TwoP()
{
    while(flag != 0)
    {
        Begin();
    	int startTime = clock();
        while(1)
        {
            ch = getch();
            if(ch == 27)
                exit(0);
            while(!(ch == 72||ch == 75||ch == 77||ch == 80||ch == 119||ch == 97||ch == 115||ch == 100)) //防止误触
            {
                if(ch == 't') //标记音效
                {
                    f = 1;
                }
                else if (ch == 'f')
                    f = 0;
                ch = getch();
            }
            if(ch==72||ch==75||ch==77||ch==80) //Player One
            {
                GoToXYSpace(ch);//清除上次位置
                Direction(ch);//判断输入方向
                MoveEmoji();//移动表情
                CountNum(x1,y1); //统计数字个数
            }
            else	//Player Two
            {
                GoToXYSpace(ch);
                Direction(ch);//判断输入方向
                MoveEmoji();
                CountNum(x2,y2);
            }
            Information();
            if(CheckLeftNum())
            {
                int endTime = clock();
                int time = endTime - startTime;//计算用时

                step1 = 0;
    			step2 = 0;
                ChangeColor();
                Gotoxy(30,19);
                printf("<(￣︶￣)> 用时%d s~",time/1000);
                ChangeColor();
                if(num1>num2)
                    MessageBox(NULL,"玩家1获胜","QvQ",MB_OK);
                else
                    MessageBox(NULL,"玩家2获胜","QvQ",MB_OK);
            	num = 0;
                num1 = 0;
                num2 = 0;
                break;
            }
        }
    }
}

//选择哪种游戏模式
void Switch()
{
	while(flag != 0)
    {
        if(flag == 1)
        {
            OneP(); //单人模式
        }
        else if(flag == 2)
        {
            TwoP(); //双人模式
        }
    }
}

int main()
{
    SetConsoleTitle("数字迷宫v 1.3");//设置标题
    system("color 3f");
    Load();//进度条效果
    ShowMain();
    Switch();
    return 0;
}
