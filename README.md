

<div align=center><img src="./picture/01.svg"/></div>

# Edge-Computing-Engine

## Edge : 一个开源的科学计算引擎				

[README for English_version](./README_EN.md)

[![license](https://img.shields.io/github/license/mashape/apistatus.svg?maxAge=2592000) ](https://github.com/AllenZYJ/Edge-Computing-Engine/blob/add-license-1/LICENSE)![](https://img.shields.io/badge/Bulid-Version1.0-green.svg)

> 项目开始日期 : 2019/10/01

> 目前项目总代码 : 709 行
>
> 测试代码 : 810 行
>
> 测试环境:
>
> MacBook Pro
>
> 编译器环境:
>
> Configured with: --prefix=/Applications/Xcode.app/Contents/Developer/usr --with-gxx-include-dir=/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.14.sdk/usr/include/c++/4.2.1
> Apple LLVM version 10.0.1 (clang-1001.0.46.4)
> Target: x86_64-apple-darwin18.7.0
> Thread model: posix
>
> 实现的:

如何安装和运行基于Edge的测试demo.

`git clone git@github.com:AllenZYJ/Edge-Computing-Engine.git`

进入到clone 之后的目录

`cd to this dir `

编译demo入口程序

`g++ main.cpp -o main`

`'./main'`

输出最终损失和参数迭代结果.

-----------split-line-----------
2.79955
0.36431
-0.451694
epoch: 100 error: 6.05895
-----------split-line-----------
0.009167(sum of loss)

### 目前实现的程序接口
Matrix API:

- [x] Matrix read_csv(string &file_path)读取格式化文件(csv),返回一个自动计算长度的矩阵.

- [x] Create a matrix :  create(row,cols)开辟一个矩阵结构的内存,元素初值为0;

- [x] Change the element for matrix void move_ele(int &ele1, int &ele2),修改某一个位置的元素的值.

- [x] Matrix1+Matrix2 : Matrix add(Matrix mid1,Matrix mid2,int flag=1),矩阵加和操作接口,可选位运算加速.

- [x] Flag is how to compete the ele ,default 1 ,bitwise operation(位运算加速).

- [x] Matrix1-Matrix2 : Matrix subtract(Matrix mid1,Matrix mid2)

- [x] Matrix1*Matrix2 : Matrix mul(Matrix mid1,Matrix mid2)

- [x] Matrix1*n : Matrix times_mat(int times,Matrix mid1)

- [x] Matrix1's Transposition : Matrix get_T(Matrix mid1)矩阵转置

- [x] Mul(matrix1,matrix2)矩阵乘积(完整数学定义).

- [x] double* flatten(Matrix mid1) : Return a flattened array.矩阵展开

- [x] Matrix matrix_rs(Matrix mid1,int rs_row,int rs_col) 矩阵的结构压缩

- [x] double matrix_sum(Matrix mid1)矩阵求和

- [x] double matrix_mean(Matrix mid1)均值

- [x] Matrix appply(Matrix mid1,Matrix mid2,int axis = 0)矩阵拼接

- [x] Matrix iloc(Matrix mid1,int start_x=0,int end_x=0,int start_y=0,int end_y=0)矩阵切片

- [x] Matrix mul_simple(Matrix mid1,Matrix mid2)为了贴合机器学习的需要,实现了矩阵对应元素相乘,请与传统意义的矩阵乘法区分开.

  ### 即将着手开发:

- [ ] 卷积神经网络定义(包括但不限于卷积核,池化层定义,自定义损失接口).

- [ ] 随机森林算法封装.

- [ ] 主流网络架构实现.

  

## 演示:矩阵乘法

Matrix **A**：

| 第1列   | 第2列   | 第3列   | 第4列   | 第5列   |
| ------- | ------- | ------- | ------- | ------- |
| 72.0000 | 0.0000  | 0.0000  | 0.0000  | 0.0000  |
| 0.0000  | 64.0000 | 0.0000  | 0.0000  | 0.0000  |
| 16.0000 | 8.0000  | 0.0000  | 0.0000  | 0.0000  |
| 0.0000  | 0.0000  | 56.0000 | 16.0000 | 32.0000 |
| 0.0000  | 0.0000  | 0.0000  | 0.0000  | 0.0000  |
| 0.0000  | 0.0000  | 0.0000  | 0.0000  | 0.0000  |

MAtrix **B**：

| 第1列   | 第2列   | 第3列   | 第4列   | 第5列  | 第6列  |
| ------- | ------- | ------- | ------- | ------ | ------ |
| 72.0000 | 0.0000  | 16.0000 | 0.0000  | 0.0000 | 0.0000 |
| 0.0000  | 64.0000 | 8.0000  | 0.0000  | 0.0000 | 0.0000 |
| 0.0000  | 0.0000  | 0.0000  | 56.0000 | 0.0000 | 0.0000 |
| 0.0000  | 0.0000  | 0.0000  | 16.0000 | 0.0000 | 0.0000 |
| 0.0000  | 0.0000  | 0.0000  | 32.0000 | 0.0000 | 0.0000 |

To

| 第1列     | 第2列     | 第3列     | 第4列     | 第5列  | 第6列  |
| --------- | --------- | --------- | --------- | ------ | ------ |
| 5184.0000 | 0.0000    | 1152.0000 | 0.0000    | 0.0000 | 0.0000 |
| 0.0000    | 4096.0000 | 512.0000  | 0.0000    | 0.0000 | 0.0000 |
| 1152.0000 | 512.0000  | 320.0000  | 0.0000    | 0.0000 | 0.0000 |
| 0.0000    | 0.0000    | 0.0000    | 4416.0000 | 0.0000 | 0.0000 |
| 0.0000    | 0.0000    | 0.0000    | 0.0000    | 0.0000 | 0.0000 |
| 0.0000    | 0.0000    | 0.0000    | 0.0000    | 0.0000 | 0.0000 |

## 演示: 矩阵展开(flatten).

double* flatten(Matrix mid1)

|  1   |  2   |  3   |
| :--: | :--: | :--: |
|  2   |  4   |  6   |
|  7   |  8   |  9   |

​	To

| 1    | 2    | 3    | 2    | 4    | 6    | 7    | 8    | 9                  |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | :----------------- |
|      |      |      |      |      |      |      |      | Like numpy.flatten |

function:

## 演示: 邻接矩阵的参数定义:

​	Matrix appply(Matrix mid1,Matrix mid2,int axis = 0)

> 参数 axis=0 :

| 0    | 7    | 2    |
| ---- | ---- | ---- |
| 0    | 3    | 1    |
| 0    | 0    | 0    |
| 0    | 0    | 11   |
| 0    | 7    | 2    |
| 0    | 3    | 1    |
| 0    | 0    | 0    |
| 0    | 0    | 11   |
------

> axis = 1:

| 0    | 7    | 2    | 0    | 7    | 2    |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 0    | 3    | 1    | 0    | 3    | 1    |
| 0    | 0    | 0    | 0    | 0    | 0    |
| 0    | 0    | 11   | 0    | 0    | 11   |

------

## 更新2019/11/18/00:12

- [x] read_csv 通过文件流读取逗号分隔符文件,返回一个自动计算长度的矩阵.

  例如 CSV's head :

  | -0.017612 | 14.053064 | 0    |
  | --------- | --------- | ---- |
  | -1.395634 | 4.662541  | 1    |
  | -0.752157 | 6.53862   | 0    |
  | -1.322371 | 7.152853  | 0    |
  | 0.423363  | 11.054677 | 0    |
  | 0.406704  | 7.067335  | 1    |

  Get:

  ![](./picture/WX20191119-105411@2x.png)

  

  ## Logistic Regression demo base Edge:


```c
#include<iostream>
#include<ctime>
#include<string>
#include <time.h>
#include <math.h>
#include <fstream>
#include"./matrix/matrix_def.h"
#include"./matrix/matrix_pro.h"
#include"./welcome/score_wel.cpp"
#include"./logistic/logistic_def.h"
#include"./file_pro/data_read.h"
using namespace std;
clock_t start, stop;
double duration;
int main()
{
	welcome();	
	string path = "./new_data2.csv";
	Matrix data = read_csv(path);
	Matrix bais = CreateMatrix(data.row,1);		
	data = appply(data,bais,1);
	Matrix y = iloc(data,0,0,3,4);
	Matrix x_1 = iloc(data,0,0,0,3);
	Matrix x_2 = get_T(x_1);
	double alpha = 0.002;
	int max_epoch = 100;
	Matrix weight = CreateMatrix(3,1);
	change_va(weight,0,0,1);
	change_va(weight,1,0,1);
	change_va(weight,2,0,1);
	int epoch = 0;
	for(epoch = 0;epoch<=max_epoch;epoch++)
	{
	cout<<"-----------split-line-----------"<<endl;			
	Matrix temp_mul = mul(x_1,weight);
	Matrix h =e_sigmoid(temp_mul);
	Matrix error = subtract(y,h);
	Matrix temp_update = mul(x_2,error);
	Matrix updata = add(weight,times_mat(alpha,temp_update),0);
	cout_mat(weight);
	cout<<"epoch: "<<epoch<<" error: "<<matrix_sum(error)<<endl;
	cout<<"-----------split-line-----------"<<endl;	
	}
	stop = clock();
  printf("%f\n", (double)(stop - start) / CLOCKS_PER_SEC);
	return 0;
}
```
Something :

> 1. 矩阵元素默认为1
> 2. 使用位运算加速防止填充过大的数值,但是会损失一定精度,慎用.
> 3. 记得delete(matrix)在你使用完一个矩阵计算单元以后.
> 4. api接口更多的接近于pandas和numpy的使用习惯.
> 5. 更多的细节参见目前最新的代码
> 6. 欢迎star和关注.
>

------



<div align = center><img src = './picture/星月.svg'></div>



 个人小站:[极度空间](likedge.top)

作者邮箱:zk@likedge.top | edge@ibooker.org.cn

 QQ:2533524298