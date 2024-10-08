# 51
## main.c
```
#include <regx52.h>
#include  "1602.h"
void main()
{
	LCD_Init();
	LCD_ShowChar(1,1,'B');
	whlie (1)
	{
		
	}
}
```
## 1602.c
```
#include <REGX52.H>
sbit RS=P2^0;
sbit Rw=P2^1;
sbit E=P2^2;
#DEFINE LCD_DataPort P0
void yanshi(unsigned int A)	//@12.000MHz,
{
	unsigned char data i, j;
	while(A)
	{	
				i = 2;
				j = 239;
				do
				{
					while (--j);
				} while (--i);
				A--;
	}
}
//????yanshi??
//??yanshi(100);
void LCD_WriteCommand(unsigned char Command)//
{
		RS=0;
		RW=0;
		LCD_DataPort=Command;
		E=1;
		yanshi(100);
		E=0;
		yanshi(200);
}
void LCD_WriteData(unsigned char Command)
{
		RS=1;
		RW=0;//
		LCD_DataPort=Data;
		E=1;
		yanshi(100);
		E=0;
		yanshi(200);
}
void LCD_Init(void)//???
{
		LCD_WriteCommand(0x38);
		LCD_WriteCommand(0x0c);
		LCD_WriteCommand(0x06);
		LCD_WriteCommand(0x01);
}
void LCD_ShowChar(unsigned char Line/*?*/,unsigned char Column/*?*/,unsigned char char)
{
    if (Leine == 1)
    {
        LCD_WriteCommand(0x80|(Column-1));
    }
    else
    {
        LCD_WriteCommand(0x80|(Column-1)+0x40); 
    }
    //??????
    LCD_WriteData(char)
}
```
## 1602.h
```
#ifndef _1602_H_
#define _1602_H_
void LCD_Init(void)//???
void LCD_ShowChar(unsigned char Line/*?*/,unsigned char Column/*?*/,unsigned char char)
#endif
```
## 错误
```
Build started: Project: main
Build target 'Target 1'
compiling main.c...
1602.h(4): error C141: syntax error near 'char', expected 'hdata'
main.c(3): error C132: '_LCD_ShowChar': not in formal parameter list
main.c(3): error C141: syntax error near 'void', expected ';'
main.c(4): error C132: 'main': not in formal parameter list
main.c(4): error C141: syntax error near '{', expected ';'
main.c(5): error C132: 'LCD_Init': not in formal parameter list
main.c(6): error C141: syntax error near '1', expected 'bit'
main.c(6): error C132: 'LCD_ShowChar': not in formal parameter list
main.c(7): error C141: syntax error near '1', expected 'bit'
main.c(8): error C132: 'whlie': not in formal parameter list
main.c(8): error C141: syntax error near '{', expected ';'
compiling 1602.c...
1602.c(5): warning C315: unknown #directive 'DEFINE'
1602.c(25): error C202: 'RW': undefined identifier
1602.c(26): error C202: 'LCD_DataPort': undefined identifier
1602.c(35): error C202: 'RW': undefined identifier
1602.c(36): error C202: 'LCD_DataPort': undefined identifier
1602.c(49): error C141: syntax error near 'char', expected 'hdata'
1602.c(51): error C202: 'Leine': undefined identifier
1602.c(60): error C141: syntax error near 'char', expected 'sizeof'
Target not created.
Build Time Elapsed:  00:00:01
```
