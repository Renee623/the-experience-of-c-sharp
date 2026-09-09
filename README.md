# the-experience-of-c-sharp
------------------------------------------------------------------基础
## 复杂数据（变量）
特点：数据集合
自定义
枚举，数组，结构体
## 枚举
### 基本概念
是一个被命名的整形常量的集合
一般用它表示状态，类型
### 在哪里申明
声明枚举：创建一个自定义的枚举类型
enum E_自定义枚举名（以E或E_开头 ）
{
	自定义枚举项，
	自定义枚举项[,]枚举中包裹的整型常量默认第一个默认值是0，可赋值，下面依次累加，从上一个的值累加，被命名的整型常量
	
}
声明枚举变量：

在namespace里声明枚举常用，也可声明在class和结构体内
注意枚举不能在函数块里声明
enum E_MonsterType{
	Normal,
	Boss,
}
enum E_PlayerType{
	Main,
	Other,
}
### 使用
声明枚举变量，在函数中声明
E_PlayerType playertype = E_PlayerType.Main;
自定义枚举类型 变量名 = 默认值(自定义枚举类型.枚举项)
枚举和switch天生一对
### 类型转换,少用
在函数内进行
#### 枚举和int
int i  = (int) playertype
#### 枚举和string
枚举转string
string str = playertype.ToString;
打印枚举项的名字
string转枚举
playertype =(E_PlayerType)Enum.Parse(typeof(E_PlayerType),"Other")
第一个参数代表转换成什么类型的枚举
第二个参数代表转成前面枚举里有的枚举项，用于转换的对应的枚举项的字符串
转完是通用类型
需要括号前面强转
### 作用
游戏开发中对象很多时有许多的类型，许多的状态
我们需要用一个变量或标识来表示玩家处于哪种状态
我们可能需要int
那么只通过数字来判断很难理解，尤其在没有注释
那么枚举就可以知道代码的意思，通过.枚举项

///注释可以在用的时候指上去有提示窗口说明
int.Parse()
## 数组
### 基本概念
储存一组相同类型的数据的集合
内存是一组连续的空间，有默认的编号
### 数组声明
1.变量类型[]数组名，只是声明了，但是不存在内存中
变量类型可以是我们学过的没学的所有类型，包括枚举
2.变量类型[]数组名 = new 变量类型[数组长度]
int []arr = new int[3];,new代表在内存中新开n个房间，房间里的数值为默认值0
3.变量类型[]数组名 = new 变量类型[数组长度]{具体内容}
int[]arr = new int[3]{0,1,0};
4.变量类型[]数组名 = new 变量类型[]{具体内容}
即不写长度，但是写了具体内容，会自动分配具体数量的房间
5.变量类型[]数组名 = {具体内容}
### 数组使用
int []arr = new int[]{1,2,3,4,5,6}
#### 1.数组长度
arr.Length
#### 2.获取数组中元素
index，即数组有下标和索引，从0开始，不能越界，c#中没有负索引
arr[0];
arr[1];
#### 3.修改数组中的元素
直接重新赋值,同类型
arr[0] = 2;
#### 4.遍历数组
for(int i = 0;i < arr.Length; i++){

	Console.WriteLine(arr[i]);

}或者
foreach(int i in arr){

	Console.WriteLine(i);

}
#### 5.增加数组的元素
数组在初始化之后，是不能直接添加新元素的
只有搬家，即搞个新数组
`int []arr = new int[3]{1,2,3};`
`int[]array = new int[4];`
`for (int i = 0; i < arr.Length ;i++){`
	
	array[i] = arr[i];//相当于一个个赋值过来
	
`}`
`arr = array;` 
`arr[4] = 6;`
#### 6.删除数组中的元素
和上面一样,搬家,删除最后一个元素
`int [] arr = new int[4]{1,2,3,4};`
`int[]array = new int[3];`
`for(int i = 0;i < array.Length;i++){
	`array[i] = arr[i];`

}
`arr = array;`
#### 7.查找数组中的元素
遍历
`int[] arr = new int[]{1,2,3,4,5,6,7,8,9};`
`int j = 3`
`for(int i = 0;i < arr.Length;i++){

	if(arr[i] == j){
		Console.WriteLine($"和j相等的元素在索引{i}");
	}

}`
### 二维数组
#### 基本概念
相当于矩阵，有行列
即多行一维数组
#### 申明
*1.变量类型[，] 二维数组变量名；*
`int [,] arr;`未初始化
*2.变量类型[，]二维数组名 = new 变量类型[行，列];*
`int [,]arr = new int[3,4];`默认放0
*3.变量类型[，]二维数组名 = new 变量类型[行，列];*
`int[,]arr = new int[3,4]{{1,2,3,4},{2,3,4,5},{3,4,5,6}};`
*4.变量类型[，]二维数组名 = new 变量类型[，]{{},{},{},{}...}*
`int[,]arr = new int[,]{{},{},{},...};`
*5.变量类型[，]二维数组名 = {{},{},{},{},{}...};*
`int[,]arr = {{},{},{},{}...};`
#### 使用
##### 二维数组的长度
`int[,] arr = new int[2,3]{{1,2,3},
						`{4,5,6}};`
`Console.WriteLine(arr.GetLength(0));//获取行数`
`Console.WriteLine(arr.GetLength(1));//获取列数`
##### 获取元素
`int[,] arr = new int[2,3]{{1,2,3},
						`{4,5,6}};`
`Console.WriteLine(arr[0,0]);//对应行和列交叉得到的元素`
行和列都是从0开始，不要越界
##### 修改元素
即重新赋值
`int[,]arr = new int[2,3]{{1,2,3},
						`{4,5,6}};`
`arr[0,0] = 99;`			
#### 遍历
`int[,]arr = new int[2,3]{{1,2,3},
					`{4,5,6}};`
`for(int i = 0; i < arr.GetLength(0);i++){

		for(int j = 0; j < arr.GetLength(1);i++){
		
			Console.WriteLine(arr[i,j]);
		
		}

}`
##### 增加
通过搬家的形式
`int[,]arr = new int[2,3]{{1,2,3},
					`{4,5,6}};`
`int[,]arr1 = new int[3,3];`
`for(int i = 0;i < arr.GetLength(0);i++){

		for(int j = 0;j < arr.GetLength(1);j++){
			
				arr1[i,j] = arr[i,j];
			
		}

}`
`arr = arr1;`
`arr[2,0] = 0;
`arr[2,1] = 1;
`arr[2,2] = 2;//之后挨个赋值`
##### 删除
通过搬家的形式
`int[,]arr = new int[3,3]{{1,2,3},
						`{4,5,6},
						`{7,8,9}};`
`int[,]arr1 = new int[2,3];`
`for(int i = 0;i < arr1.GetLength(0);i++){

		for(int j = 0;j < arr1.GetLength(1);j++){

			arr1[i,j] = arr[i,j];
		
		}

}`

