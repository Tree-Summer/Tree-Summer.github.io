---
title: matlab
date: 2024-01-19 22:08:18
tags:
- method
---
## 语法
* t="qaq"定义字符串变量，加法直接在后面加,但是在数组里占一格
* t=‘DNA’是字符，存三个字符，s=t(3) //s的值为A，char类型不能加，添加用[t,'www']
* 如果一个操作数是标量，另一个操作数不是标量，matlab会将该标量隐式扩展为与另一个操作数具有相同的大小

## 函数
* [D,V]=eig(A) 求特征向量
* B=A' 求转置
* E=inv(A) 求逆矩阵
* C=A*B 矩阵乘法
* E=A.*B 矩阵点乘，对应元素相乘
* x=A\b等效于inv(A)*b
* **linprog函数**：求解线性规划问题<br>
[x,fval,exitflag]=linprog(f,A,b,Aeq,beq,lb,ub)<br>
Linprog输入：<br>
f是目标函数的系数矩阵<br>
A是线性规划不等式约束的变量系数矩阵<br>
b是不等式约束的资源数<br>
Aeq和beq是相应等式约束的变量系数矩阵和资源数<br>
lb和ub为保变量的上下区间<br>
linprog返回值：
x为求得的各变量的值，fval为最优化的值，exitflag是函数的退出标志


* [ intlinprog:整数约束变量](https://blog.csdn.net/f_h_h/article/details/100537394)：<br>
intcon ：整数所在位置<br>
 
 * 输出：disp（a）
 * 输入：a=input("请输入a的值")
 * plot（b）画图
 * grid on 添加网格线
 
* **[function](https://blog.csdn.net/qq_25018077/article/details/88998126)**：<br>
 function [y1,...,yn]=myfun(x1,...,xm)
<br>前面是输出，后面是输入

* **fmincon**：<br>
    [x,val]=fmincon(fun,x0,A,b,Aeq,beq,lb,ub,nonlcon)
    fun:单独脚本文件里定义的目标函数<br>
    x0:决策变量的初始值<br>
    nonclcon:非线性约束，包括不等式和等式
    ![加载不出来了qwq](https://www.freeimg.cn/i/2024/01/21/65ad229922aa0.png)
```
            function f=fun1(x);
            f=sum(x.^2)+8;  %编写目标函数
            end
            %记得写在函数文件里
```
```
            function [g,h]=fun2(x);
            g=[-x(1).^2+x(2)-x(3).^2;x(1)+x(2).^2+x(3)^2-20];
            h=[-x(1)-x(2).^2+2;x(2)+2*x(3).^2-3];
            end%约束函数，g是不等式约束，h是等式约束
```
最后求解用[x,y]=fmincon('fun1',rand(3,1),[],[],[],[],zeros(3,1),[],'fun2')即可
 
 * 读入excel文件处理
```
[tx,str]=xlsread('Problem_C_Data_Wordle.xlsx');
time=tx(:,1);
Altitude=tx(:,3);
```
 
* sort函数原数组是不改动的，需要将sort后的返回值记录下来

* [fit,fittype曲线拟合](https://blog.csdn.net/dsydsylove/article/details/116225942)
* beta分布
```
data1 = betarnd(4,3,100,1);%生成符合beta分布的数值
data1=sort(data1);%排序方便下面看数值长啥样
plot(data1)
hold on;
[p,ci] = betafit(data1,0.01);%拟合
x=0:0.01:1;
y=betapdf(x,p(1,1),p(1,2));%求概率密度
plot(x,y);
xlabel('x');
ylabel('y');
```
* 用已有的拟合模板（见下面官方文档链接）拟合曲线
```
[fit_result,gof]=fit(x,y,'poly7');%x是自变量，y是因变量，poly7是可替换的
disp(fit_result);
plot(fit_result,x,y);
```

 ## 文件
* 编程文件：写了运行命令行弹出结果
* 实时文件：左边代码右边结果，点击文本后可以插入图片，使用markdown语法
* 函数文件：无法直接使用，在脚本文件中调用



## 符号
* %后面是注释
* 写完一行代码末尾加分号会执行运算但是不在命令行窗口输出（不写就输出了是吧qaq）
- 命令行：
  - clc（清空命令行）
  - clear（清空工作区）
  - 按向上方向键调用历史命令
- 快捷键：
  -  ctrl+N新建脚本
  - ctrl+Z撤销，ctrl+Y撤销过头时回溯
   - ctrl+F 查找或替换变量名
   - F5保存并运行
   - F10单步执行
   - F9运行代码选中片段
   - ctrl+r片段注释，ctrl+t注销
   - ctrl+e实时脚本文字，代码转换
   - ctrl+j:自动整理注释
   - ctrl+i：智能缩进代码
  
## 官方文档
[一些模型的中英对照](https://ww2.mathworks.cn/help/curvefit/list-of-library-models-for-curve-and-surface-fitting.html#btbcxna-1)
