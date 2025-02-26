---
title: C语言实现生成Excel文件并写入所需数据
date: 2023-11-22 10:10:10
tags:
  - C
categories:
  - C语言
index_img: ../tnt/26.jpg
banner_img: ../tnt/26.jpg
excerpt: 摘要
---

```c
#include <stdio.h>
void writeExcel()
{
	remove("D:\\test.xls");
	int data[7]={ 1 , 3 , 6 , 9 , 10 , 4.07 , -14.12};
	int i ;
	FILE *fp = NULL ;
	fp = fopen("D:\\test.xls","w") ;
	for (i=0 ; i<7 ;i++)
		fprintf(fp,"%d\t%d\t%d\t%d\t%d\n",data[i],data[i],data[i],data[i],data[i] ) ;
	fclose(fp);
}

void main()
{					
	writeExcel();	
}
```
