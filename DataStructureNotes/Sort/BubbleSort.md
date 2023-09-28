# 冒泡算法笔记

### 构建main函数
```java
public static void main(String[] args) {
		// creat new array
		int[] array = {2, 1, 7, 3, 5, 8, 4, 3, 0, 3, 2, 4, 1};
		
		// bubble sort
		int[] newarray = bubbleSortMyAnswer(array);
		//int[] newarray = bubbleSort(array);
		System.out.println("Bubble sort result: "+ Arrays.toString(newarray));
	}
```
### 标准答案
```java
public static int[] bubbleSort(int[] array) {
		if (array.length == 0)
			return array;
		for (int i = 0; i < array.length; i++)
			for (int j = 0; j < array.length - 1 - i; j++)
				if (array[j + 1] < array[j]) {
					int temp = array[j + 1];
			        array[j + 1] = array[j];
			        array[j] = temp;
				}
		 return array;
	}
```
### 我的答案
```java
public static int[] bubbleSortMyAnswer(int[] array) {
		// never forget to test empty array
		if (array.length==0) {
			return array;
		} else {
			for (int i=0; i<array.length-1; i++) {
				for (int j=1; j<array.length-i; j++) {
					if (array[i] > array[i+j]) {
						int temp = array[i];
						array[i] = array[i+j];
						array[i+j] = temp;
					}
				}
			}
		}
		return array;
	}
```
### gpt算法分析

**为什么我的代码可以排序？**
	  
但是你的实现与传统的冒泡排序有所不同。通常的冒泡排序是比较相邻的元素。但在你的实现中，你从 i 开始，跟 i+j 进行比较，这确实会得到正确的排序结果，但不是最典型的冒泡排序实现。

我们来仔细分析你的代码：
- 当 i 为0时，j 从1开始，所以 i+j 从1开始；这将保证数组的第一个元素（array[0]）成为整个数组中的最小值。
- 当 i 为1时，j 从1开始，所以 i+j 从2开始；这将保证数组的第二个元素（array[1]）成为数组中剩余的元素中的最小值。

以此类推...因此，你的算法确实会对数组进行正确的排序。

你的排序方法其实是一种变种的选择排序。
传统的选择排序工作原理如下：
- 在第 i 轮中，遍历数组的 i 到最后的部分，找到最小的元素，然后与 array[i] 交换位置。
- 这样，经过每一轮，数组的前 i 个元素就是已排序的，且 array[i] 是 i 到最后部分的最小元素。

你的代码与选择排序的主要思想相似，即确保前 i 个元素是已排序的。但你的实现中，你并没有直接寻找最小值，而是通过比较和交换逐渐将最小值移动到前面。

所以，你的排序方法其实是选择排序的一个变种。

**让我们来分析一下时间复杂度：**

在实际的交换操作数上，你的方法可能在某些情况下比传统的冒泡排序要少，但又比传统的选择排序要多。

**我这个方法和传统方法比有什么优势么？**

你的排序方法是一个选择排序和冒泡排序的结合。在某种程度上，它的表现会介于这两者之间。让我们来探讨它的优势和可能的劣势：

* 优势:
    1. 较少的交换操作: 与冒泡排序相比，你的方法可能会减少交换操作的次数。在冒泡排序中，每次发现逆序的相邻元素都会进行交换，而在你的方法中，每个元素只会被交换到其最终位置一次（就像选择排序）。
    2. 简洁的逻辑: 对于一些开发者来说，你的代码逻辑可能更为直观和简洁。它保持了固定的双重循环结构，不需要像选择排序那样额外地寻找最小（或最大）元素。
* 劣势:
    1. 不是最优的选择排序: 传统的选择排序对于确定每轮的“选择”只需要一次交换，而你的方法可能需要多次，这意味着在某些情况下，它可能比传统的选择排序更加低效
	2. 非标准化: 由于这不是一个标准的排序算法，其他开发者可能不太熟悉这种方法，可能需要额外的时间来理解代码的工作原理。
    
总结：你的方法有其优点，特别是可能的较少交换操作和简洁的逻辑。然而，它可能不如经典的选择排序或冒泡排序在某些场景下高效。如果效率是关键考虑因素，建议使用更高效的排序算法，如归并排序、快速排序或堆排序。如果是教学或学习目的，这是一个有趣的实现，可以用来讨论不同排序策略的优劣。