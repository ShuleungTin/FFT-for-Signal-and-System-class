#include<iostream>
#include<math.h>
using namespace std;
const double PI = 3.1415926;
int main()
{
	//读文件存在两个数组中
	long double *ReadReal = new long double[N];
	long double *ReadImg = new long double[N];
	long double *CoutReal = new long double[N];
	long double *CoutImg = new long double[N];
	int *usd = new int[N];                               //倒叙重排，只在逻辑上重排
	for (int i = 0; i < N; i = i + 2)                    //进行第一遍计算
	{
		CoutReal[i] = ReadReal[usd[i]] + ReadReal[usd[i + 1]];
		CoutImg[i] = ReadImg[usd[i]] + ReadImg[usd[i + 1]];
		CoutReal[i + 1] = ReadReal[usd[i]] - ReadReal[usd[i + 1]];
		CoutImg[i + 1] = ReadImg[usd[i]] - ReadImg[usd[i + 1]];
	}
	long double AccessoryReal;                           //需要一个辅助空间
	long double AccessoryImg;
	for (int j = 2; j <= N / 2; j = 2 * j)               //蝶形图计算
	{
		for (int k = 1; k <= N;)
		{
			AccessoryReal = CoutReal[k - 1] + CoutReal[k - 1 + j] * cos(PI*((k - 1) % j) / j) + CoutImg[k - 1 + j] * sin(PI*((k - 1) % j) / j);
			AccessoryImg = CoutImg[k - 1] + CoutImg[k - 1 + j] * cos(PI*((k - 1) % j) / j) - CoutReal[k - 1 + j] * sin(PI*((k - 1) % j) / j);
			long double AccessoryReal_ = CoutReal[k - 1 + j];
			CoutReal[k-1+j]= CoutReal[k - 1] -CoutReal[k - 1 + j] * cos(PI*((k - 1) % j) / j) - CoutImg[k - 1 + j] * sin(PI*((k - 1) % j) / j);
			CoutImg[k-1+j]= CoutImg[k - 1] - CoutImg[k - 1 + j] * cos(PI*((k - 1) % j) / j) + AccessoryReal_ * sin(PI*((k - 1) % j) / j);
			CoutReal[k - 1] = AccessoryReal;
			CoutImg[k - 1] = AccessoryImg;
			if ((k + 1) % j == 1)
				k = k + j + 1;
			else k++;
		}
	}
}