##### 查找
通过遍历的形式查找
`int[,]arr = new int[2,3]{{1,2,3},
						`{4,5,6}};`
`int a = 6;`
`for(int i = 0;i < arr.GetLength(0); i++){

		for(int j = 0;j < arr.GetLength(1);j++){

				if(arr[i,j] == a){
				
					Console.WriteLine($"(i,j)");
				}

		}

`}`
### 交错数组
#### 基本概念
数组的数组，每个维度的数量可以不同
交错数组的列数可以不同
#### 声明
*1.变量类型[][] [] 交错数组名；*
`int [][]arr;//没有内存空间，没有初始化`
*2.变量类型[][][] 交错数组名 = new 变量类型【行数】【】；*
`int[][]arr = new int [3][];//列数不定不能写死`
*3.变量类型[][][]变量数组名 = new 变量类型【行数】【】{一维数组1，一维数组2，......}；*
`int[][]arr = new int[3][]{new int[]{1,2,3},new int[]{1,2},new int[]{1,2,3,4}};`
*4.变量类型[][][]变量数组名 = new 变量类型【】【】{一维数组1，一维数组2，....};*
`int[][]arr = new int[][]{new int[]{1,2,3},new int[]{1,2},new int[]{1}};`
*5.变量类型 [][][]变量数组名 = {一维数组1，一维数组2，...};*
`int[][]arr = {new int[]{1,2,3},new int[]{1,2},new int[]{1}};`
#### 使用
##### 1.长度
`int [][]arr = new int[2][]{new int []{1,2,3},new int[]{4,5}};`
`Console.WriteLine(arr.GetLength(0));//行数是固定的`
`Console.WriteLine(arr[0].Length);//得到每一行的列数(长度)`
##### 2.获取元素
`int[][]arr = new int[2][]{new int[]{1,2,3},new int[]{1,2}};`
`Console.WriteLine(arr[0][1]);//第零行第一列`
##### 3.修改元素
直接等于一个值，重新赋值
##### 4.遍历
`int[][]arr = new int[2][]{new int[]{1,2,3},new int[]{1,2}};`
`for(int i = 0;i < arr.GetLength(0);i++){

		for(int j = 0; j < arr[i].Length;j++){
		
			Console.WriteLine(arr[i][j]);
		}

}`
##### 5.增加
##### 6.删除
##### 7.查找
### 值类型和引用类型
#### 变量类型的复习
##### 1.无符号整型
byte 0-255,1字节
ushort
uint
ulong
##### 2.有符号整型
sbyte
short
int
long
##### 3.浮点数
decimal
float
double
##### 4.特殊类型
string
char
bool
##### 5.复杂数据类型
枚举
数组
结构体

引用类型：string，数组，类
值类型：其他，结构体
#### 值类型和引用类型的区别
区别：
`int a = 10;`
`int[]arr = new int[]{1,2,3,4};`
`int b = a;`
`int[]arr1 = arr;//结果是b = 10，arr1里的元素和arr里一样`
`b = 20;
`arr1[0] = 5;//结果是a = 10，b = 20，但arr[0]和arr1[0]都等于5`
**值类型在相互赋值时，把相应内容copy过来，它变我不变**
**引用类型在相互赋值时，是让两个指向同一个值，它变我也变**
值类型和引用类型在内存区域存储方式不同，在使用上有区别
值类型存储在栈空间，栈是系统分配的空间，会自动回收，小而快
引用类型存储在堆空间，需要手动申请和释放，大而慢
即对于引用空间而言，其在栈空间里存储一个指向堆空间的地址，相互赋值时，拷贝的也是地址
而对于值类型其相互赋值时，是拷贝内容并开了一个新空间
**new的话就会新开一个房间**
`arr1 = new int[]{99,2,3,4};//arr[0] = 5,但arr1[0] = 99`
此时new完之后栈空间上存了一个新地址，指向堆空间里的房间
#### 特殊的引用类型string
**string它变我不变**
`string str = "123";`
`string str1 = str;`
`str1 = "321";//结果是str仍然是“123”，str1是“321”`
缘由是c#中给string赋予了值类型的特征，相当于new了一个string，即其重新赋值时，会在栈空间中给一个新地址
但是string每次在重新赋值时，会产生许多内存垃圾
**通过断点调试，可以查看内存信息**
调试-窗口-监视
## 函数（方法）
### 基本概念
具有名称的代码块，封装代码，提升复用率，少写点代码，抽象行为，可以使用函数的名称来执行代码块
`Console.WriteLine();//就是一个函数`
可以右键f12跳转一些函数的定义
抽象行为即如何操作能执行行为到控制台
### 写在哪里
写在class里，或结构体struct语句块中
### 语法
对照main
`static void Main(string[]args){
...
}`
static 返回类型 函数名(参数类型 参数名1，参数类型 参数名2，......){

		//语句块，封装的逻辑
		//return返回值;(可选，有返回类型才返回)
}
**1.static不是必须的，但在学class和struct前，默认写上去
2.void代表没有，即没有返回值
3.返回类型可以是任意变量类型，包括复杂数据类型，class，struct
4.函数名是你自己给下面的代码块取得名字，必须是帕斯卡命名即每一个单词的首字母必须大写
`//驼峰命名 myName，帕斯卡命名 MyName`
5.参数不是必须的，可以有0-n个参数，且参数类型也任意
6.参数名按驼峰命名法命名，多个参数用逗号‘，’隔开
7.return当返回值类型部位void时，必须return返回，且必须是对应的类型，*但即使是void也可以选择性的return* 
-------------------------------------------------------------**
### 运用
#### 1.无参无返回
`static void SayHello(){

		Console.WriteLine("hello,world");
		
`}`
`static void Main(string[]args){

	SayHello();//*=>hello,world*

`}`
#### 2.有参无返回(参数一定是一个能得到类型的变量)
`static void SayYourName(string yourName){

		Console.WriteLine($"hello,{yourName}");

}`
`static void Main(string[]args){

		string Name = "牛爷爷";
		SayYourName(Name);//*=>hello,牛爷爷*

`}`
#### 3.无参有返回(返回对应类型的值,一般会用到返回值，拿个东西接住它)
`static string WhatYourName(){

		string MyName = Console.ReadLine();
		return MyName;

`}`
`static void Main(string[]args){

	string YourName = WhatYourName();
	//*=>返回你的名字//(函数获得了你的名字)*
	//Console.WriteLine(WhatYourName());
	Console.WriteLine(YourName);//*=>你的名字*

`}`
#### 4.有参有返回
`static int Sum(int a,int b){

		int sum = a + b
		return sum; 
		//return a + b;
		//return可以跟表达式，return会先看return后面的内容

`}`
`static void Main(string[]args){

	int a = 1;
	int b = 2;
	int sum = Sum(a,b);
	Console.WriteLine(sum)//*=>3*

`}`
#### 5.有参有多返回(返回值类型？)
*对于现在阶段我们不能把两个类型都写在一起，故想到数组*
`static int[] Calc(int a,int b){

		int sum = a + b;
		int avg = sum / 2;
		int[]arr = {sum,avg};
		return arr;
		*//不可return{sum,avg},因为没有申明它是什么类型*
		//return new int[]{sum,avg};
`}`
`static void Main(string[]args){

	int[]arr = Calc(5,7);
	Console.WriteLine($"sum:{arr[0]},avg:{arr[1]}");

`}`
### return关键字
==*return可以不执行return后面的代码，直接返回到函数外部*==
*(无论有无返回值)*

### ref和out关键字
#### 1.学习缘由
*对于要改变传入参数并传到外面的，单纯是改不了的*
形式参数和传入参数的关系，
形式参数即申请了一个临时空间，其与外部传进来的参数没有关系，相当于copy赋值
`static void Change(int value){//这里相当于value = a

		value = 3;

`}`
`static void Change1(int[]arr){//这里相当于拷贝地址，指向同一个堆内存

		arr[0] = 99;

`}`
`static void ChangeArray(int[]arr){//相当于copy了外面arr的地址

		arr = new int[]{4,55,6,7,8,9};//参数地址新开辟，但是原来外面的地址不变

`}`
`static void Main(string[]args){

		int a = 4;
		int[]arr = {1,2,3,4,5,6};
		Change(a);
		Change1(arr);
		
		Console.WriteLine(a);//改不了，还是4;
		Console.WriteLine(arr[0]);//可以改
		ChangeArray(arr)
		Console.WriteLine(arr[0]);//还是99
`}`
这里如果我想要内部修改外部也修改值，内部new外部也变，
*即如果传入值参数在内部重新赋值，或传入引用参数在内部重新声明时，外部也发生同样的变化，可以用ref和out关键字*
#### 2.使用
**ref**
`static void ChangeValueRef(ref int value){

		value = 3;

}`
`static void ChangeArrayRef(ref int[]arr){

		arr[0] = 99;

`}`
`static void Main(string[]args){

		int a = 1;
		ChangeValueRef(ref a);//ref传入也要加ref的关键字
		int arr1 = {1,2,3,4};
		ChangeArrayRef(ref arr1);
		Console.WriteLine(a);//*=> 3
		Console.WriteLine(arr[0]);//**=> 99

`}`
**out**
`static void ChangeValueOut(out int value){

		value = 3;

`}`
`static void ChangeArrayOut(out int[]arr){

		arr[0] = 99;

`}`
`static void Main(string[]args){

		int a = 1;
		int[]arr1 = {1,2,3,4};
		ChangeValueOut(out a);
		ChangeArrayOut(out arr1);
		Console.WriteLine(a);*=>3
		Console.WriteLine(arr1[0]);*=>99

`}`
效果是一样的
#### 3.区别
 *ref传入的变量必须初始化，out不用*
 **out传入的变量必须在内部赋值，ref可改可不改**
				 **？？？**
out在外部不初始化，但是如果 内部不赋值，这个值就没用了
而ref其在外面已经初始化了，就算内部不赋值，其也是有值的
### 变长参数和参数默认值
#### 函数语法复习
#### 变长参数关键字
*如果参数有无数多个*
params 声明数组
**数组类型可以是任意类型**
*函数参数中最多只能有一个params关键字，且一定是在参数的最末尾*
	`static int Sum(params int[]arr){//即params声明这是一个变长参数//将所有传入参数放到一个数组里，这样就可以传无数个参数
			
		int sum = 0;
		for(int i = 0;i < arr.Length;i++){

			sum += arr[i];
		
		}
		return sum;
`}`
#### 参数默认值
有参数默认值的参数，成为可选参数
即当调用函数是不传入某个参数，那么就会使用默认参数值
*在写函数时，规定了某个参数默认等于某个值*
**1.支持多个默认参数值
2.如果要混用，可选参数一定要放到普通参数后面**
#### 函数重载
##### 基本概念
在同一语句块中（class或struct）函数或方法的名相同，但参数数量和类型不同
*1.命名一组功能相似的函数
2.提升函数可读性*
**WriteLine是我们用的最多的重载函数**
##### 实例
重载和返回值无关(即若返回值不一样，其他一样，不算重载)，只和函数的参数个数和参数类型有关
`static int CalcSum(int a,int b){

		return a + b;

`}`
`static int CalcSum(int a, int b,int c){

	return a + b + c;

`}`
`static void Main(string[]args){

		int b = CalcSum(1,2);
		int a = CalcSum(1,2,3);
		Console.WriteLine($"{a}{b}");
`}`
*ref和out*
`static void CalcSum(ref float f,int a){

		return f + a;

`}`
`static void CalcSum(out flost f,int a){(ref和out不能同时存在)

			f = 10.0f;
			return f + a;

`}`
**可选参数不能重载，但是变长参数可以**
#### 递归函数
##### 基本概念
函数自己调用自己
即函数体内调用自己
**1.必须有结束调用的条件**
**2.用于条件判断的条件必须改变，能够达到结束的目的**
##### 实例
`static void ToTen(int a){

		if(a <= 10){
		Console.WriteLine(a);
		a++;
		ToTen(a);
		}
`}`
## 结构体
### 基本概念
自定义变量类型，类似枚举，需要自己定义，是数据和函数的结合
*用来表示存在关系的数据集合*
### 语法
**1.写在namespace语句块中**
**2.关键字struct**
`struct 自定义结构体名{

		//变量
		//构造函数（可选）
		//函数

`}`
//*结构体名字是帕斯卡命名*
### 实例
`struct Student{

		//变量
		int age;
		bool sex;
		int number;
		string name;//表示学生的共同内容，不初始化
		
		//构造函数（可选）
		
		//函数//表现数据结构的行为
		void Speak(){
		
			Console.WriteLine($"我叫{name},{age},{sex},{number}");
		}
		

`}`
***1.结构体中声明的变量不能初始化
2.结构体中声明的变量可以是任意类型，包括结构体，但不能是本结构体
3.在结构体中的方法不加static关键字
4.结构体中的方法是可以用结构体中声明的变量的
5.结构体中可以有很多个方法****
### 使用
`static void Main(string[]args){

		Student stu1;
		stu1.//通过.来访问结构体内的内容
	
`}`
### 访问修饰符
修饰结构体中的变量和方法能否被外部使用
public,公共的，可以被外部使用
private，私有的，只能在内部使用
默认不写，为private
*只需要在声明变量和方法时，在其前面加上关键字*
`struct Stident{

		public int age;
		public int num;
		public bool sex;
		public string name;

		public void Speak(){
		
			Console.WriteLine($"{name},{age},,{sex},{num}");
		
		}

`}`
`static void Main(string[]args){

		Student stu;
		stu.age = 60;
		stu.name = "牛爷爷";
		stu.sex = false;
		stu.Speak();

`}`
### 构造函数（浅）
==*1.没有返回值==
==2.函数名必须和结构体名相同==
==3.必须有参数==
==4.如果声明了构造函数，那么就必须在其函数体中初始化变量*==
`struct Student{

		//变量
		public int age;
		public bool sex;
		publci int number;
		public string name;//表示学生的共同内容，不初始化
		
		//构造函数（可选）
//==新的关键字this，用以区分内部的变量和传入的变量==
	`	public Student(int  age,bool sex,int number,string name){

				this.age = age;
				this.sex = sex;
				this.number = number;
				this.name = name;
				

		}
		//函数//表现数据结构的行为
		public void Speak(){
		
			Console.WriteLine($"我叫{name},{age},{sex},{number}");
		}
		

`}`
**一般是为了在外面方便初始化，可以重载但是也需要保证其他变量的初始化**
`static void Main(string[]args){


		Student stu = new Student(18,false,123456，牛爷爷)；

`}`
## 排序初探
### 冒泡排序
#### 排序的基本原理
排序是为了将一组无序的序列，变为有序的，
包括升序和降序
在程序中，序列一般存在数组中，所以排序一般对数组
#### 冒泡排序的基本原理
8，7，1，5，4，2，6，3，9
*两两相邻
不停比较
不停交换
比较n轮*
#### 代码实现
`using System;
`namespace ConsoleApp117
`{

    class Program
    {

        static void Main(string[] args)
        {


            int[] arr = { 8, 7, 1, 5, 4, 2, 6, 3, 9 };
            for (int j = 0; j < arr.Length; j++)
            {
                ==for (int i = 0; i < arr.Length - 1 - j; i++)==
                {


                    if (arr[i] > arr[i + 1])
                    {
                        int tmp = arr[i];
                        arr[i] = arr[i + 1];
                        arr[i + 1] = tmp;


                    }


                }
                
				==if (!IsSort) {==

					    ==break;==
                    
					==`}==

            }
            for (int i = 0; i < arr.Length; i++)
            {


                Console.WriteLine(arr[i]);

            }



        }


    }
`}`
**优化**
==**1.即没必要和上一个最大的数比较了，也就是确定位置的数不参与比较
2.特殊情况的优化
也就是如果只有经过1轮，或几轮（小于n），即较多数其实不用参与排序，但按上述程序仍会继续
**==

### 选择排序
#### 选择排序基本原理
*排序的手段之一
*新建中间商(记录索引值)
依次比较
找出极值（最大最小）
放入目标位置
比较n轮*
#### 代码实现
`using System;
`namespace ConsoleApp {

    class Program { 
    
        static void Main(string[] args)
        {

            int[] arr = new int[20];
            Random numrand = new Random();
            for (int i = 0; i < arr.Length; i++)
            {
                arr[i] = numrand.Next(0, 101);
            
            
            }
            for (int i = 0; i < arr.Length; i++) {

                int index = 0;
                for (int j = 1; j < arr.Length - i; j++) {

                    if (arr[j] > arr[index]) {

                        index = j;
                    
                    }
                
                }
                if (index != arr.Length - 1 - i)
                {
                    int tmp = arr[index];
                    arr[index] = arr[arr.Length - 1 - i];
                    arr[arr.Length - 1 - i] = tmp;
                
                }
            
            
            }
            for (int i = 0; i < arr.Length; i++) {

                Console.WriteLine(arr[i]);
            
            }
        }
    
    
    
    }




`}
---------------------------------------------------------------------核心
## 面向对象的概念
对比==面向过程编程==：以过程为核心的编程思想
即分析解决问题的步骤，然后用函数把步骤一步一步实现，使用的时候一个一个调用
==面向对象编程==，*对现实世界理解和抽象的编程方法，万物皆对象，用程序来抽象（形容）对象*
**开启了女娲模式，想造什么对象就new什么对象**
## 面向对象-封装
### 类和对象
#### 什么是类
类是对象的模板，是一个语句块，类包含的东西是用来描述对象的相同特性，相同行为的，==关键字class==
#### 类声明在哪里
声明在namespace语句块里。不能在函数里声明。
#### 声明语法
`（可加访问修饰符，目前先不加）class 类名{

		//特征-成员变量
		//行为-成员方法
		//保护特征-成员属性
		//构造函数和析构函数
		//索引器
		//运算符重载
		//静态成员

`}`
==声明对象的模板==
#### 类声明实例
//形容人的类
**命名用帕斯卡命名，同一个语句块中的不同类不能同名**
`class Person{

//

`}`
`class Machine{

//

`}`
#### 什么是(类)对象
类的声明和类对象的声明不同
类似于枚举和结构体的声明，==类的声明相当于声明了一个自定义变量类型==，对象才是这个类创建出来的变量，这个过程称为实例化对象

*类对象是引用类型的*

#### 实例化对象的基本语法
**1.类名 变量名；*没有初始化==没有初始化是不能访问的==*
2.类名 变量名 = null（null代表空）;*没有初始化*
3.类名 变量名 = new 类名();**
#### 实例化对象
`class Person{
//
`}`
`Person p;
`Person p2 = null;
`Person p3 = new Person();`
`Person p4 = new Person();`
引用类型是放在堆上的，但在栈上也会存放空间，存放其在堆上的地址，没有初始化那么栈上分配的空间就是空的，即在堆上没有分配空间
null代表不分配对空间，和不写一样
p3和p4都是从Person类new的，但是p3，p4没有关系
*即同一个类创建的多个对象之间没有关系，数据不同*
### 成员变量和访问修饰符
#### 成员变量
*1.声明在类中
2.用来描述对象的特征
3.可以是任意变量类型
4.数量不定
5.是否赋值根据需求来定
*
`enum E_sex{

	Man,
	Woman

`}`
`class Position{

	//

`}`
`class Pet{
	//
}`
`
`class Person{

	//特征-成员变量即共有的特点
	public string name;
	public int age;
	public E_sex sex;
	==如果再类中声明一个和自己相同类型的成员变量时是不能对它实例化的，会造成死循环==
	public Person[]friends;//区别于结构体，结构体不能再其内声明自己同名的变量
	public Position pos;
	public Pet pet;

`}`
#### 访问修饰符
`public 公共的，自己（内部）和别人（外部）都能访问和使用
`private 私有的，只有自己（内部）才能使用
`protected 只有自己和自己的子类才能访问使用的` 
#### 成员变量的使用和初始值
`class Person{


    `public string name;
	public int age;
	public E_sex sex;
	
	public Person[]friends;
	public Position pos;
	public Pet pet;

`}`
`Person p = new Person();`
`p.name;//这样就是.出来用就行`
只要你new了一个Person，那么它里面的成员变量都是有初始值的
**值类型：
数字类型，默认是0;
bool类型，默认是false;
char类型，默认是空字符 **
**引用类型
默认都是null，即空**
==看默认值小技巧==
*`Console.WriteLine(default(变量类型));`*
### 成员方法
#### 成员方法声明
即成员函数来表述对象的行为的
*1.写在类语句块
2.描述对象行为
3.与函数声明规则相同
4.受到3P影响
5.返回数和方法数量不做限制*
**成员方法不加static关键字
成员方法必须通过实例对象来使用**
`class Person{

		public string name;
		public int age;
		public Person[]friends;
		
		public void Speak(string str){
		
			Console.WriteLine($"{name} 说了{str}");
			
		}
		public bool IsAdult(){
		
			if(age >= 18){
				return true;
			}
			return false;
		}
		public void AddFriend(Person p){
		
				if(friends.Length == 0){

						friends = new Person[]{p};

				}else{
					Person[]newFriends = new Person[friends.Length + 1];
					for(int i = 0;i < friends.Length;i++){
					
						newFriends[i] = friends[i];
					}
					newFriends[newFriends.Length - 1] = p;
					friends = newFriends;
				
				}
		
		}


`}`
#### 成员方法使用
`Person p = new Person();
`p.name = "牛爷爷";
`p.age = 60;`
`p.Speak("你好");`
### 构造函数和析构函数
#### 构造函数
实例化对象时，会调用的用于初始化的函数
如果不写，默认存在一个无参的构造函数
**可以声明无参的构造函数，对比结构体**
*1.没有返回值
2.函数值和类名必须相同
3.没有特殊需求时，一般为public*
*4.this代表当前调用该函数的对象自己，==用以区分同名变量==*
**5.可以写无数个**
如果不写无参函数写了有参函数，会默认失去掉这个无参函数
`class Person{

		int age;
		string name;
	public Person(string name,int age){
	
			this.name = name;
			this.age = age;
			//无参name = "牛爷爷"；
			//age = 60;
	
	}

`}`
`Perosn p = new Person("牛爷爷",60);`
#### 构造函数特殊写法
**可以通过this重用构造函数代码,即可以复用一些代码**
`访问修饰符 构造函数名(参数列表):this(参数1，参数2......)`
`public Person(int age,string name):this(name){
``				会先调用this()这个无参构造函数
		`this()可以有参数`,`它会先把string name传给this里的name,你往this里传什么参数，它就会对应先调用什么参数的构造函数,当然this里的参数不一定是前面的，也可以写死
`}`
#### 析构函数（了解）
==当引用类型的堆内存被回收时==，会调用析构函数，对于需要手动回收的语言（c++），需要在析构函数中做内存回收处理
*c#中有自动回收机制GC*
所以不怎么用，Unity中几乎不用
`~类名(){
		
`}`
**是当垃圾真正被回收时，自动调用，不是变成垃圾就调用**
#### 垃圾回收机制（重要）
垃圾回收，*简称GC*
垃圾回收的过程是遍历堆（Heap）上动态分配的所有对象
通过识别它们是否被引用来确定哪些对象是否是垃圾，哪些对象仍要被使用
垃圾就是没有被任何变量引用的变量，对象，需要被回收释放
**1.GC只负责堆内存的垃圾回收
2.引用类型都是存在堆中的，所以它的分配和释放都是通过垃圾回收机制来处理的，栈上的内存是通过系统分配的，有自己的生命周期，不需要对其管理**
原理：
*会把堆内存分成三代（代是垃圾回收机制使用的一种算法，分代算法）
0代内存：新分配的对象会被配置在0代内存中，每次分配都可能进行垃圾回收以释放内存（0代内存满时）
**在一次内存回收开始时，垃圾回收器会认为堆中全是垃圾，会进行以下两步
1.标记对象，从根（静态字段，方法参数）开始检查引用对象，标记后为可达对象，未标记是不可达对象，不可达就是垃圾
2.搬迁对象压缩堆，释放未标记对象，把0代内存中可达对象挪到1代对象，修改引用地址（堆里的内存可能不是连续的，需要把这些搬迁过来的放到连续的位置）**
1代内存：1代内存总有一天会满，会触发垃圾回收，此时0代1代一起释放，1代中的可达对象搬到2代
2代内存：大对象会被认为是2代内存，不会对大对象进行搬迁压缩，（85000字节83kb以上的）* ，其内部东西很多，所以0代1代速度比2代快，如果2代也满了，那么0代1代2代一起释放
==手动触发垃圾回收==（过程会卡顿）
`GC.Collect()
一般都是在Loading过场景的时候调用
### 成员属性
#### 成员属性的基本概念
*1.保护成员变量
2.为成员属性的获取和赋值添加逻辑处理
3.解决3P的局限性
public内外都能访问 private只能内部 protected内部和子类
属性可以让成员变量在外部只能获取不能修改，或者只能修改不能获取*
#### 成员属性的基本语法
`访问修饰符 属性类型 属性名{

		get{}
		set{}

`}
**命名以帕斯卡命名法**
例如：
`class Person{

		string name;
		int age;
		int money;
		

		public string Name{
			可以在返回之前添加逻辑规则
			//意味着这个Name可以获取的内容
			get{
				return name;
			}//需要返回一个属性类型的值，这里需要返回一个string
			set{
			//value用来表示外面传进来的值，只在set里做关键字,代表设置的内容
			name = value;
			
			}
		
		}

`}`
属性可以i进行加密处理
比如说value我传了一个5进去，但是我存的是10，即money = value + 5，即内存里的实际值实际不是我传进来的值
`public int Money{

		get{
		
			return money;
		}
		set{
		
			if(value < 0){
					value = 0;
					Console.WriteLine("钱不能小于0");
			}
			money = value;
		}

`}`
#### 成员属性的使用
`Person p = new Person();
`p.Name = "牛爷爷";//执行set语句块，赋给这个value`
`Console.WriteLine(p.Name);//这里执行get语句块，进行访问`
#### 成员属性中get和set前可以加访问修饰符(解决3P)
*1.默认不加，会使用属性声明时的访问权限
2.加的访问修饰符要低于属性的访问权限，也不能重复
public最高
*3.不能让get和set的访问权限都低于属性的访问权限*
`public int Money{

			private get{//意味着外面不能得到它了
					

			}
			private set{//意味着外面不能改了
			
			但是不能两个都是private
			因为这个属性本身有访问修饰符，如果两个都有，外面属性的访问就没用了
			}

`}`
#### get和set可以只有一个
只有一个时，其前面的访问修饰符没必要写
这种情况往往只有get因为我们希望其得，不希望其改，基本不会出现只有set的情况
`public int Age{

		get{

			return age;

		}

`}`
#### 自动属性
外部能得不能改的特征
如果类中有一个特征是只希望外部能得不能改得，又没有什么特殊处理（就是没有什么逻辑需求），那么就可以使用自动属性
`public bool sex{

		get;
		private set;

`}`
==就是一个自动的成员变量==，就是在3P的基础上，对其访问进行一些限制
### 索引器
#### 索引器基本概念
让对象可以像数组一样通过索引访问其中元素，使得程序看起来更直观，更容易编写
#### 索引器语法
`访问修饰符 返回值 this[参数类型 参数名，参数类型 参数名...]{

		get{}
		set{}

`}`
`class Person{

		string name;
		int age;
		private Person[] friends;//像数组一样访问其中需要有一个数组

		public Person this[int index]{
				//get，set用法和属性一样
				get{
					return friends[index];
				}
				set{
					friends[index] = value;
				}
				
		
		}

`}`

#### 索引器使用
`Person p = new Person();
`p[0] = new Person();`
#### 索引器中可以写逻辑
和属性中的逻辑一样，在get，set中写逻辑，对访问和赋值进行限制
#### 索引器可以重载
重载是函数名相同，但参数类型，顺序和数量不同
那么这里参数类型可以任意
`private Person[]friends;
`private int[,]array;
`public Person this[int index]{

		get{
			return friends[index];
		}
		set{
			friends[index] = value;
		}

`}`
`public int this[int i,int j]{

		get{
			return array[i,j];
		}
		set{
			array[i,j] = value;
		}

`}`
`Person p = new Person();
`p[0,0] = 10;`
但是你没有数组也行，可以搭配switch得到你想要的值,==只是可以实现`对象[]的语法糖`==
`public string this[string str]{

		get{
				switch(str){
					case "name":
						return this.name;
					case "age":
						return age.ToString();
				
				}
				return "";
		
		}

`}`
**结构体里也可以使用索引器**
### 静态成员
#### 静态成员基本概念
用static修饰的成员变量、方法、属性等称为静态成员
*直接用类名点出来使用*
#### 早已出现的静态成员
`Console.WriteLine()`其中Console就是一个静态类
#### 自定义静态成员
在类里封装的静态成员
`class Test{

		public static float PI = 3.14159265358979f;
		//static和public的顺序没有讲究
		public int a = 100;
		//就是多了一个static关键字
		public static CalCircle(float r){
		
			float area = PI * r * r;
		}
		public void  TestFuc(){
		
			Console.WriteLine("123");
		}

`}`
**使用**
`Console.WriteLine(Test.PI);//即不用实例化对象，直接类名.静态成员`
#### 为什么可以直接点出来使用
==记住程序中是不能无中生有的
我们所使用的对象，变量，函数都是需要在内存中分配空间的，之所以要实例化对象，目的就是分配内存空间，在程序中产生一个抽象的对象
静态成员的特点是程序运行时，就会为其分配内存空间，**所以我们能直接使用它**==
*静态成员和程序同生共死，直到程序结束后，它的内存空间才会被释放，故其有一个独立的小空间（静态存储区），具有唯一性（就是你在外面用的是这个房间里的内容，改也是改这里的内容），具有全局性*
#### 静态函数中不能使用非静态成员(生命周期造成)
成员变量只能将对象实例化出来才能点出来使用，不能无中生有，不能直接使用非静态成员，否则会报错
`class Test{

		public static float PI = 3.14159265358979f;
		//static和public的顺序没有讲究
		public int a = 100;
		//就是多了一个static关键字
		public static CalCircle(float r){
			//Console.WriteLine(a);这里不能这么搞，因为此时这个a（非静态成员）在内存中还没有
			Test.t = new Test();
			Console.WriteLine(t.a);
			float area = PI * r * r;
		}
		public void  TestFuc(){
		
			Console.WriteLine("123");
		}

`}`
#### 非静态函数可以使用静态成员(生命周期)
`class Test{

		public static float PI = 3.14159265358979f;
		//static和public的顺序没有讲究
		public int a = 100;
		//就是多了一个static关键字
		public static CalCircle(float r){
			//Console.WriteLine(a);这里不能这么搞，因为此时这个a（非静态成员）在内存中还没有
			Test.t = new Test();
			Console.WriteLine(t.a);
			float area = PI * r * r;
		}
		public void  TestFuc(){
		
			Console.WriteLine("123");
			Console.WriteLine(PI);
		}

`}`
#### 静态成员对于我们的使用
**静态变量**
*1.常用唯一变量的声明
2.方便别人获取的对象声明*
**静态方法**
*常用的唯一的方法声明*
#### 常量和静态变量
`const可以视为特殊的静态
`都可以通过类名点出使用`
==const必须初始化，不能修改，static没有这个规则
const只能修饰变量，static可以修饰很多
const必须写在访问修饰符后面，static没有要求 ==
### 静态类和静态函数
#### 静态类
`用static修饰的类`
*1.只能包含静态成员
2.不能被实例化*
==**作用**
1.将常用的静态成员写在静态类中，方便使用==
==2.静态类不能被实例化，体现静态成员的唯一性==
`Console就是一个静态类`
更适合做工具类
`static class TestStatic{

		static public int testIndex = 0;
		static public void TestFun(){
		
		}
		static public int TestIndex{
			get;
			set;
		}
`}`
#### 静态构造函数
`在构造函数前面加static修饰`
*1.静态类和普通类都可以有
2.不能使用访问修饰符
3.不能有参数
4.只会自动调用一次*
是为了初始化静态成员变量的
**在静态类中的静态构造函数**
`class StaticClass{

		public static int testInt = 100;
		public static int testInt2 = 200;
		static StaticClass(){
		
			Console.WriteLine("静态构造函数");//只会在第一次使用时调用
		}
		public StaticClass(){
			Console.WriteLine("普通构造函数");//每new一次执行一次
		}

`}`
### 拓展方法
#### 拓展方法基本概念 
为现有的非静态 变量类型添加新方法
*1.提升程序的拓展性
2.不需要在对象中重新写方法
3.不需要继承来添加方法
4.为别人封装的类型写额外方法*
**特点**
1.一定写在静态类中
2.一定是个静态函数
3.第一个参数为拓展目标
4.第一个参数用this修饰
#### 基本语法
`访问修饰符 static 返回值 函数名(this 拓展类名 参数名，参数类型 参数名，参数类型 参数名....)//this 拓展类名(现有的) 表示对哪个类进行拓展`
`static class Tools{
			`//为int拓展了一个成员方法
			`//成员方法是需要实例化之后才能使用的
			`//value代表使用该方法的实例化对象
		``		public static void SpeakValue(this int value){
		
				Console.WriteLine("int的拓展方法" + value);
		
		}

`}`
`int i = 10;`
`i.SpeakValue();//value代表的就是i`
`public static void SpeakString(this string value,string str){

		Console.WriteLine("string的拓展方法" + str);

`} `
#### 实例
`public static void SpeakString(this string value,string str){

		Console.WriteLine("string的拓展方法" + str);

`} `
#### 为自定义的类型拓展方法
刚刚的都是系统自带的类
`class Test{

			public void Fun1(){
			
				Console.WriteLine("111");
			}
			public void Fun2(){
			
				Console.WriteLine("222");
			}
`}`
`static class Tools{

			public static void Fun3(this Test value){
				Console.WriteLine("333");
			}

`}`
==如果拓展的方法和原有的方法名字一样，用的是原方法==
### 运算符重载
#### 运算符重载的基本概念
让自定义类和结构体能够使用运算符,即让类和结构体也能进行加减乘除
`使用关键字operator`
*1.一定是一个公共的静态的方法
2.返回值写在operator前
3.逻辑处理自定义*
**注意
1.条件运算符需要成对实现
2.一个符号可以多个重载
3.不能使用ref和out**
#### 基本语法（作为类的一个成员）
`public static 返回类型 operator 运算符(参数列表)//参数顺序重要，参数个数和其运算符的元数有关`
#### 实例
`class Point{

		public int x;
		public int y;
		public static Point operator +(Point p1,Point p2){//参数里至少有一个点是Point
			Point p = new Point();
			p.x = p1.x + p2.x;
			p.y = p1.y + p2.y;
			return p;
			
		}
`}`
#### 可重载和不可重载的运算符
==**可重载的**==
`算数运算符 - + * / ++（一参数） --（一参数）
`逻辑运算符 只有！
`位运算符 & | ^ >> <<
`条件运算符 > < >= <= == !=条件运算符需要成对实现
==**不可重载的**==
`逻辑与逻辑或&& ||
`索引符[]`
`强转（）`
`特殊运算符`
`比如点、三目运算符 =`
### 内部类和分部类
#### 内部类
在一个类中再声明一个类
使用时要用包裹者点出自己，用以表示亲密关系
访问修饰符作用很大
`class Person{

		public string name;
		public int age;
		public Body body;
		public class Body{
				Arm leftArm;
				Arm rightArm
				 public class Arm{
				 
				 }
		}
`}`
`Person p = new Person();`
`Person.Body body = new body();`
`Person.Body.Arm arm = new Arm();`
#### 分部类
把一个类分成几部分来声明
`关键字 partial`
分部描述一个类，增加程序的拓展性，可以写在多个脚本文件，
==分部类的访问修饰符要一致，不能有重复成员==
`public partial class Student{

		public bool sex;
		public string name;

`}`
`public partial class Student{//和上面还是代表同一个类，只是分开来写了

		public int number;
		public void Speak(){}

`}`
#### 分部方法
将方法的声明和实现分离
*1.不能加访问修饰符，默认私有
2.只能再分部类中声明
3.返回值只能是void
4.可以有参数但不用out关键字*
`public partial class Student{

		public bool sex;
		public string name;
		partial void Speak(string str);
`}`
`public partial class Student{//和上面还是代表同一个类，只是分开来写了

		public int number;
		partial void Speak(){
				Console.WriteLine("你好"); 
		
		}
		public void Speak(string str){}

`}`
## 面向对象-继承
### 继承的基本规则
#### 基本概念
一个类A继承一个类B，那么这个A会继承B中的所有成员，A拥有B中的所有特征和行为
被继承的类称为==父类、基类==
继承的类称为==子类、派生类==
子类可以有自己的特征和行为
*1.单根性 子类只能有一个父类（c#里只能继承一个类）
2.传递性 子类可以间接继承父类的父类*
#### 基本语法
`class 类名: 被继承的类名{

`}`
#### 实例
`class Teacher{

		public string name;
		public int number;
		public void SpeakName(){
			Console.WriteLine($"我叫{name}");
		}
`}`
`class TeachinigTeacher:Teacher{//那么这个也可以用Teacher的方法

		public string subject;
		public void SpeakSubject(){
		
			Console.WriteLine($"我教{subject}");
		}

`}`
`class ChineseTeacher:TeachingTeacher{

		public void Skill(){
				Console.WriteLine("竹杖芒鞋轻胜马，谁怕，一蓑烟雨任平生");
		}

`}`
#### 访问修饰符的影响
3P
`public
`private
`protected 只能在内部和子类访问`
即有一些信息你不想它在外部访问，但是还包含着子类，所以可以用protected
#### 子类和父类的同名成员
极不建议使用
可以
`public new string name;`把父类的name覆盖了
### 里氏替换原则
#### 基本概念
面向对象七大原则中最重要的原则
任何父类出现的地方，子类都可以替代
==父类容器可以装载子类对象，因为子类对象包含了父类的所有内容==
方便对象的存储和管理
#### 基本实现
`class GameObject{


`}`
`class Player:GameObject{

		public void PlayerAtk(){
		
			Console.WriteLine("玩家攻击");
		}

`}`
`class Monster:GameObject{

		public void MonsterAtk(){
		
			Console.WriteLine("怪物攻击");
		}

`}`
`class Boss:GameObject{

		public void BossAtk(){
		Console.WriteLine("Boss攻击");
		
		}
`}`
`GameObject player = new Player();//new的是Player()，这里就是一个里氏替换法则`
`GameObject[]objects = new GameObject[]{new Player(),new Monster(),new Boss()};`
#### is和as
如果要通过父类容器使用子类中的方法时
`is用来判断一个对象是否是指定类对象，返回一个bool(因为你只是用父类容器装子类对象)`
`if(player is Player){

		

`}
`as将一个对象转换为指定类对象,如果成功转换，返回指定类型的类对象，失败，返回空`
`Player p = player as Player;`
### 继承中的构造函数
#### 基本概念
当声明一个子类对象时，==先执行父类的构造函数，再执行子类的构造函数==
*1.父类的无参构造很重要
2.子类可以通过base关键字代表父类，调用父类构造*
#### 执行顺序
`父类的父类的构造——>...——>父类构造——>......——>子类构造`
`class GameObject{

		public GameObject(){
			Console.WriteLine("GameObject的构造函数");
		} 

`}`
`class Player:GameObject{

		public Player(){
			Console.WriteLine("Player的构造函数");
		}
`}`
`class MainPlayer:GameObject{

		public MainPlayer(){
			Console.WriteLine("MainPlayer的构造函数");
		}
`}`
*先执行根部的构造函数，然后一次执行*
#### 父类的无参构造函数很重要
`class Father{

		public Father(int i){//无参构造被顶掉了
			Console.WriteLine("Father的构造函数");
		}

`}`
`class Son:Father{//故子类报错，它默认调用父类的无参构造

		public Son()
`}`
#### 通过base调用指定父类构造
即不想默认调用父类无参构造,和this语法相似
`class Father{

		
		public Father(int i){
				Console.WriteLine("Father 的有参狗营造函数");
		}
`}`
`class Son:Father{

		public Son(int i):base(i){
		
		
		}
		public Son(int i,string str):this(i){
				//间接调用，通过上一个构造函数
		}
}`
### 万物之父和装箱拆箱
#### 万物之父
`object关键字`==是所有类型的基类==，是一个类，是引用类型
*1.可以用里氏替换法则，用object容器装所有对象
2.可以用来表示不确定的类型，==作为函数参数类型==*
`static void Test(params object[])`//里面可以传任意类型的参数
#### 万物之父的使用
`class Father{

		
		public Father(int i){
				Console.WriteLine("Father 的有参狗营造函数");
		}
`}`
`class Son:Father{

		public Son(int i):base(i){
		
		
		}
		public Son(int i,string str):this(i){
				//间接调用，通过上一个构造函数
		}
`}`
`Father f = new Son();`
`if(f is Son){

		Son s = f as Son;
		
`}`
*引用类型*
`object o = new Son();*
`o = f;*//可以等于任意类
*值类型*
`object o = 10;`
`//使用需强转`
`int i = (int)o;`
*特殊的string类型*
`object o = "你好";`
`string str = o.ToString();`
`string str1 = o as string;`
`object arr = new int[10];//object也可以是数组`
`arr1 = arr as int[];`
`arr1 = (int[])arr;`
#### 装箱拆箱
用object用值类型时，称为装箱
将object转为值类型，称为拆箱
*装箱*
==就是把值类型用引用类型来存储，栈内存会迁移到堆内存中==
*拆箱*
==就是把引用类型存储的值类型取出来，堆内存会迁移到栈内存==
存在内存迁移，增加性能消耗
### 密封类（断子绝孙）
#### 基本概念
`使用sealed密封关键字修饰的类`
让类无法再被继承
#### 实例
`sealed class Father{


`}`
`class Son:Father{//报错，Father无法被继承

}`
#### 作用
==不允许最底层子类被继承==
## 面向对象-多态
### 多态Vob
#### 多态的概念
多种状态，让继承同一父类的子类，在执行相同方法时有不同表现
让同一个对象有唯一的行为特征
#### 解决的问题
`class Father{

		public void SpeakName(){
			
			Console.WriteLine("Father的方法");
		}

`}`
`class Son:Father{

			//之前会写相同名字的方法，new覆盖掉
		public new void SpeakName(){
		
				Console.WriteLine("Son的方法");
		}
`}`
`Father f = new Son();`
`f.SpeakName();//这里执行Father的方法`
`(f as Son).SpeakName();//这里执行Son的方法`
这里f明明是一个Son的对象，但是执行方法时还是Father的方法，故多态的目的就是让对象具有唯一的行为和特征
#### 多态的实现
函数的重载是编译时的多态，参数不同，调用对应的函数
但我们接下来学的是运行时的多态
`Vob 代表三个关键字
`v:virtual(虚函数)==可以被子类重写==
`o:override(重写)
`b:base(父类)`
`class GameObject{


		string name;
		public GameObject(string name){
		
				this.name = name;
		}
		//虚函数的目的是用来给子类重写的
		public virtual void Atk(){
				Console.WriteLine("游戏对象进行攻击");
		}

`}`
`class Player:GameObject{

		public Player(string name):base(name){
		
			
		}
		//重写
		public override void Atk(){
			//代表父类，可以通过base来保留父类的行为
			//如果要重写的话,意味着逻辑都要改，也就是说如果保留那么之后，调用父类方法，然后再加逻辑，既执行父类的，也执行子类的， 不保留，就覆盖掉父类的，只执行子类的
			base.Atk();
			Console.WriteLine("玩家攻击");
		}
		

`}`
### 抽象类和抽象方法
#### 抽象类
`被抽象关键字abstract修饰`
*1.不能被实例化
2.可以包含抽象方法
3.继承抽象类必须重写其抽象方法*
`abstract class Thing{

		//只是一类物品的统称，不能new
		//抽象类中封装的所有知识点都可以书写
		//可以写抽象函数
		
`}`
`class Water:Thing{

		
`}`
==但是可以用里氏替换法则==
#### 抽象函数
纯虚方法
*1.只能在抽象类中声明
2.没有方法体
3.不能是私有的
4.继承后必须实现override重写*
`abstract class Friut{

			public string name;
			public abstract void Bad()//父类中不需要实现，只是声明，不能有函数体和{}
			
					
`}`
`class Apple:Fruit{

			public override void Bad(){
					Console.WriteLine("水果坏了");
			}

`}`
虚方法可以选择是否写函数体，且子类中可以选择实现重写
但抽象方法必须不能有函数体，且子类必须实现重写，
*若子类已经实现了，子类的子类可以不写*
### 密封方法（了解）
#### 概念
`sealed 密封类，断子绝孙`
`使用sealed修饰的重写函数，让虚方法或抽象方法之后不能再被重写`
#### 实例
`abstract class Animal{

		public string name;
		public abstract void Eat();
		public virtual void Speak(){
		//
		}
`}`
`class Person:Animal{

		public sealed void Eat(){
			//		
		}
		public sealed override void Speak(){
		
			//
		}
`}`
`class WhitePerson:Person{

		public override void Eat(){//这里会报错
		
		}
		public override void Speak(){//报错  
		
		}
`}`
### 接口（实现多态的第三种方法）
#### 概念
==行为的抽象规范==
是一种自定义类型
`关键字interface`
*1.只包含方法，（自动属性那样写）属性，索引器，事件
2.成员不能被实现
3.成员可以 不用写访问修饰符，不能是私有的
4.不包含成员变量
5.类继承接口后，必须实现接口中所有成员，且必须是public*
**类可以继承多个接口
类继承接口之后，要实现接口中所有成员**
==和类的声明类似，接口是用来继承的，接口不能被实例化，但可以作为容器存储对象，**遵循里氏替换法则**==
#### 声明
`interface 接口名{

			//接口语句块
`}`
接口是抽象行为的基类
==**接口命名，帕斯卡前面加个I**==
`interface IFly{

			//不能写函数体
			void Fly()；//这里不写访问修饰符默认是public
			string Name{

					get;
					set;//不能有语句块
			
			}
			int this[int index]{
			
					get;
					set;
			}
			event Action doSomething; // 事件，后续...
`}`
#### 使用
接口是用来继承的,一般来说接口成员前面一般不加protected，加了要显示实现
`class Animal{

		
`}`
`class Person:Animal,IFly{//通过逗号的方式，可以同时继承一个类和一个接口，或多个接口


		//实现的接口函数可以在子类中重写
		public virtual void Fly(){
		
			Console.WriteLine("中国人能飞~，中国人能飞~");
		}
		public string Name{
				get;
				set;
		}
		public int this[int index]{

				get{
				
						return 0;
				
				}set{
					
					
				}
		
		
		}
		public event Action doSomething;
`}`
`IFly f = new Person();//将接口看作父类容器，装子类对象`
用来装具有相同行为但不同类型的东西
#### 接口可以继承接口
不需要实现，待类继承接口时，才进行实现所有接口的所有成员
`interface IWalk{

		void Walk();
`}`
`interface IMove:IWalk,IFly{

		void Move();
`}`
#### 显示实现接口
*1.接口中成员用来protected
2.当一个类继承两个接口，但两个接口中含有同名方法时*
==显示实现接口时不能写访问修饰符==
类自己也可以有同名方法，但就和接口没关系了 
`interface IAtk{

			void Atk(){
			
			}
`}`
`interface ISuperatk{

			void Atk(){
			
			}
`}`
`class Player:IAtk,ISuperatk{

				//接口名.行为名()
			void IAtk.Atk(){
			
			}
			void ISuperatk.Atk(){
			
			}
`}`
## 面向对象关联知识点
### 命名空间
#### 命名空间基本概念
是用来组织和重用代码的
是一个工具包，类是一个个工具
#### 使用
**帕斯卡命名**
`namespace 命名空间名{

		一个个类

`}`
==命名空间可以分开来写，也可以写在不同文件==
`namespace MyGame{

		class GameObject{
		
		
		}
		//同一命名空间中不能有同名类
`}`
`namespace MyGame{

		class Player:GameObject{
		
		
		}
`}`
#### 不同命名空间中相互使用 需要引用命名空间或指明出处 
==使用using 命名空间
或MyGame点出，指明出处==
`namespace MyGame{

		class GameObject{
		
		
		}
		//同一命名空间中不能有同名类
`}`
`namespace MyGame{

		class Player:GameObject{
		
		
		}
`}`
`using MyGame;`
`namespace ConsoleApp{

			GameObject a = new GameObject();
			//MyGame.GameObject a = new GameObject();
`}`
#### 不同命名空间中允许有同名类
*同一命名空间不能有同名类*
==但不同命名空间允许有同名类==
`namespace MyGame{

		class GameObject{
		
		
		}
`}`
`namespace MyGame2{

		class GameObject{
		
		}
`}`
`MyGame.GameObject;
`MyGame2.GameObject//指明出处，有所区分`
#### 命名空间可以包含命名空间
==工具包里的小包，即子空间==
`namespace MyGame{

		namespace UI{
				class Image{
				
				}
		}
		namespace Game{
		
				class Image{
				
				}
		}
`}`
`MyGame.UI.Image uImage = new MyGame.UI.Image();`
`MyGame.Game.Image gIamge = new MyGame.UI.Iamge();`
#### 关于修饰类的访问修饰符
==命名空间中的类默认是public==，只允许用public
`internal 用的比较少，即只能在这个程序集里用`
### 万物之父中的方法
#### object中的静态方法
1.**`Equals判断两个对象是否相等，最终的决断权交给左侧对象的Equals方法，不管值类型引用类型都会按照左侧对象**Equals方法的规则来进行比较**

