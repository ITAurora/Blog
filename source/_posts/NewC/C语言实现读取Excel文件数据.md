---
title: C语言实现读取Excel文件数据
date: 2023-08-23 10:10:10
tags:
  - C
categories:
  - C语言
index_img: ../tnt/27.jpg
banner_img: ../tnt/27.jpg
excerpt: 摘要
---

```c
#include <stdio.h>
void main()
{   
    FILE *fp;
    char filename[40]  ;
    int i,j ;
    float da[6][5] = {0} ;
    // printf(" 输入文件名: ");
    // gets(filename);
    fp=fopen("D:\\test.xls","r");
    fseek(fp, 0, SEEK_SET);   // 从文件第一行开始读取
    for(i = 0 ;i < 6  ; i++)
        for(j = 0 ;j < 5 ; j++)
		{
			fscanf(fp,"%f",&da[i][j]);
			fseek(fp, 1L, SEEK_CUR);   /*fp指针从当前位置向后移动*/
		}
           
	for(i = 0 ;i < 6 ; i++)
        printf("%f\t%f\t%f\t%f\t%f\t\n",da[i][0],
         da[i][1],da[i][2],da[i][3],da[i][4]);

	getchar() ;
}

```
