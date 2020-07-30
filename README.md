## 题目

 设计并测试一个函数，从一行输入中把一个单词读入一个数组中，并丢弃输入行中的其余字符。该函数应该
 跳过第一个非空白字符前面的所有空白。将一个单词定义为没有空白/制表符或换行符的字符序列。
 
##编程分析：
  程序的目的是从输入中读取第一个单词，并舍弃其他字符。
  针对这种特殊需求，首先应当判断单词的开始位置和结束位置，
  判断标准为以非空白字符作为单词的开始，以空白字符作为结束（题目要求并未排除标点符号，只排除空白字符）。
  
#完整代码：
#include<stdio.h>
#include<ctype.h>  /*为了使用isalpha(),需要添加该头文件*/
#define SIZE 80
char * get_word(char*out);

int main(int argc, char *argv[])
{
	char output[SIZE];
	get_word(output);
	printf("First word you input is : %s",output);
	return 0;
	
} 
char * get_word(char *out)
{
	char input[SIZE];
	char*in=input;
	puts("Enter a String:");
	fgets(input,SIZE,stdin);
	
	while((*in == '\n'|| *in == '\t' || *in == ' ')&& *in !='\0')
		in++;
	/*  通过while循环删除字符串前面的空白。此处需要注意无单词的字符串。
	 * 当前代码只删除指定的字符，通常可以使用isalpha()来判断字符是
	 * 否是英文字符，这样可以删除多种标点符号和特殊字符，可读性更高
	 * */
	
	while(*in != '\n' && *in != '\t' && *in != ' ' && *in != '\0')
	{
		*out++ = *in++;
	}
	/* 从第一个非空白字符开始复制，直到单词结束，这里同样可以使用isalpha()。
	 * 题目未要求输出到字符串，因此可以结束。如果需要保存至字符串中，添加
	 * *out++ = '\0';
	 * */
	
	return out; 
}
