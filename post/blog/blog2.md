## 递归
* 递归必须满足三个条件：

    1、递归必须有一个明确的终止条件 

    2、该函数所处理的数据规模必须递减 

    3、这个转化必须是可解的

* 定义：一个函数自己直接或间接调用自己

* 不同函数之间的相互调用
    
        #include
        <stdio.h>
        void f();
        void g();
        void k();
        void f()
        {
            printf("FFF\n");
            g();
            printf("1111\n");
        }
        void g()
        {
            printf("GGG\n");
            k();
            printf("2222\n");
        }
        void k()
        {
            printf("KKK\n");
        }
        int main(void)
        {
            f();
        }
* 结果为FFFGGGKKK22221111

* 自己调用自己
        
        #include
        <stdio.h>
        void f()
        {
            printf("haha\n");
            f();
        }
        int main(void)
        {
            f();
        }
* 一直输出haha直到溢栈

        #include<stdio.h>
        void f(int n)
        {
            if(n==1)
            {
                printf("haha\n");
            }
            else
            {
                f(n-1);
            }
        }
        int mian(void)
        {
            f(3);
        }

* 求阶乘
* 2的阶乘要依靠1的阶乘实现，3的阶乘要依靠2的阶乘来实现，以此类推

        #include<stdio.h>
        int main(void)
        {
            int val,i,mult=1;
            printf("请输入一个数字：val=");
            scanf("%d",&val);

            for(i=1;i<val;++i)
            {
                mult*=i;
            }
            printf("阶乘为：%d",mult);
        }
* 此程序会溢出


* 运用递归的算法

        #include<stdio.h>
        //假定n的值是1或大于1的值
        long f(long val)
        {
            if(1==n)
            {
                return 1;
            }
            else
            (
                return f(n-1)*n;
            )
        }
        int mian(void)
        {
            printf("%ld\n",f(3));
        }
* 结果为6


* 1到100的和

        #include<stdio.h>
        long sum(int n)
        {
            if(1==n)
            {
                return 1;
            }
            else
            {
                return sum(n-1)+n;
            }
        }
        int main(void)
        {
            printf("%ld",sum(100));
        }


* 汉诺塔（用递归）
* 伪算法：

        if(n>1)
        {
            先把A柱子上的n-1个盘子从A借助C移到B
            将A柱子上的第n个盘子直接移到C
            再将珠子上的n-1个盘子借助A移到C
        }


* 真的代码：
        
        #include<stdio.h>
        void hannuota(int n,char A,char B, char C);
        //第一个参数表示放盘子的位置（初始位置），第二个参数表示借助的柱子（中间柱子），第三个参数表示目标柱子
        int main(void)
        {
            //先定义三个柱子
            char ch1='A';
            char ch2='B';
            char ch3='C';
            int n;//要移动盘子的个数;

            printf("请输入要移动的盘子的个数：");
            scanf("%d",&n);

            hannuota(n,'A','B','C');
        }
        void hannuota(int n,char A,char B, char C)
        {
            /*如果是1个盘子
            直接将A柱子上的盘子移到C
            否则
            先将A柱子上的n-1个盘子从A借助C移到B
            直接将A柱子上的盘子从A移到C
            最后将B柱子上的n-1个盘子借助A移到C*/
            if(1==n)
            {
                printf("将编号为%d的盘子直接从%c柱子移到%c柱子"，n,A,C);
            }
            else
            {
                hannuota(n-1,A,C,B);
                printf("将编号为%d的盘子直接从柱子%c移动到柱子%c\n",n,A,C);
                hannuota(n-1,B,A,C);
            }
        }



* 间接调用自己

        #include<stdio.h>
        void f(int n)
        {
            g(n);
        }
        void g(int m)
        {
            f(m);
        }
        int main(void)
        {
            f(4);
        }


* 递归和循环关系：

1、递归易于理解、存储空间大，但速度慢

2、循环相反，不易理解、存储空间小（几乎不占用）、但速度快

递归的应用：树和森林就是以递归的方式定义的、树和图的很多算法都是以递归来实现的、很多数学公式就是以递归的方式定义的（斐波那契数列）
