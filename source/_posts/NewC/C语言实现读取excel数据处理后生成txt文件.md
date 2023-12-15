---
title: C语言实现读取excel数据处理后生成txt文件
date: 2023-08-28 10:10:10
tags:
  - C
categories:
  - C语言
index_img: ../tnt/28.jpg
banner_img: ../tnt/28.jpg
excerpt: 摘要
---


```c
#include <stdio.h>
#include <malloc.h>
void  main()
{   remove("D:\\newtest.txt");
    FILE *fp;
    FILE *nw = NULL ;
    nw = fopen("D:\\newtest.txt","w") ;
    char filename[40]  ;
    int i,j ;
      int m, n;
      n=3;
      printf("请输入行数:");
      scanf("%d", &m);
      float** da = (float**)malloc(sizeof(float*) * m);
      for (i = 0; i < m; i++) {
	  *(da+i) = (float*)malloc(sizeof(float) * n);
      }
    fp=fopen("D:\\test.xls","r");
    if (fp == NULL)
	{
		perror("打开文件失败啦");
	}
    fseek(fp, 0, SEEK_SET);   // 从文件第一行开始读取
    for(i = 0 ;i < m  ; i++)
        for(j = 0 ;j < 3 ; j++)
		{
			fscanf(fp,"%f",&da[i][j]);
			fseek(fp, 1L, SEEK_CUR);   /*fp指针从当前位置向后移动*/
		}
           
	for(i = 0 ;i < m ; i++)
        printf("%d\t%.3f\t%.3f\t%.3f\t\n",i,da[i][0],
         da[i][1],da[i][2]);
         
    float num1=0;
    float num2=0;
    float num3=0;
    int day=0;
    for(i = 1 ;i <= m ; i++)
    
    if (i%24==0)
    {   day+=1;
        num1+=da[i-1][0];
        num2+=da[i-1][1];
        num3+=da[i-1][2];
        printf("第%d天的值:%.3f\t%.3f\t%.3f\t\n",day,num1,num2,num3);
        char temp[30]="";
        sprintf(temp, "第%d天:", day);
        // fprintf(nw ,"%d\t%.3f\t%.3f\t%.3f\n",i,da[i-1][0],da[i-1][1],da[i-1][2] ) ;
        fprintf(nw ,"%s\t%.3f\t%.3f\t%.3f\n",temp,num1,num2,num3 ) ;
        num1=0;
        num2=0;
        num3=0;
    }else{
        num1+=da[i-1][0];
        num2+=da[i-1][1];
        num3+=da[i-1][2];
        // fprintf(nw ,"%d\t%.3f\t%.3f\t%.3f\n",i,da[i-1][0],da[i-1][1],da[i-1][2] ) ;
    };
	getchar() ;
}

```

