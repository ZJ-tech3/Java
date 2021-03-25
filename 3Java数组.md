# 数组

## 3.1数组的概述

* 多个相同类型的数据按照一定的顺序排列，并使用一个名字命名，通过编号进行管理。
* **数组：**引用数据类型；**数组元素：**既可以是基本数据类型也可以是引用数据类型。
* 连续空间，长度确定不能修改。

## 3.2一维数组的使用：

* 声明和初始化：

  ```java
  int[] ids;//声明
  //静态初始化:初始化和赋值同时进行
  ids=new int[]{1,2,3,4};
  //动态初始化
  String[] names = new String[5];
  ```

* 调用指定位置的元素：数组名[下标]

* 获取数组的长度length; ```ids.length;```

* 遍历数组：循环

* **数组元素的默认初始化值**：整型（byte、short、long、int）：0；浮点型（double、float）0.0；char型：0不是'0'；boolean  false；**引用数据类型null空值**

* 数组的内存解析：new出来的都在堆里，首地址值在栈中。

## 3.3多维数组的使用

把数组作为一个数组的元素。

* 声明和初始化：

  ```java
  int[][] ids;//声明
  //静态初始化:初始化和赋值同时进行
  ids=new int[][]{{1,2,3,4},{4,5},{5,8,9}};
  //动态初始化
  String[][] names = new String[5][2];
  String[][] names = new String[5][];//该情况不能直接访问某个元素，需要先赋值
  //中括号可以分开放
  //声明和赋值在同一行时可以省略new(类型推断)
  ```

* 调用指定位置的元素：数组名\[下标\]\[下标\]

* 获取数组的长度length; ```ids.length;```

* 遍历数组：循环

* **数组元素的默认初始化值**：arr[0]地址值；arr地址值；arr\[0\]\[0\]元素默认值

* 数组的内存解析：new出来的都在堆里，首地址值在栈中。

引用类型变量要么是null要么是地址值。

## 3.4数组中涉及的常见算法

### 1.数组元素的赋值

杨辉三角、回形数

### 2.数值形式问题

最大、最小、平均数、总和

### 3.数组的复制、反转、查找（线性查找、二分查找）

赋值与 复制不同。

反转：首尾交换

查找：二分法需要有序

```java
		//二分法在有序数组中查找
		int[] arr = new int[]{1,3,5,9,12,15,20,30,55}; 
		int dest = 12;
		int head = 0;//初始的首索引
		int end = arr.length -  1;//初始的末索引
		
		while(head <= end)
		{
			int middle = (head+end)/2;
			if(dest==arr[middle])
			{
				System.out.println("找到元素的位置："+middle);
				break;
			}
			else if(arr[middle] > dest)
			{
				end = middle - 1;
			}
			else if(arr[middle] < dest)
			{
				head = middle + 1;
			}
		}
```

### 4.排序算法

**交换排序：**冒泡排序、快速排序（重要，需要会写）

堆排序、归并排序（知道思想）

算法的5大特征：输入、输出、有穷性、确定性、可行性。

* 冒泡排序  **O(n^2)和最坏**    最好为O(n)

```java
int[] arr = new int[]{49,38,65,97,76,13,27,49};
		//冒泡排序
		for(int i=0;i<arr.length-1;i++)
		{
			for(int j=0;j<arr.length-1-i;j++)
			{
				if(arr[j]>arr[j+1])
				{
					int temp = arr[j];
					arr[j] = arr[j+1];
					arr[j+1] = temp;
				}
			}
		}
```

* **快速排序  O（nlog(n)）**  最坏为O(n^2)

与堆排序、归并排序平均和最坏时间复杂度一样

## 3.5Arrays工具类的使用

java.util.Arrays

| 序号 | 方法和说明                                                   |
| ---- | ------------------------------------------------------------ |
| 1    | **public static boolean equals(long[] a, long[] a2)** 如果两个指定的 long 型数组彼此*相等*，则返回 true。如果两个数组包含相同数量的元素，并且两个数组中的所有相应元素对都是相等的，则认为这两个数组是相等的。 |
| 2    | **public static **String toString(int[] a)**输出数组信息。   |
| 3    | **public static void fill(int[] a, int val)** 将指定的 int 值分配给指定 int 型数组指定范围中的每个元素。同样的方法适用于所有的其他基本数据类型（Byte，short，Int等）。 |
| 4    | **public static void sort(Object[] a)** 对指定对象数组根据其元素的自然顺序进行升序排列。同样的方法适用于所有的其他基本数据类型（Byte，short，Int等）。 |
| 5    | **public static int binarySearch(Object[] a, Object key)** 用二分查找算法在给定数组中搜索给定值的对象(Byte,Int,double等)。数组在调用前必须排序好的。如果查找值包含在数组中，则返回搜索键的索引；否则返回 负数。 |

## 3.6数组使用中的常见异常

### 1.数组角标越界



### 2.空指针异常