`Console.WriteLine(object.Equals(1,1));`
`class Test
`{


`}
`class Program {

    static void Main(string[] args) {

        Console.WriteLine(object.Equals(1, 1));//true
        Test t1 = new Test();
        Test t2 = new Test();
        Console.WriteLine(object.Equals(t1, t2));//false
        
    }
`}
2.**`ReferenceEquals判断两个对象是否是相同的引用，主要来判断引用类型的对象,值类型对象始终返回false`**

`Console.WriteLine(object.ReferenceEquals(1,1));//false`
#### object中的成员方法
1.**`GetType在反射相关知识点很重要，主要作用是返回对象运行时的Type类型`**

`Type type = t1.GetType();`

2.**`MemberwiseClone用于获取对象浅拷贝对象，口语化就是返回一个新的对象，但引用变量和老对象相同，值类型改后老的不变`**

`class Test{

		public int i = 1;
		public Test t2 = new Test();

		public Test Clone(){
		
				return MemberwiseClone() as Test;
		}
`}`
`class Test2{

		
`}`
`Test t1 =  new Test();
`Test t2 = t1.Clone();`
#### object中的虚方法
1.**`虚方法Equals，静态Equals中提到的左侧(实际是把右边的对象传到了左边的虚方法Equals)，默认实现还是比较两者是否为同一个引用，微软重写了该方法，可以比较值
`我们也可以重写`**
2.**`GetHashCode是获取对象的哈希码的，是通过算法算出的一个对象特有的编码（可能会相同），我们可以重写，基本不用`**
3.**`ToString返回当前对象代表的字符串，可以重写它，非常常用，在Console.WriteLine()中会自动调用对象的ToString方法`**
`class Test{


		public override string ToString(){
				return "你好";
		}
`}`
`Test t = new Test();`
`Console.WriteLine(t);//你好`
### String（密封类）
#### 字符串指定位置获取
**字符串本质其实是char数组**
`string str = "牛爷爷";`
`str[0];//联想到索引器`
`转成char数组`
`char[]chars = str.ToCharArray();`
#### 字符串拼接
`str = string.Format("{0}{1}",1,3333)//13333`
#### 正向查找字符位置
`str = "你是牛爷爷";`
`int idx = str.IndexOf("你") // 返回索引值，没找到返回-1`
#### 反向查找指定字符串位置
`str = "你是牛爷爷牛爷爷";`
`刚刚只找到第一个出现的`
`int idx = str.LastIndexOf("牛爷爷");//找这个词第一个，没找到返回-1`
#### 移除指定位置后的字符
`str = "你是牛爷爷牛爷爷";`
`str = str.Remove(4);//String 很多方法不改变原字符串，会返回一个新字符串，这里包括4`
`str = str.Remove(1,1);//两个参数，参数1：开始位置，参数2：移几个字符`
#### 替换指定字符串
`str = "你是牛爷爷牛爷爷";`
`str.Replace("牛爷爷","李爷爷");//第一个参数old char/string，第二个参数new char/string`
#### 大小写转换
`str = "hello";`
`str = str.ToUpper();`
`str = str.ToLower();`
#### 字符串截取
`str = "你好，你是牛爷爷";`
`string str1 = str.SubString(2);//把第二个字符包括之后截取`
`string str2 = str.SubString(1,3);//参数1代表开始位置，参数2代表指定个数，超出字符串长度运行报错`
#### 字符串切割
`str = "1,2,3,4,5,6,7,8,9";`
`string[]str1 = str.Split(',');//参数是以什么分割，得到字符串数组`
### Stringbuilder
*如果一个字符串 经常改变会非常浪费空间*
**是c#提供的一个用于处理字符串的公共类**
修改字符串而不创建新的对象，可以提升性能
使用前需要引用命名空间
`using System.Text;`
`StringBuilder str = new StringBuilder("123123",100);//必须new一个`
**存在容量的问题，每次往里添加东西会自动扩容，就是其容量其实要比传入字符串更大，每次往里放不是开新房间，而是往里放，第二个参数是你要求的最大的容量，超过容量就GC**
`获得容量`
`str.Capacity`
`获得字符长度`
`str.Length`
**增删查改替换**
**增**
`str.Append("444")//在字符串后再加4个字符`
`str.AppendFormat("{0}{1}",100,999)`
**插入**
`str.Insert(0,"你好");//第一个参数是位置，第二个是要插入的`
**删**
`str.Remove(0,3);//第一个开始位置，第二个长度`
**清空**
`str.Clear();`
**查**
`Console.WriteLine(str[0]);`
**改**
`str[0] = "33";//string中[]是只读的，但这里不是`
**替换**
`str.Replace("1","hi");//第一个是old第二个是new的`
**重新赋值**
`先清空，再往里加东西`
**判断是否和某一个字符串相等**
`if(str.Equals("123")){

		Console.WriteLine("相等")；
`}`
### 结构体和类的区别
==存储空间上的区别==
*结构体存在栈空间上，类在堆空间*
*结构体具有封装的特性，但不具备继承和多态的特性。不能用protected修饰*
==细节区别==
*1.结构体是值类型，类是引用类型*
*2.结构体不能用protected*
*3.结构体声明成员变量时，不能初始化，类可以*
*4.结构体不能显示声明无参构造函数*
*5.结构体声明有参构造函数，无参的不会被顶*
*6.结构体不能声明析构函数*
*7.结构体需要在构造函数中初始化所有成员变量，类随哟*
*8.不存在静态结构体，即结构体不能被static修饰，但其中可以有静态成员*
*9.结构体内不能声明和自己一样的结构体变量，类可以*
==结构体的特别之处==
结构体可以继承接口
==如何选择结构体和类==
**1.想要用继承和多态时，淘汰结构体**
**2.对象是数据集合时，优先考虑结构体，比如位置，坐标**
**3.从值类型和引用类型赋值上考虑**
### 抽象类和接口的区别
#### 相同点
*1.都可以被继承*
*2.都不能被实例化
3.都可以包含方法声明
4.子类必须实现未实现的方法
5.都遵循里氏替换法则*
#### 区别
*1.抽象类中可以有构造函数，接口不能
2.抽象类只能单一继承，接口可以被继承多个
3.抽象类中可以有成员变量，接口不能
4.抽象类中可以声明成员方法，虚方法，抽象方法，静态方法，接口中只能声明没有实现的抽象方法
5.抽象类中可以用访问修饰符，接口建议不用*
#### 如何选择
==表示对象的用抽象类，表示行为的用接口==
## 多个脚本文件(程序结构更清晰)
### 了解脚本文件格式和路径
`slnx就是解决方案的主路口`
`.cs即脚本文件`
`bin里有Debug，其内文件只有在执行一次之后才会生成
`其中有.exe可执行文件,如果想让别人执行拷贝整个文件夹`
### 新建脚本文件
*1.第一种就是在文件夹里新建一个文本文件.txt然后改后缀*
*2.file里add，可以添加类或其他，add类的时候一定要改名字，namespace名字一定要和工程名一样*
*==我们遵循一个类一个脚本==*
新建脚本的命名空间可以改，但是需要using
接口，类，结构体一个声明对应一个脚本
### 在文件夹中新建脚本文件
在工程右键新建文件夹，把同类的文件放到文件夹
`如果在这个新建的文件夹里新建文件，其命名空间后面会有.Game`
## Uml类图
UML同一建模语言
对面向对象系统的产品进行说明和可视化
`使用图形把业务逻辑完成，生成代码`
学习类图，以理清对象关系，养成面向对象编程习惯
`VISIO`
`更多形状，选择软件，选择UML类，把图形拖出来`
`上面是类名，下面是成员，包来表示命名空间`
==`关系说明`==
`关联:比如类A会有一个类B成员作为它的成员变量`
`聚合：比如地图类聚合围墙类，鸟群聚合大雁类有点包含的感觉
`依赖关系：
`复合：很多不同的东西单个单个组成的整体`
指向谁就是怎么样它
## 七大原则(高内聚，低耦合，提升可重用性，减少类内部对其他类的调用)
### 单一职责原则
类被修改的几率很大，因此应该专注单一的功能，各司其职
### 开阀原则
对拓展开放，对修改关闭
不允许修改模块的源代码
继承就是一个最典型的开闭原则
### 里氏替换原则
任何父类出现的地方子类都可以被替代
父类容器装载子类对象
### 依赖倒转原则
依赖于抽象，不要依赖于具体实现
即抽象出某一类东西都具有的行为，然后搞成接口
### 接口隔离原则
一个接口不应该提供太多的行为，应该让别人去选择需要实现什么样的行为
一个接口一个方法
### 合成复用原则
尽量使用对象组合，而不是继承来达到复用的目的，
要在遵循迪米特原则的前提下进行
### 迪米特原则
最少知识原则，一个对象应该对其他对象尽可能少的了解
一个对象中的成员，要尽可能少的直接和其他类建立关系
----------------------------------------------------------------------------进阶
